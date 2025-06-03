# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

# Apollo Client

📘 Documentation officielle :  
https://www.apollographql.com/docs/react/get-started

---

## Installation Apollo-client

- https://www.apollographql.com/docs/react/get-started

```bash
npm install @apollo/client graphql
```

---

## Configuration de Apollo Client dans `App.js`

```js
// ...
import { ApolloProvider } from "@apollo/client";
import { ApolloClient, InMemoryCache } from "@apollo/client";
// ...

const client = new ApolloClient({
  uri: "http://localhost:4000",
  cache: new InMemoryCache(),
});
// ...
```

---

## Explication du code

| Élément  | Description                                                                    |
| -------- | ------------------------------------------------------------------------------ |
| `client` | Objet `ApolloClient` utilisé pour échanger des données avec le serveur GraphQL |
| `uri`    | Adresse du serveur GraphQL                                                     |
| `cache`  | Système de gestion de cache via `InMemoryCache` fourni par Apollo              |

---

## Envelopper l'application avec ApolloProvider

`<ApolloProvider client={client}>` pour rendre le client accessible à tous les composants React.

```
  return (
    <div className="App">
      <ApolloProvider client={client}>
        <header className="App-header">
          <h1>Company Management</h1>
          <nav>
            <ul>
              {NavMenus()}
            </ul>
          </nav>
        </header>
        <main>
          {mainComp[menu]}
        </main>
      </ApolloProvider>
    </div>
  );
```

## Requête et mutation, fragment

- https://graphql-kr.github.io/learn/queries/
