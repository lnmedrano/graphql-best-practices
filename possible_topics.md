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

## 3- Main Elements

### 3.1- Queries

- **Queries must be used only to fetch resources, not to modify nor delete them.**
- Queries names should be in camelCase. They could be singular or plural depending on the amount of resources being fetched. In addition, _get_ and _fetch_ verbs shouldn't be used. For example:
  - `user` to get one user.
  - `users` to get more than one user.
  - `usersFromTags` on some hypothetical case of getting users that match with some tags.

- Arguments must be a set of key-value pairs comma separated (in the resolver the arguments are received in an object and destructuring is possible and convenient). A max of 4 arguments is recommended. For example:

  ```graphql
  query {
    user(firstName: 'John', lastname: 'Doe'){}`
  }
  ```

- The queries should be as nested as possible. The fields that are being asked must not be comma separated.

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

- Variables, directives and fragments are allowed.

  ```graphql
  query {
      user($firstName: 'John', lastname: 'Doe') {
        friends(firstName: $firstName) {
          firstName
          lastName
          email
        }
      }
    }
  ```

  Note: In the example above, we are getting all John Doe's friends that have his same name.

  ```graphql
  query {
      user($firstName: 'John', $lastname: 'Doe', $showFriends: true) {
        friends @include(if: $showFriends) {
          firstName
          lastName
          email
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
