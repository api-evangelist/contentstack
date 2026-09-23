---
name: contentstack-provision-users-with-scim
description: Provision, update and deprovision Contentstack organization users over the SCIM 2.0 endpoint, using the standard an identity provider already speaks.
api: Contentstack SCIM API
provider: Contentstack
providerId: contentstack
generated: 2026-09-17
method: generated
source: openapi/contentstack-scim-users-api-openapi.yml, openapi/contentstack-scim-groups-api-openapi.yml, openapi/contentstack-scim-schema-discovery-api-openapi.yml; https://www.contentstack.com/docs/developers/apis/scim-api
operations:
  - listScimUsers
  - createScimUser
  - getScimUser
  - replaceScimUser
  - updateScimUser
---

# Provision users with SCIM 2.0

Contentstack implements **SCIM 2.0 (RFC 7643 / 7644)** rather than a bespoke user API. If your identity provider already speaks SCIM — Okta, Entra ID, OneLogin — this needs no custom connector.

Base: `https://auth-api.contentstack.com` (regional variants exist — `eu-auth-api`, `au-auth-api`, `azure-na-auth-api`, `azure-eu-auth-api`, `gcp-na-auth-api`, `gcp-eu-auth-api`). All paths hang off `/scim/v2.0/organizations/{organization_uid}`.

## Steps

1. **Discover the schema.** The schema-discovery surface returns the supported SCIM schemas, so a client can confirm which attributes this tenant accepts before it writes anything.
2. **List users.** `listScimUsers` — `GET /scim/v2.0/organizations/{organization_uid}/Users`. Responses are wrapped in `urn:ietf:params:scim:api:messages:2.0:ListResponse`.
3. **Create a user.** `createScimUser` — `POST .../Users` with a `urn:ietf:params:scim:schemas:core:2.0:User` body.
4. **Read one.** `getScimUser` — `GET .../Users/{user_id}`.
5. **Replace or patch.** `replaceScimUser` (`PUT`) swaps the whole resource; `updateScimUser` (`PATCH`) takes a `urn:ietf:params:scim:api:messages:2.0:PatchOp` body and is the right call for a single attribute change such as deactivation.
6. **Groups** map to Contentstack roles through the SCIM Groups surface using `urn:ietf:params:scim:schemas:core:2.0:Group`.

## Auth and scopes

Bearer token. Organization administration scopes apply — see `scopes/contentstack-scopes.yml`. SAML SSO is configured separately; as of 2026-09-11 an organization can register up to five SAML 2.0 identity providers.

## Errors

SCIM errors come back as `urn:ietf:params:scim:api:messages:2.0:Error`, which is the SCIM envelope rather than the Contentstack JSON error body used elsewhere in the estate. Handle the two shapes separately.

## Undoing it

Deactivation through `updateScimUser` with a PatchOp on `active` is reversible. A hard delete is not — the same permanence rule that governs entries and assets applies.
