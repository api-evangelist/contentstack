---
name: contentstack-publish-an-entry
description: Create or update a Contentstack entry and publish it to an environment, with the retry and rollback rules the API actually supports.
api: Contentstack Content Management API
provider: Contentstack
providerId: contentstack
generated: 2026-09-17
method: generated
source: openapi/contentstack-entries-api-openapi.yml and openapi/contentstack-content-types-api-openapi.yml; conventions and limits from https://www.contentstack.com/docs/developers/apis/content-management-api
operations:
  - getAllContentTypes
  - getSingleContentType
  - createEntry
  - updateEntry
  - getSingleEntry
  - publishEntry
  - unpublishEntry
---

# Publish an entry

## Before you call anything

- Pick the stack with the `api_key` header and authenticate with `authorization: Bearer <management_token>` (server-to-server) or an OAuth access token carrying `cm.entry:write` and `cm.entry:publish`.
- The `branch` header selects the branch; it defaults to `main`.
- There is **no idempotency mechanism**. Contentstack documents no `Idempotency-Key` header anywhere. If `createEntry` times out, do **not** blind-retry — call `getAllEntries` first and check whether the entry landed, or you will create a duplicate.

## Steps

1. **Find the content type.** `getAllContentTypes` (`GET /content_types`) returns at most 100 records; page with `skip` and `limit`. Use `getSingleContentType` to read the field schema you must satisfy.
2. **Create the entry.** `createEntry` — `POST /content_types/{content_type_uid}/entries`. The body is wrapped: `{ "entry": { ... } }`. Pass `locale` for a localized entry.
3. **Or update an existing one.** `updateEntry` — `PUT /content_types/{content_type_uid}/entries/{entry_uid}`. Read the current state with `getSingleEntry` first; an update creates a new version rather than overwriting history.
4. **Publish.** `publishEntry` — `POST /content_types/{content_type_uid}/entries/{entry_uid}/publish`. The body names the target `environments[]` and `locales[]`. Requires `cm.entry:publish`.
5. **Verify.** Read the entry back from the delivery surface (`https://cdn.contentstack.io/v3`) with the stack `api_key` plus the environment `access_token`.

## Rate limits

Writes are capped at **10 requests per second per organization** — shared across every team on that org. Bulk publishing runs on a separate, tighter **1 request per second** budget and caps at 10 items per bulk call. Exhaustion returns **429**. Contentstack returns `X-RateLimit-Limit` and `X-RateLimit-Remaining` but **no `Retry-After` and no reset timestamp**, so choose your own exponential backoff with jitter.

## Errors

`401` invalid credentials · `412` invalid stack API key · `422` semantic/validation error or unknown field · `429` rate limited. See `errors/contentstack-problem-types.yml`. The error body is Contentstack-shaped JSON, not RFC 9457 `problem+json`.

## Undoing it

- Publishing is reversible: `unpublishEntry` — `POST /content_types/{content_type_uid}/entries/{entry_uid}/unpublish`. No window is stated.
- Updating is recoverable through version history, but there is **no restore operation** — you read the old version and write it again.
- **Deleting is not reversible.** Contentstack states plainly: "Once you delete entry or asset metadata, it is permanently deleted and cannot be restored." There is no trash and no recovery window. Do not call `deleteEntry` on behalf of a user without explicit confirmation.
