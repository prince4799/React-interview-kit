<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](./Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">GraphQL with Apollo Client</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

## 📌 Introduction to GraphQL
GraphQL is a **query language** for APIs that allows clients to request only the data they need. It replaces REST by providing:
- **Declarative data fetching**
- **Strongly-typed schema**
- **Single endpoint for all queries**

## 📌 Why Use Apollo Client?
Apollo Client is a **state management** and **data-fetching** library for GraphQL. It simplifies data fetching and caching by providing:
- Declarative queries using **useQuery** & **useMutation**
- Automatic caching and state management
- Subscription support for real-time data
- Integration with React, React Native, and other frameworks

## 📌 Installing Apollo Client
To set up Apollo Client in a React project, install the required dependencies:
```sh
npm install @apollo/client graphql
```

## 📌 Setting Up Apollo Client
```javascript
import { ApolloClient, InMemoryCache, ApolloProvider } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://your-graphql-api.com/graphql',
  cache: new InMemoryCache()
});

function App() {
  return (
    <ApolloProvider client={client}>
      <YourComponent />
    </ApolloProvider>
  );
}
```

## 📌 Fetching Data with Queries
### 🔹 Writing a GraphQL Query
```javascript
import { gql, useQuery } from '@apollo/client';

const GET_USERS = gql`
  query GetUsers {
    users {
      id
      name
      email
    }
  }
`;

const Users = () => {
  const { loading, error, data } = useQuery(GET_USERS);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <ul>
      {data.users.map(user => (
        <li key={user.id}>{user.name} - {user.email}</li>
      ))}
    </ul>
  );
};
```

## 📌 Modifying Data with Mutations
### 🔹 Writing a GraphQL Mutation
```javascript
import { gql, useMutation } from '@apollo/client';

const ADD_USER = gql`
  mutation AddUser($name: String!, $email: String!) {
    addUser(name: $name, email: $email) {
      id
      name
      email
    }
  }
`;

const AddUserForm = () => {
  const [addUser] = useMutation(ADD_USER);

  const handleSubmit = (event) => {
    event.preventDefault();
    addUser({ variables: { name: 'John Doe', email: 'john@example.com' } });
  };

  return <button onClick={handleSubmit}>Add User</button>;
};
```

## 📌 Real-Time Updates with Subscriptions
### 🔹 Setting Up a Subscription
```javascript
import { gql, useSubscription } from '@apollo/client';

const USER_ADDED = gql`
  subscription OnUserAdded {
    userAdded {
      id
      name
      email
    }
  }
`;

const UserSubscription = () => {
  const { data, loading } = useSubscription(USER_ADDED);
  
  if (loading) return <p>Waiting for new users...</p>;

  return <p>New User: {data.userAdded.name}</p>;
};
```

## 📌 Caching in Apollo Client
Apollo uses an **InMemoryCache** to manage and update cached data.
- **Automatic caching**: Queries are cached for faster access.
- **Updating the cache manually**:
```javascript
const [addUser] = useMutation(ADD_USER, {
  update(cache, { data: { addUser } }) {
    cache.modify({
      fields: {
        users(existingUsers = []) {
          return [...existingUsers, addUser];
        }
      }
    });
  }
});
```

## 📌 Common Interview Questions on Apollo Client
| Question | Answer |
|----------|--------|
| What is Apollo Client? | A GraphQL client for fetching and managing application data. |
| How does Apollo Client handle caching? | Uses an **InMemoryCache** to store query results and avoid unnecessary network requests. |
| What are subscriptions in GraphQL? | A way to get real-time updates from the server using WebSockets. |
| What are the key hooks in Apollo Client? | `useQuery`, `useMutation`, and `useSubscription`. |
| How can you update the cache after a mutation? | Use the `update` function in `useMutation`. |
| What is the difference between REST and GraphQL? | REST uses multiple endpoints, while GraphQL uses a single endpoint with flexible queries. |

## 📌 Conclusion
Apollo Client makes working with GraphQL in React seamless by providing powerful tools for fetching, caching, and managing data. It enhances performance and reduces unnecessary re-renders, making it an essential choice for modern web applications. 🚀


  </div>