[View code on GitHub](/.autodoc/docs/json/src/server/api)

The `.autodoc/docs/json/src/server/api` folder contains the primary router and tRPC server setup for the agentgpt project. It plays a crucial role in defining the API and handling requests related to examples, agents, and accounts in a consistent and organized manner.

The `root.ts` file defines the primary router for the server, which is created using the `createTRPCRouter` function from the `trpc` module. The router is populated with three additional routers: `exampleRouter`, `agentRouter`, and `accountRouter`. These routers are defined in separate files located in the `routers` directory. The `appRouter` object and `AppRouter` type are exported for use in other parts of the project.

Example usage:

```typescript
import { AppRouter } from "./appRouter";

// create an instance of the app router
const router: AppRouter = new AppRouter();

// handle incoming requests
router.handleRequest(req, res);
```

The `trpc.ts` file sets up the tRPC server, defining contexts, initializing the API, and creating routers and procedures for building the API. The contexts provide access to the database and session, while the `createTRPCRouter` function and `publicProcedure`, `enforceUserIsAuthed`, and `protectedProcedure` methods help build the tRPC API.

The `routers` subfolder contains routers for handling various operations, such as managing user accounts, agents, and tasks. The `account.ts` file defines a router for account-related operations, with `subscribe` and `manage` endpoints. The `agentRouter.ts` file defines a router for managing agents, with `create`, `getAll`, `findById`, and `deleteById` methods. The `example.ts` file defines a router named `exampleRouter` with two procedures: `hello` and `getSecretMessage`.

Example usage:

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

These routers work with other modules, like `prisma` for database access and `utils/stripe-utils` for Stripe customer management, to provide a complete system for the agentgpt project.
