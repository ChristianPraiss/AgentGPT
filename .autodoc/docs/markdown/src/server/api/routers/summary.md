[View code on GitHub](/.autodoc/docs/json/src/server/api/routers)

The `.autodoc/docs/json/src/server/api/routers` folder contains routers for handling various operations in the agentgpt project. These routers are created using the `trpc` module and can be used in conjunction with other parts of the project to provide a complete system.

### account.ts

The `account.ts` file defines a router for handling account-related operations. It has two endpoints, `subscribe` and `manage`, both of which require authentication.

- `subscribe`: Creates a new Stripe checkout session for the user to subscribe to a plan. It retrieves the user's information from the database using the `prisma` module and creates a new checkout session using the Stripe API.
- `manage`: Creates a new Stripe billing portal session for the user to manage their subscription. It retrieves the user's subscription ID from the session and creates a new billing portal session using the customer ID associated with the subscription.

Example usage:

```javascript
const subscribeResponse = await accountRouter.mutation("subscribe", { planId: "your_plan_id" });
const manageResponse = await accountRouter.mutation("manage", { subscriptionId: "your_subscription_id" });
```

### agentRouter.ts

The `agentRouter.ts` file defines a router for managing agents. It has four methods: `create`, `getAll`, `findById`, and `deleteById`.

- `create`: Creates a new agent in the database with the given `name`, `goal`, and `tasks`. It also creates associated `agentTask` objects in the database.
- `getAll`: Returns an array of up to 20 agents belonging to the current user and not deleted, sorted by `createDate` in descending order.
- `findById`: Returns the agent object with the corresponding `id` from the database, along with an array of associated `agentTask` objects.
- `deleteById`: Marks the corresponding agent object in the database as deleted by setting its `deleteDate` property to the current date.

Example usage:

```javascript
const createResponse = await agentRouter.mutation("create", { name: "Agent 1", goal: "Goal 1", tasks: [...] });
const allAgents = await agentRouter.query("getAll");
const agent = await agentRouter.query("findById", { id: "your_agent_id" });
const deleteResponse = await agentRouter.mutation("deleteById", { id: "your_agent_id" });
```

### example.ts

The `example.ts` file defines a router named `exampleRouter` with two procedures: `hello` and `getSecretMessage`.

- `hello`: A public procedure that takes an input object with a single property `text` of type string and returns an object with a single property `greeting` that concatenates the input `text` with the string "Hello".
- `getSecretMessage`: A protected procedure that returns a string that can only be accessed by authenticated users.

Example usage:

```javascript
const helloResponse = await exampleRouter.query("hello", { text: "world" });
console.log(helloResponse.greeting); // "Hello world"

const secretMessage = await exampleRouter.query("getSecretMessage", null, {
  headers: {
    Authorization: "Bearer <your_access_token>",
  },
});
console.log(secretMessage); // "you can now see this secret message!"
```

These routers provide a way to handle various operations in the agentgpt project, such as managing user accounts, agents, and tasks. They can be used with other modules, like `prisma` for database access and `utils/stripe-utils` for Stripe customer management.
