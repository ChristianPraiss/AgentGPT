[View code on GitHub](/.autodoc/docs/json/src)

The `src` folder in the `agentgpt` project contains essential code for managing environment variables, hooks, layout, pages, server, services, styles, and utilities. These components work together to provide a complete system for the project, handling authentication, database access, API routing, and user interface.

For example, the `env` folder is responsible for validating, formatting, and ensuring the correct usage of environment variables in the project. It consists of three files: `client.mjs`, `schema.mjs`, and `server.mjs`. These files work together to manage environment variables for both client-side and server-side code.

```javascript
import { env } from "./env.mjs";

console.log(env.MY_ENV_VAR); // logs the value of MY_ENV_VAR
```

The `hooks` folder contains custom hooks, such as `useAgent` and `useAuth`, which handle agent data and user authentication, respectively. These hooks can be used in the larger project to handle user authentication and agent data management.

```javascript
import { useAuth } from "agentgpt";

function MyComponent() {
  const { signIn, signOut, status, session } = useAuth();
  // ...
}
```

The `layout` folder defines a reusable `DefaultLayout` component that provides a consistent layout and styling for the AgentGPT web application. It can be easily used by wrapping it around the content of a page.

```jsx
import DefaultLayout from "./path/to/DefaultLayout";

const MyPage = () => {
  return (
    <DefaultLayout centered>
      <h1>Welcome to my page!</h1>
      <p>This is some content.</p>
    </DefaultLayout>
  );
};
```

The `pages` folder and its subfolders contain essential components and API handlers for the project, enabling users to interact with the project and manage tasks, goal agents, authentication, and subscriptions.

```jsx
import AgentPage from './src/pages/agent';

function App() {
  return (
    <div>
      <AgentPage />
    </div>
  );
}

export default App;
```

The `server` folder contains code for handling authentication, database connections, and API routing in the project. It uses NextAuth.js for authentication, Prisma for database access, and tRPC for API routing.

```javascript
import { getServerAuthSession } from "./auth";

async function getSession(ctx) {
  const session = await getServerAuthSession(ctx);
  return session;
}
```

The `services` folder provides a set of functions and an interface for interacting with an AI agent service that assists users in achieving goals by offering prompts and suggestions for tasks to complete.

```javascript
const modelSettings = { ... };
const goal = "Learn to play guitar";
const tasks = await startGoalAgent(modelSettings, goal);
```

The `styles` folder contains a collection of CSS styles that are used throughout the project to ensure a consistent visual appearance and formatting.

```html
<div class="background">
  <!-- content goes here -->
</div>
```

The `types` folder defines a message parser and a message type for the project, ensuring that messages sent between different components of the project are in a standardized format and contain the necessary information.

```typescript
import { messageParser, Message } from "agentgpt";

function handleMessage(message: unknown): void {
  // ...
}
```

The `utils` folder contains utility functions, constants, and types that are used throughout the project. These utilities are essential for setting up the client-side API, working with different versions of the GPT model, managing tasks, and interacting with the Stripe API.

```javascript
const text = "Here are some tasks: ['Task 1', 'Task 2', 'No tasks added']";
const completedTasks = ['Task 1'];
const tasks = extractTasks(text, completedTasks);
console.log(tasks); // ['Task 2']
```

In summary, the code in the `src` folder provides essential components and configurations for the `agentgpt` project, enabling it to work with different GPT models, manage tasks, interact with the Stripe API, and more.
