# GraphQL Best Practices

## Index

- [1- Objective](#objective)
- [2- Serving over http](#http)
- [3- Main elements](#mainElements)
  - [3.1- Queries](#queries)
    - [3.1.1- Main aspects](#queriesMainAspects)
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
- [11- Useful Links](#links)

## 1- Objective <a name="objective"></a>

The purpose of this document is to present the conventions and standards used at Wolox for GraphQL. It is supposed to cover the main aspects of GraphQL from the Wolox's approach to it.

## 2- Serving over HTTP <a name="http"></a>

## 3- Main Elements <a name="mainElements"></a>

### 3.1- Queries <a name="queries"></a>

#### Main aspects <a name="queriesMainAspects"></a>

**Important** Queries must be used only to fetch resources, and not to modify them.

#### Naming conventions

Queries should be in camelCase. They could be singular or plural depending on the amount of resources being fetched. In addition, verb get shouldn't be used.

Examples:

- `user` to get one user.
- `users` to get more than one user.

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

## Error Handling <a name="errorHandling"></a>

## API Versioning <a name="versioning"></a>

## Apollo Server <a name="apolloServer"></a>

## Useful Links <a name="links"></a>

- [GraphQL Specification](https://spec.graphql.org/)
- [Apollo Server Documentation](https://www.apollographql.com/docs/apollo-server/)
- [GraphQL Resolvers: Best Practices](https://medium.com/paypal-engineering/graphql-resolvers-best-practices-cd36fdbcef55) by Mark Stuart
- [Apollo Blog](https://blog.apollographql.com/)
