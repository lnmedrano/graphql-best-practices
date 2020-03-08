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

## Serving over http <a name="http"></a>

## Main elements <a name="mainElements"></a>

### Queries <a name="queries"></a>

### Mutations <a name="mutations"></a>

Name your mutations verb first. Then the object, or “noun,” if applicable. e.g: `createUser`.

Mutations should have only one input argument, named `input`, and should have non-null, unique, input object type.

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
