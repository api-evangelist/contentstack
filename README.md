# Contentstack (contentstack)
Contentstack is a headless CMS platform that enables organizations to manage and deliver content across digital channels through a suite of REST and GraphQL APIs. Their developer platform provides APIs for content delivery, content management, personalization, automation, analytics, AI-powered content generation, and front-end deployment, supporting modern composable digital experience architectures.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/contentstack/refs/heads/main/apis.yml)

## Scope

- **Type:** Contract
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags:

 - Headless CMS, Content Management, Content Delivery, GraphQL, Personalization, Automation, AI, Analytics

## Timestamps

- **Created:** 2026-03-21
- **Modified:** 2026-03-21

## APIs

### Contentstack Content Delivery API
The Contentstack Content Delivery API (CDA) allows developers to retrieve published content from their Contentstack stacks and deliver it to web or mobile applications. It supports fetching entries, assets, and content types through REST endpoints using stack API keys and delivery tokens for authentication. The API is read-only and optimized for high-performance content retrieval at scale. It supports filtering, sorting, pagination, and localization, making it suitable for building localized, multi-channel digital experiences.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/content-delivery-api](https://www.contentstack.com/docs/developers/apis/content-delivery-api)


#### Tags:

 - Content Delivery, Headless CMS, Content Management, REST

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/content-delivery-api)
- [OpenAPI](openapi/contentstack-content-delivery-api-openapi.yml)

### Contentstack Content Management API
The Contentstack Content Management API (CMA) provides programmatic access to manage all aspects of a Contentstack stack, including content types, entries, assets, environments, workflows, and users. It supports full CRUD operations using standard HTTP verbs (GET, POST, PUT, DELETE) and authenticates via management tokens or user session tokens. Developers use this API to automate content operations, build editorial tooling, migrate content between environments, and integrate Contentstack with third-party systems. It is available at version v3 under the api.contentstack.io base URL for the North America region.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/content-management-api](https://www.contentstack.com/docs/developers/apis/content-management-api)


#### Tags:

 - Content Management, Headless CMS, REST, CRUD

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/content-management-api)
- [OpenAPI](openapi/contentstack-content-management-api-openapi.yml)

### Contentstack GraphQL Content Delivery API
The Contentstack GraphQL Content Delivery API enables developers to query content from their Contentstack stack using GraphQL syntax, allowing precise retrieval of only the fields and relationships needed in a single request. It is built on top of the Content Delivery API and supports querying entries, assets, and nested references across content types. The GraphQL API does not support mutations or subscriptions; it is strictly read-only and intended for front-end and application data fetching. A built-in GraphiQL Explorer is available for browsing the schema and constructing queries interactively.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/graphql-content-delivery-api](https://www.contentstack.com/docs/developers/apis/graphql-content-delivery-api)


#### Tags:

 - GraphQL, Content Delivery, Headless CMS, Query Language

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/graphql-content-delivery-api)

### Contentstack Image Delivery API
The Contentstack Image Delivery API allows developers to retrieve and transform images stored as assets in their Contentstack stacks. It supports on-the-fly image manipulation operations including resizing, cropping, format conversion, quality adjustment, and overlay compositing via URL query parameters. Images are served from a CDN for fast delivery, and transformations are applied at request time without creating additional stored copies. This API is commonly used to optimize images for responsive web design and multi-device delivery scenarios.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/image-delivery-api](https://www.contentstack.com/docs/developers/apis/image-delivery-api)


#### Tags:

 - Images, Media, Asset Delivery, Transformation

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/image-delivery-api)

### Contentstack Personalize Management API
The Contentstack Personalize Management API provides programmatic control over the resources in a Contentstack Personalize project, including Attributes, Audiences, Events, and Experiences. Developers can use this API to create and manage audience segments based on user attributes and behavioral events, and to configure personalized content experiences for those segments. It is a REST API that follows standard CRUD conventions and is intended for use in headless personalization workflows where content targeting logic needs to be managed programmatically or integrated with external data platforms.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/personalize-management-api](https://www.contentstack.com/docs/developers/apis/personalize-management-api)


#### Tags:

 - Personalization, Audiences, Experiences, Content Management

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/personalize-management-api)
- [OpenAPI](openapi/contentstack-personalize-management-api-openapi.yml)

### Contentstack Personalize Edge API
The Contentstack Personalize Edge API enables real-time, dynamic personalization interactions using edge computing to retrieve personalized content experiences. It allows applications to retrieve personalization manifests of active experiences, set and update user attributes for audience matching, merge user identity records, and track behavioral events. The Edge API does not require authentication since it operates on public-facing digital properties, using project and user identifier headers for context instead of traditional API keys.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/personalize-edge-api](https://www.contentstack.com/docs/developers/apis/personalize-edge-api)


#### Tags:

 - Personalization, Edge Computing, User Attributes, Events

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/personalize-edge-api)
- [OpenAPI](openapi/contentstack-personalize-edge-api-openapi.yml)

### Contentstack Automate Management API
The Contentstack Automate Management API allows developers to programmatically manage automation projects and workflows within a Contentstack organization. It supports creating, updating, retrieving, and deleting automations that connect Contentstack content events to third-party services and internal processes. This API is part of the Contentstack Automate (formerly Automation Hub) product, which provides a no-code/low-code automation layer built on top of the CMS. It is useful for organizations that need to provision or manage automations at scale across multiple stacks or environments.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/automation-hub-management-api](https://www.contentstack.com/docs/developers/apis/automation-hub-management-api)


#### Tags:

 - Automation, Workflows, Integration, Content Management

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/automation-hub-management-api)
- [OpenAPI](openapi/contentstack-automate-management-api-openapi.yml)

### Contentstack Analytics API
The Contentstack Analytics API provides access to usage and performance metrics for CMS, Launch, and Automate products within a Contentstack organization. Developers can retrieve analytics data programmatically to build custom dashboards, monitor content delivery performance, and track platform usage against plan limits. The API is intended for organizational administrators and integration builders who need to incorporate Contentstack operational data into broader observability or reporting workflows. It returns structured data suitable for aggregation with external analytics and business intelligence tools.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/analytics-api](https://www.contentstack.com/docs/developers/apis/analytics-api)


#### Tags:

 - Analytics, Metrics, Reporting, Monitoring

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/analytics-api)
- [OpenAPI](openapi/contentstack-analytics-api-openapi.yml)

### Contentstack SCIM API
The Contentstack SCIM API implements the System for Cross-domain Identity Management (SCIM 2.0) standard to enable automated user lifecycle management within a Contentstack organization. It allows Identity Providers (IdPs) to provision and deprovision users, manage group memberships, and synchronize user attributes between the IdP and Contentstack. This API is primarily used by enterprise organizations that manage Contentstack access through centralized identity management platforms such as Okta, Azure AD, or OneLogin. Group mappings in Contentstack allow IdP-managed groups to control role-based access within the CMS.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/scim-api](https://www.contentstack.com/docs/developers/apis/scim-api)


#### Tags:

 - SCIM, User Provisioning, Identity Management, Security

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/scim-api)
- [OpenAPI](openapi/contentstack-scim-api-openapi.yml)

### Contentstack Brand Kit Management API
The Contentstack Brand Kit Management API provides programmatic control over Brand Kit resources within a Contentstack organization. Brand Kits serve as centralized hubs for an organization's brand identity, encompassing detailed brand information, writing guidelines, and persona configurations. The API supports full CRUD operations for Brand Kits, Voice Profiles, and custom LLM configuration, enabling developers to manage brand identity data programmatically and integrate it with AI content generation workflows.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/brand-kit-management-api](https://www.contentstack.com/docs/developers/apis/brand-kit-management-api)


#### Tags:

 - Brand Management, AI, Voice Profiles, Content Generation

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/brand-kit-management-api)
- [OpenAPI](openapi/contentstack-brand-kit-management-api-openapi.yml)

### Contentstack Knowledge Vault API
The Contentstack Knowledge Vault API provides endpoints for ingesting, updating, and deleting content items stored in a Brand Kit's Knowledge Vault. The Knowledge Vault is a vector database that stores brand-specific knowledge content which is retrieved during AI content generation to provide accurate, brand-aligned responses. Content ingested via this API is vectorized and made available to the Generative AI API for retrieval augmented generation (RAG) workflows.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/knowledge-vault-api](https://www.contentstack.com/docs/developers/apis/knowledge-vault-api)


#### Tags:

 - Knowledge Management, AI, Vector Database, RAG

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/knowledge-vault-api)
- [OpenAPI](openapi/contentstack-knowledge-vault-api-openapi.yml)

### Contentstack Generative AI API
The Contentstack Generative AI API provides an endpoint for generating AI-powered content using a Brand Kit's knowledge vault and voice profiles. It acts as a communication channel between the vector database and large language models, processing prompts with retrieval augmented generation (RAG) to produce brand-aligned content. The API supports optional knowledge vault retrieval and voice profile application to ensure generated content adheres to the organization's brand guidelines and writing style.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/generative-ai-api](https://www.contentstack.com/docs/developers/apis/generative-ai-api)


#### Tags:

 - Generative AI, AI, Content Generation, Brand Kit

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/generative-ai-api)
- [OpenAPI](openapi/contentstack-generative-ai-api-openapi.yml)

### Contentstack Launch API
The Contentstack Launch API allows developers to programmatically manage web application deployments within Contentstack Launch. It supports full lifecycle management of Launch projects, environments, and deployments, including creating deployments from uploaded build artifacts, monitoring deployment logs, revalidating CDN caches, and retrieving signed upload URLs for build file transfers. The API is designed for CI/CD integration and enables automated deployment workflows for front-end applications connected to Contentstack stacks.

**Human URL:** [https://www.contentstack.com/docs/developers/apis/launch-api](https://www.contentstack.com/docs/developers/apis/launch-api)


#### Tags:

 - Deployment, CI/CD, Frontend, Hosting

#### Properties

- [Documentation](https://www.contentstack.com/docs/developers/apis/launch-api)
- [OpenAPI](openapi/contentstack-launch-api-openapi.yml)

## Common Properties

- [Portal](https://www.contentstack.com/developers)
- [Documentation](https://www.contentstack.com/docs)
- [Website](https://www.contentstack.com/)
- [PrivacyPolicy](https://www.contentstack.com/privacy)
- [TermsOfService](https://www.contentstack.com/legal/terms-of-service)
- [Support](https://www.contentstack.com/support)
- [Blog](https://www.contentstack.com/blog)
- [Login](https://app.contentstack.com/)
- [AsyncAPI](asyncapi/contentstack-webhooks-asyncapi.yml)
- [JSONSchema](json-schema/contentstack-entry-schema.json)
- [JSONSchema](json-schema/contentstack-stack-schema.json)
- [JSONSchema](json-schema/contentstack-webhook-payload-schema.json)
- [JSON-LD](json-ld/contentstack-context.jsonld)
- [Vocabulary](vocabulary/contentstack-vocabulary.yml)
- [SpectralRules](rules/contentstack-rules.yml)
- [Capability](capabilities/deliver-headless-content.yml)
- [Capability](capabilities/manage-stack-content.yml)
- [Capability](capabilities/personalize-experiences.yml)
- [Capability](capabilities/automate-content-workflows.yml)
- [Capability](capabilities/generate-brand-aligned-ai-content.yml)
- [Capability](capabilities/deploy-launch-frontends.yml)
- [Capability](capabilities/provision-users-via-scim.yml)

## Maintainers

**FN:** API Evangelist

**Email:** info@apievangelist.com
