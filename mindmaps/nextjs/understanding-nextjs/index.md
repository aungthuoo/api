---
title: Understanding Next.js  
markmap: 
  colorFreezeLevel: 2 
  collapsed: false
  nodeMinHeight: 30
  # maxWidth: 300
  initialExpandLevel: 2
---

## Create new Next.js 
- ```sh
    npx create-next-app@latest next_app
    cd next_app 

  ```

## Routers 
- Nested Routes 
  - Folder structure 
    - ```sh
        app/
        ├── layout.js           // Main application layout
        ├── page.js             // Home page
        ├── dashboard/
        │   ├── layout.js       // Dashboard-specific layout
        │   ├── page.js         // Dashboard home
        │   └── settings/
        │       └── page.js     // Dashboard settings
        
      ```
- Dynamic Routes
  - `/blog/[slug]`
  - Folder structure 
    - ```sh
        app/
          └── blog/
              └── [slug]/
                  └── page.js 
      ```
  - In page.js 
    - ```js
      export default function BlogPost({ params }) {
        const { slug } = params;
        // Fetch and render blog post based on slug
      }
      ```
- Route grouping
  - Next.js is instructed not to include the wrapped name in the route
  - Folder structure 
    - ```sh
        app/
          └── (auth)
                └── /login
                └── /signup  
      ```
- Catch-All Routes
  - `/docs/intro/getting-started`
  - For routes that need to capture multiple segments, use the [...param] syntax.
  - Folder structure 
    - ```sh
        app/
          └── docs/
              └── [...slug]/
                  └── page.js 
      ```
  - `/docs/intro/getting-started`
- [ref](https://thiraphat-ps-dev.medium.com/mastering-next-js-app-router-best-practices-for-structuring-your-application-3f8cf0c76580)

## Types of Rendering
- Client Side Rendering (CSR)
- Server Side Rendering (SSR)

## Components 
- Types of Components 
  - Client Components
    - Client Components are rendered in the browser and can use React hooks like useState and useEffect
    - Components that use hooks or browser APIs must be client components, because hooks are not available on the server.
    - need to add 'use client'; at the top of the file
    - Folder structure
      - ```sh
          /app
          ├── /components
          │   └── ClientComponent.tsx
          └── page.tsx 
        ```
    - Examples 
      - ```js
          // app/components/ClientComponent.tsx (Client Component)
          'use client'; // Explicitly makes this a Client Component

          import { useState } from 'react';

          export default function ClientComponent() {
            const [count, setCount] = useState(0);

            return (
              <div>
                <h2>Client Component</h2>
                <p>This component is rendered on the client.</p>
                <button onClick={() => setCount(count + 1)}>
                  Increment Count: {count}
                </button>
              </div>
            );
          } 
        ```
  - Server Components
    - By default, all components in the Next.js app/ directory are Server Components
    - These components run on the server, don’t include JavaScript in the client bundle, and are useful for static content or fetching data from the server
    - which are completely rendered in server but it's important to note that they contain the non-interactive part of the application
    - Examples 
      - ```js 
          // app/page.tsx (Server Component)
          export default function Home() {
            const serverTime = new Date().toLocaleTimeString(); // Data fetched on the server
            return (
              <div>
                <h1>Server Component</h1>
                <p>This component is rendered on the server.</p>
                <p>Server Time: {serverTime}</p>
                <ClientComponent />
              </div>
            );
          }
        ```
    - Adventages 
      - Efficient utilisation of server resources
        - Fetch data and access all backend resources  while rendering in server with less latency
      - Faster Initial Load
        - Improves user experience and accessibility, as javascript file is already rendered and the browser just has to paint the html.
        
      - Reduces Bundle size
        - as only client components send’s  Javascript file to the client, the bundle size javascript reduces.
      - Enhanced SEO
        - improves search engine visibility and better indexing of our web-app
      - Security
        - Safe to use API key within server components

- allows combination of server or client components
- we can have client components inside server components but not vice versa


## GraphQL
- What is GraphQL?
  - A powerful query language that lets you request exactly the data you need.
- Benefits of GraphQL
  - You only get the data you ask for, nothing extra
  - You can shape the data request to fit your needs
  - It uses one pathway to get data instead of many
   
- Setting Up a Next.js Project
  - Create Next.js App
    - ```sh
        npx create-next-app my-app
        cd my-app
      ```
  - Integrating GraphQL in Next.js
    - ```sh  
        npm install graphql @apollo/client apollo-server-micro graphql-tag 
      ```
  - Setting Up Apollo Client
    - ```js
        // lib/apolloClient.js

        import { ApolloClient, InMemoryCache } from '@apollo/client';

        const client = new ApolloClient({
          uri: 'http://localhost:4000/graphql',  
          cache: new InMemoryCache()
        });

        export default client; 
      ```
  - Creating GraphQL Server (Optional)
    - ```js
        // pages/api/graphql.js

        import { ApolloServer } from 'apollo-server-micro';
        import { typeDefs, resolvers } from '../../graphql';

        const apolloServer = new ApolloServer({ typeDefs, resolvers });

        export const config = {
          api: {
            bodyParser: false
          }
        }

        export default apolloServer.createHandler({ path: '/api/graphql' }); 
      ```
  - Fetching Data with GraphQL
    - Writing GraphQL Queries
      - GraphQL queries are like a shopping list for data
      - ```js
          {
            hero {
              name
              height
            }
          }
        ```
      - You can also ask for specific items by using arguments
      - ```js 
          {
            human(id: "1000") {
              name
              homePlanet
            }
          }
        ```
  - Using the useQuery Hook
    - ```js
        import { useQuery } from '@apollo/client';
        .
        const { data, loading, error } = useQuery(GET_HERO, { 
          variables: { id: 1000 }
        });
      ```
  - Displaying Fetched Data
    - First, check if the data is still loading:
    - ```js
        if (loading) return <p>Loading...</p>;
        .
        
      ```
    - If there's an error, show it:
    - ```js 
        if (error) return <p>Error! {error.message}</p>;
      ```
    - use the data to show something on the screen:
    - ```js 
        return (
          <div>
            <h1>{data.hero.name}</h1>
            <p>Height: {data.hero.height}</p> 
          </div>
        );
      ```
  - Updating Data with Mutations
    - Understanding Mutations
      - Think of a mutation as a way to tell your API to do something
        - Add a new item
          - ```js
              mutation {
                createUser(name: "Sarah", email: "sarah@example.com") {
                  id
                  name
                }
              } 
            ```
          - This tells the API to create a new user named Sarah and then gives you back Sarah's new ID and name
        - Change an existing item
        - Remove an item

    - useMutation Hook
      - First, you need to bring it into your project:
      - ```js 
            import { useMutation } from "@apollo/client";
            Then, use it with your mutation like this:

            const [createUser] = useMutation(CREATE_USER);
            This gives you a function (createUser) that you can call to run your mutation.

            const handleSubmit = async () => {
              const { data } = await createUser({
                variables: {
                  name: formState.name,
                  email: formState.email
                }
              });
            }
        ```
      - When you run it, any data the mutation sends back is in data.
    - Updating Cache
      - Sometimes, after you change something with a mutation, the stored data (cache) Apollo Client uses isn't up-to-date anymore.
      - You can fix this by giving an update function when you set up your mutation:
      - ```js 
          const [createUser] = useMutation(CREATE_USER, {
            update(cache, { data }) {
              // Here's where you update the cache with the new data
            }
          })
        ```
      - This way, your cache stays fresh even after making changes!
- Advanced Concepts
  - Subscriptions
    - Subscriptions are a way to keep your app updated with the latest data automatically. 
    - Instead of asking the server for updates, the server sends new data to your app as it happens.
    - need to know about subscriptions
      - They make sure your app always has the newest data without having to ask for it.
      - You set them up with a special setup called Subscription.
      - They usually work over a connection that stays open, so updates can come in any time.
      - Your app listens for certain types of updates.
      - They're great for things like live chats or when you're working on a document with others.
    - To add subscriptions to your Next.js app:
      - Make sure your GraphQL server can handle subscriptions.
      - Use the useSubscription hook in your app.
      - Pick the updates you care about.
      - Enjoy getting updates as they happen.
  - Caching
    - Caching means saving data so your app can load faster. Here are some ways to cache data with Apollo Client:
      - In-memory cache - This is the default and it keeps data ready to use without asking for it again.
      - Cache redirects - This tells your app to use data from the cache instead of getting it again.
      - Offline persistence - This saves your data so it's still there when you come back to the app.
      - Partial queries - This only asks for the data you don't already have.
    - Some tips for good caching:
      - Organize your cache well.
      - Use rules to manage your cache better.
      - Refresh your cache after changes.
      - Keep data in the background ready.
      - Deal with old data smartly.

  - Error Handling
    - Dealing with errors well makes your app more reliable. Here's how to handle errors with GraphQL:

      - Use Apollo's errorPolicy to deal with errors in a general way.
      - Use the error from hooks to catch errors in parts of your app.
      - Show messages that tell users what went wrong in a nice way.
      - Keep track of errors to fix bugs.
      - Have a plan for when things go wrong, like trying again.
      - Know where errors are coming from - is it your app, the network, or the server?
      - Know the difference between a problem with the operation and a bigger system error.
    - For example:
      - ```js 
          // Global error handler
          const errorLink = onError(({ graphQLErrors }) => {
            if (graphQLErrors) 
              sendToLoggingEndpoint(graphQLErrors);
          });

          // Handle errors from useQuery
          if (error) 
            return <p>An error occurred: {error.message}</p> 
        ``` 
    - Handling errors well means your app can keep running smoothly even when things go wrong.


## Prisma 
- What is Prisma? 
  - Prisma is an open-source ORM tool for Node.js and TypeScript, that simplifies connection, querying, migrations, and data modeling to SQL databases.
  - ORM is Object-Relational Mapping, it is a technique in which we can query data, connect and manipulate databases using the object-oriented paradigm. 
  - ORMs can be written in any language, in whatever language it is written in, it encapsulates the code required to manipulate the database. 

  - To query for all foods in the database manually
    - ```js
        var mysql = require("mysql");
        var connection = mysql.createConnection({
          host: "localhost",
          user: "me",
          password: "secret",
          database: "my_db",
        });

        connection.connect();

        connection.query("SELECT * FROM food", function (error, results, fields) {
          if (error) throw error;
          console.log("Results: ", results);
        });

        connection.end();
      ```
  - But with an ORM library, it will be this:
    - ```js 
        const allFoods = Food.getAll("foods")
      ```
    - Simple and neat. With Prisma, it is simpler:
    - ```js 
        async function main() {
          const allFoods = await prisma.food.findMany();
          console.log(allFoods);
        }
      ```
- Pratical example  
  - components 
    - addfood 
    - editfood 
    - foodcard 
    - header
  - pages 
    - api 
      - addFood.js 
      - deleteFood.js 
      - editFood.js 
    - food 
      - Food.module.css 
      - [id].js 
    - foods 
      - Foods.module.css
      - index.js 
    - _app.js 
    - index.js 
  - prisma 
    - migrations 
  - public 
  - styles 
  - .env 
  - .gitignore 
  - README.md 
  - package.js 
  - recipies.md 
  - yarn.lock 

- [Source code](https://github.com/nextjs-prj/prisma-next)
- [Ref](https://daily.dev/blog/nextjs-with-prisma)