[View code on GitHub](/.autodoc/docs/json/src/server)

The `.autodoc/docs/json/src/server` folder contains essential code for handling authentication, database connections, and API routing in the agentgpt project. It uses NextAuth.js for authentication, Prisma for database access, and tRPC for API routing.

`auth.ts` configures NextAuth.js with authentication providers like Github, Google, and Discord. It also sets up a `PrismaAdapter` for database access and customizes the session object. The `getServerAuthSession` function is a wrapper for getting the user's session on the server-side. Example usage:

```javascript
import { getServerAuthSession } from "./auth";

async function getSession(ctx) {
  const session = await getServerAuthSession(ctx);
  return session;
}
```

`db.ts` sets up a global `prisma` object, an instance of `PrismaClient`, for database access throughout the project. Example usage:

```javascript
import { prisma } from "./db";

async function getUsers() {
  const users = await prisma.user.findMany();
  return users;
}
```

The `api` subfolder contains the primary router and tRPC server setup. The `root.ts` file defines the primary router, which includes `exampleRouter`, `agentRouter`, and `accountRouter`. The `trpc.ts` file sets up the tRPC server, defining contexts and initializing the API.

The `routers` subfolder contains routers for handling various operations. The `account.ts` file defines a router for account-related operations, with `subscribe` and `manage` endpoints. The `agentRouter.ts` file defines a router for managing agents, with `create`, `getAll`, `findById`, and `deleteById` methods. The `example.ts` file defines a router named `exampleRouter` with two procedures: `hello` and `getSecretMessage`. Example usage:

```javascript
// Account router
const subscribeResponse = await accountRouter.mutation("subscribe", { planId: "your_plan_id" });
const manageResponse = await accountRouter.mutation("manage", { subscriptionId: "your_subscription_id" });

// Agent router
const createResponse = await agentRouter.mutation("create", { name: "Agent 1", goal: "Goal 1", tasks: [...] });
const allAgents = await agentRouter.query("getAll");
const agent = await agentRouter.query("findById", { id: "your_agent_id" });
const deleteResponse = await agentRouter.mutation("deleteById", { id: "your_agent_id" });

// Example router
const helloResponse = await exampleRouter.query("hello", { text: "world" });
console.log(helloResponse.greeting); // "Hello world"
const secretMessage = await exampleRouter.query("getSecretMessage", null, {
  headers: {
    Authorization: "Bearer <your_access_token>",
  },
});
console.log(secretMessage); // "you can now see this secret message!"
```

These components work together to provide a complete system for the agentgpt project, handling authentication, database access, and API routing in a consistent and organized manner.
