# BaseHub GraphQL API

## Description

BaseHub is a GraphQL-first headless CMS and content platform where every repository exposes a fully type-safe GraphQL API. Because BaseHub schemas are dynamically generated from each repository's content model, the shape of the `Query` type varies per workspace. However, all repositories share a set of built-in system types (block primitives, rich text, media, mutations, filtering) that are constant across every BaseHub deployment.

Authentication is via the `x-basehub-token` HTTP header. Tokens are scoped per repository and available from the BaseHub dashboard.

## Endpoint

```
https://api.basehub.com/graphql
```

## Authentication

Pass the repository token as an HTTP header:

```
x-basehub-token: <your-token>
```

Optionally target a specific branch:

```
x-basehub-branch: <branch-name-or-id>
```

## Documentation

- API Reference: https://docs.basehub.com/api-reference
- GraphQL Query Guidelines: https://docs.basehub.com/api-reference/graphql-api/query-api-guidelines
- GraphQL Mutation Guidelines: https://docs.basehub.com/api-reference/graphql-api/mutation-api-guidelines
- Interactive Explorer (GraphiQL): https://docs.basehub.com/api-reference/graphql-api/explorer
- TypeScript SDK: https://www.npmjs.com/package/basehub
- GitHub Organization: https://github.com/basehub-ai

## Schema Notes

The SDL in `basehub-schema.graphql` captures the **stable built-in types** that are present in every BaseHub repository. The root `Query` object is represented with the fields from the official playground/blog-template repository (`basehub-ai/basehub`), which serves as the canonical example schema shipped alongside the SDK.

User-defined content models extend the `Query` type with additional document and list blocks generated from the repository's content structure. Each repository's full schema can be introspected via the GraphQL endpoint once authenticated.

## Schema Source

Derived from:
- `basehub-ai/basehub` repository: `playground/src/lib/basehub/basehub-types.d.ts`
- BaseHub SDK source: `packages/basehub/src/`
- Official documentation: https://docs.basehub.com/api-reference/graphql-api/query-api-guidelines
