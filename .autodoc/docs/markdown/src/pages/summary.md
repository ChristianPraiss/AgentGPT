[View code on GitHub](/.autodoc/docs/json/src/pages)

The `src/pages` folder in the `agentgpt` project contains the main components and API handlers responsible for rendering the user interface and managing the backend interactions. The folder is organized into two main files, `_app.tsx` and `index.tsx`, and two subfolders, `agent` and `api`.

`_app.tsx` sets up a Next.js application with authentication using NextAuth and analytics tracking using Vercel Analytics. It also includes a TRPC provider for building APIs in TypeScript. This code can be used as a starting point for building a larger web application that requires authentication and analytics tracking.

```jsx
import MyApp from "./path/to/MyApp";

function MyPage() {
  return (
    <MyApp>
      <div>This is my page content</div>
    </MyApp>
  );
}
```

`index.tsx` contains the `Home` component, which renders a chatbot interface for creating and deploying autonomous AI agents. It leverages various components and hooks from the `agentgpt` project to provide a seamless user experience and allows users to customize the behavior of their agents using various settings and configurations.

The `agent` subfolder contains the `AgentPage` component, which renders the chat window for a specific agent, along with buttons to share, delete, and go back to the main page.

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

The `api` subfolder contains API endpoint handlers for processing incoming HTTP requests, interacting with the AgentService, and returning appropriate responses. These handlers enable clients to create tasks, execute tasks, and start goal agents. The `auth` subfolder sets up authentication using NextAuth, while the `trpc` subfolder provides the interface for external clients to interact with the API. The `webhooks` subfolder contains the `stripe.ts` file, which handles webhook events related to customer subscriptions.

```javascript
// Example usage of create.ts
const response = await fetch('/api/agent', {
  method: 'POST',
  body: JSON.stringify({
    modelSettings: {...},
    goal: '...',
    tasks: [...],
    lastTask: '...',
    result: '...',
    completedTasks: [...]
  })
});

const { newTasks } = await response.json();
```

In summary, the `src/pages` folder and its subfolders contain essential components and API handlers for the `agentgpt` project, enabling users to interact with the project and manage tasks, goal agents, authentication, and subscriptions.
