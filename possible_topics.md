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
  - [3.7- Schemas](#schemas)
- [4- Nullability](#nullability)
- [5- Pagination](#pagination)
- [6- Caching and Batching](#cachingAndBatching)
- [7- Authentication and Authorization](#auth)
- [8- Error handling](#errorHandling)
- [9- API versioning](#versioning)
- [10- Apollo Server](#apolloServer)
- [11- Useful Links](#links)
- [12- Bibliography](#bibliography)

## 1- Objective <a name="objective"></a>

The purpose of this document is to present the conventions and standards used at Wolox for GraphQL. It is supposed to cover the main aspects of GraphQL from the Wolox's approach to it.

## 2- Serving over HTTP <a name="http"></a>

## 3- Main Elements <a name="mainElements"></a>

### 3.1- Queries <a name="queries"></a>

- **Queries must be used only to fetch resources, not to modify nor delete them.**
- Queries names should be in camelCase. They could be singular or plural depending on the amount of resources being fetched. In addition, _get_ and _fetch_ verbs shouldn't be used. For example:
  - `user` to get one user.
  - `users` to get more than one user.
  - `usersFromTags` on some hypothetical case of getting users that match with some tags.

- Arguments must be a set of key-value pairs comma separated (in the resolver the arguments are received in an objetc and destructuring is possible and convenient). A max of 4 arguments is recommended. For example:

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

- Variables, directives and  are allowed.

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

### 3.2- Mutations <a name="mutations"></a>

### 3.3- Types <a name="types"></a>

### 3.4- Resolvers <a name="resolvers"></a>

### 3.5- Field-resolvers <a name="fieldResolvers"></a>

### 3.6- Subscriptions <a name="subscriptions"></a>

### 3.7- Schemas <a name="schemas"></a>

## 4- Nullability <a name="nullability"></a>

## 5- Pagination <a name="pagination"></a>

## 6- Caching and Batching <a name="cachingAndBatching"></a>

## 7- Authentication and Authorization <a name="auth"></a>

## 8- Error Handling <a name="errorHandling"></a>

## 9- API Versioning <a name="versioning"></a>

## 10- Apollo Server <a name="apolloServer"></a>

## 11- Useful Links <a name="links"></a>

- [GraphQL Specification](https://spec.graphql.org/)
- [Apollo Server Documentation](https://www.apollographql.com/docs/apollo-server/)
- [GraphQL Resolvers: Best Practices](https://medium.com/paypal-engineering/graphql-resolvers-best-practices-cd36fdbcef55) by Mark Stuart
- [Apollo Blog](https://blog.apollographql.com/)
- [GraphQL official site](https://graphql.org)

## 12- Bibliography <a name="bibliography"></a>

Bilbiography used by the authors of this documents can be found at [bibliography](./bibliography.md)
