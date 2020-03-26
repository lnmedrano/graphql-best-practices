# GraphQL Best Practices

## Index

- [GraphQL Best Practices](#graphql-best-practices)
  - [Index](#index)
  - [1- Objective](#1--objective)
  - [2- Serving over HTTP](#2--serving-over-http)
  - [3- Main Elements](#3--main-elements)
    - [3.1- Queries](#31--queries)
    - [3.2- Mutations](#32--mutations)
    - [3.3- Types](#33--types)
    - [3.4- Resolvers](#34--resolvers)
    - [3.5- Field-resolvers](#35--field-resolvers)
    - [3.6- Subscriptions](#36--subscriptions)
    - [3.7- Schemas](#37--schemas)
  - [4- Nullability](#4--nullability)
  - [5- Pagination](#5--pagination)
  - [6- Caching and Batching](#6--caching-and-batching)
  - [7- Authentication and Authorization](#7--authentication-and-authorization)
  - [8- Error Handling](#8--error-handling)
  - [9- API Versioning](#9--api-versioning)
  - [10- Apollo Server](#10--apollo-server)
  - [11- Useful Links](#11--useful-links)
  - [12- Bibliography](#12--bibliography)

## 1- Objective

The purpose of this document is to present the conventions and standards used at Wolox for GraphQL. It is supposed to cover the main aspects of GraphQL from the Wolox's approach to it.

## 2- Serving over HTTP

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

Although uncommon, GET requests can be used too. The GraphQL query should be specified in the `query` query parameter and variables can be sent as a JSON-encoded string in an additional query parameter called `variables`. If the query contains several named operations, an `operationName` query parameter can be used to control which one should be executed.

The response should be returned in the body of the request in JSON format. As mentioned in the [spec](https://spec.graphql.org/June2018), a query might result in some data and some errors, and those should be returned in a JSON object of the form:

```json
{
  "data": { ... },
  "errors": [ ... ]
}
```

If there were no errors returned, the `errors` field should not be present on the response. If no data is returned the `data` field should only be included if the error occurred during execution.

## 3- Main Elements

### 3.1- Queries

 **Queries must be used only to fetch resources, not to modify nor delete them.**

 Queries names should be in camelCase. They could be singular or plural depending on the amount of resources being fetched. In addition, _get_ and _fetch_ verbs shouldn't be used. For example:

- `user` to get one user.
- `users` to get more than one user.
- `usersFromTags` on some hypothetical case of getting users that match with some tags.

Arguments must be a set of key-value pairs comma separated (in the resolver the arguments are received in an object and destructuring is possible and convenient). A max of 4 arguments is recommended.

Variables, directives and fragments are allowed.

The queries should be as nested as possible. The fields that are being asked must not be comma separated.

  ```graphql
  query {
    user(firstName: 'John', lastName: 'Doe'){
      firstName
      lastName
      email
      contactUser {
        firstName
        lastName
        email
      }
      books {
        title
        calification
        author {
          firstName
          lastName
          birthDate
        }
      }
    }
  }
  ```

### 3.2- Mutations

Mutations should be named using camelCase. The verb should go first, then the object or "noun". e.g: `createUser`.

Mutations should have only one input argument, named `input`, and should have non-null, unique, input object type. Then you should try to nest the input object, this gives you room to easily deprecate sections of the API or add new ones.

### 3.3- Types

### 3.4- Resolvers

### 3.5- Field-resolvers

### 3.6- Subscriptions

### 3.7- Schemas

## 4- Nullability

## 5- Pagination

## 6- Caching and Batching

## 7- Authentication and Authorization

## 8- Error Handling

## 9- API Versioning

## 10- Apollo Server

## 11- Useful Links

- [GraphQL Specification](https://spec.graphql.org/)
- [Apollo Server Documentation](https://www.apollographql.com/docs/apollo-server/)
- [GraphQL Resolvers: Best Practices](https://medium.com/paypal-engineering/graphql-resolvers-best-practices-cd36fdbcef55) by Mark Stuart
- [Apollo Blog](https://blog.apollographql.com/)
- [GraphQL official site](https://graphql.org)

## 12- Bibliography

Bilbiography used by the authors of this documents can be found at [bibliography](./bibliography.md)
