# GraphQL Best Practices

## Index

- [1- Objective](#objective)
- [2- Serving over http](#http)
- [3- Main elements](#mainElements)
  - [3.1- Queries](#queries)
  - [3.2- Mutations](#mutations)
  - [3.3- Types](#types)
  - [3.4- Resolvers](#resolvers)
  - [3.5- Field-resolvers](#fieldResolvers)
  - [3.6- Subscriptions](#subscriptions)
- [4- Nullability](#nullability)
- [5- Pagination](#pagination)
- [6- Caching and Batching](#cachingAndBatching)
- [7- Authentication and Authorization](#auth)
- [8- Error handling](#errorHandling)
- [9- API versioning](#versioning)
- [10- Apollo Server](#apolloServer)

## Objective <a name="objective"></a>

The purpose of this document is to present the conventions and standards used at Wolox for GraphQL. It is supposed to cover the main aspects of GraphQL from the Wolox's approach to it.

## Serving over HTTP <a name="http"></a>

Most modern web frameworks use a pipeline model where requests are passed through a stack of middleware. GraphQL should be placed after all authentication middleware, so that you have access to the same session and user information you would in your HTTP endpoint handlers.

A standard GraphQL POST request should use the `application/json` content type, and include a JSON-encoded body of the following form:

```json
{
  "query": "...",
  "operationName": "...",
  "variables": { "myVariable": "someValue", ... }
}
```

`operationName` and `variables` are optional fields. `operationName` is only required if multiple operations are present in the query.

The response should be returned in the body of the request in JSON format. As mentioned in the [spec](https://spec.graphql.org/June2018), a query might result in some data and some errors, and those should be returned in a JSON object of the form:

```json
{
  "data": { ... },
  "errors": [ ... ]
}
```

If there were no errors returned, the `errors` field should not be present on the response. If no data is returned the `data` field should only be included if the error occurred during execution.

## Main elements <a name="mainElements"></a>

### Queries <a name="queries"></a>

### Mutations <a name="mutations"></a>

### Schemas <a name="schemas"></a>

### Types <a name="types"></a>

### Resolvers <a name="resolvers"></a>

### Field-resolvers <a name="fieldResolvers"></a>

### Subscriptions <a name="subscriptions"></a>

## Nullability <a name="nullability"></a>

## Pagination <a name="pagination"></a>

## Caching and Batching <a name="cachingAndBatching"></a>

## Authentication and Authorization <a name="auth"></a>

## Error handling <a name="errorHanling"></a>

## API versioning <a name="versioning"></a>

## Apollo Server <a name="apolloServer"></a>
