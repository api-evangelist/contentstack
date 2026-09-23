---
name: contentstack-sync-a-content-cache
description: Keep a local copy of a Contentstack stack in step using the Synchronization API's pagination and sync tokens instead of re-fetching everything.
api: Contentstack Content Delivery API
provider: Contentstack
providerId: contentstack
generated: 2026-09-17
method: generated
source: openapi/contentstack-synchronization-api-openapi.yml, openapi/contentstack-entries-api-openapi.yml, openapi/contentstack-assets-api-openapi.yml; https://www.contentstack.com/docs/developers/apis/content-delivery-api
operations:
  - syncContent
  - getAllEntries
  - getAllAssets
---

# Sync a content cache

Full re-fetch is the wrong shape here. Contentstack publishes a delta endpoint, and the monthly API-call quota — 100K on Free, 1M on Growth — makes the difference material.

Base: `https://cdn.contentstack.io/v3` (regional: `eu-cdn.contentstack.com`, `au-cdn.contentstack.com`). Auth is the stack `api_key` header plus the environment `access_token`.

## Steps

1. **Initial sync.** `syncContent` — `GET /stacks/sync` with `init=true`. Optionally narrow with `content_type_uid`, `type`, `start_from` or `locale`.
2. **Page through it.** The response carries a `pagination_token` while more pages remain. Call `syncContent` again with `pagination_token` until it stops appearing.
3. **Keep the sync token.** The final page returns a `sync_token`. Persist it.
4. **Delta sync.** Call `syncContent` with `sync_token` to receive only what changed — publishes, unpublishes and deletes — since that token, and store the new token it returns.
5. **Backfill on demand.** For anything the delta does not carry, `getAllEntries` and `getAllAssets` return at most 100 records; page with `skip` and `limit` and use `include_count` to size the loop.

## Staying inside the limits

Reads are **10 requests per second per organization**, shared org-wide. Watch `X-RateLimit-Remaining`; there is no `Retry-After`, so back off exponentially with jitter on a 429. Monthly call quotas are a separate ceiling set by the pricing tier — see `plans/contentstack-plans-pricing.yml`.

## Notes

- The delivery surface is read-only, so nothing in this flow needs an idempotency guarantee and nothing here needs undoing.
- Webhooks (`asyncapi/contentstack-webhooks-asyncapi.yml`) are the push counterpart; use them to trigger a delta sync rather than polling.
