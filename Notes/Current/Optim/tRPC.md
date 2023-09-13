https://trpc.io/docs/concepts

# Concepts

## What is RPC? What mindset should I adopt?[​](https://trpc.io/docs/concepts#what-is-rpc-what-mindset-should-i-adopt "Direct link to What is RPC? What mindset should I adopt?")

### It's just functions[​](https://trpc.io/docs/concepts#its-just-functions "Direct link to It's just functions")

RPC is short for "Remote Procedure Call". It is a way of calling functions on one computer (the server) from another computer (the client). With traditional HTTP/REST APIs, you call a URL and get a response. With RPC, you call a function and get a response.

```js
// HTTP/REST

const res = await fetch('/api/users/1');

const user = await res.json();

// RPC

const user = await api.users.getById({ id: 1 });
```

### Don't think about HTTP/REST implementation details[​](https://trpc.io/docs/concepts#dont-think-about-httprest-implementation-details "Direct link to Don't think about HTTP/REST implementation details")

If you inspect the network traffic of a tRPC app, you'll see that it's just fairly standard HTTP requests and responses. But you don't need to think about the implementation details while writing your application code. You call functions, and tRPC takes care of everything else.

## Vocabulary[​](https://trpc.io/docs/concepts#vocabulary "Direct link to Vocabulary")

Below are some terms that are used frequently in the tRPC ecosystem. We'll be using these throughout the documentation, so it's good to get familiar with them. Most of these concepts also have their own pages in the documentation.



### server/trpc.ts
### 1. Create a router instance[​](https://trpc.io/docs/quickstart#1-create-a-router-instance "Direct link to 1. Create a router instance")

First, let's initialize the tRPC backend. It's good convention to do this in a separate file and export reusable helper functions instead of the entire tRPC object.
```ts
import { initTRPC } from '@trpc/server';
 
/**
 * Initialization of tRPC backend
 * Should be done only once per backend!
 */
const t = initTRPC.create();
 
/**
 * Export reusable router and procedure helpers
 * that can be used throughout the router
 */
export const router = t.router;
export const publicProcedure = t.procedure;
```

### server/index.ts
```ts
import { createHTTPServer } from "@trpc/server/adapters/standalone";
import { z } from "zod";
import { db } from "./db";
import { publicProcedure, router } from "./trpc";
 
const appRouter = router({
  userList: publicProcedure
    .query(async () => {
      const users = await db.user.findMany();
      return users;
    }),
  userById: publicProcedure
    .input(z.string())
    .query(async (opts) => {
      const { input } = opts;
      const user = await db.user.findById(input);
      return user;
    }),
  userCreate: publicProcedure
    .input(z.object({ name: z.string() }))
    .mutation(async (opts) => {
      const { input } = opts;
      const user = await db.user.create(input);
      return user;
    }),
});
 
export type AppRouter = typeof appRouter;
 
const server = createHTTPServer({
  router: appRouter,
});
 
server.listen(3000);
```


### server/index.ts

```ts
type User = { id: string; name: string };
 
// Imaginary database
const users: User[] = [];
export const db = {
  user: {
    findMany: async () => users,
    findById: async (id: string) => users.find((user) => user.id === id),
    create: async (data: { name: string }) => {
      const user = { id: String(users.length + 1), ...data };
      users.push(user);
      return user;
    },
  },
};
```


```ts
import { createTRPCProxyClient, httpBatchLink } from '@trpc/client';
import type { AppRouter } from './server';
//     👆 **type-only** import
 
// Pass AppRouter as generic here. 👇 This lets the `trpc` object know
// what procedures are available on the server and their input/output types.
const trpc = createTRPCProxyClient<AppRouter>({
  links: [
    httpBatchLink({
      url: 'http://localhost:3000',
    }),
  ],
});
```