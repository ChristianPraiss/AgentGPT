[View code on GitHub](/.autodoc/docs/json/src/hooks)

The `hooks` folder in the `agentgpt` project contains two custom hooks, `useAgent` and `useAuth`, which are responsible for handling agent data and user authentication, respectively.

The `useAgent` hook is designed to save an agent's information to a backend API. It takes an object with three properties: `name`, `goal`, and `tasks`. The hook first checks the user's authentication status using the `useAuth` hook. If the user is authenticated, it creates a mutation function using the `useMutation` hook from the `api.agent.create` module. This mutation function sends a POST request to the backend API with the agent's information. On successful POST request, the `onSuccess` callback updates the agent's information in the `utils.agent.getAll` cache. The hook returns an object with a `saveAgent` function that can be used to save the agent's information to the backend API.

Example usage of `useAgent`:

```javascript
import { useAgent } from "./useAgent";

function AgentForm() {
  const { saveAgent } = useAgent();

  const handleSubmit = (event) => {
    event.preventDefault();
    const formData = new FormData(event.target);
    const data = {
      name: formData.get("name"),
      goal: formData.get("goal"),
      tasks: [],
    };
    saveAgent(data);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="name">Name:</label>
      <input type="text" name="name" id="name" />
      <label htmlFor="goal">Goal:</label>
      <input type="text" name="goal" id="goal" />
      <button type="submit">Save</button>
    </form>
  );
}
```

The `useAuth` hook provides functions and interfaces for user authentication using the Next.js framework and NextAuth library. It returns an object with four properties: `signIn`, `signOut`, `status`, and `session`. The `signIn` and `signOut` functions handle user authentication and logout, respectively. The `status` property indicates the current authentication status, and the `session` property contains information about the current user session.

The hook also uses the `useEffect` hook to store a unique identifier (UUID) for the user in the browser's local storage when the user is authenticated. This UUID is generated from the user's email address using the `zod` library.

Example usage of `useAuth`:

```javascript
import { useAuth } from "agentgpt";

function MyComponent() {
  const { signIn, signOut, status, session } = useAuth();

  const handleLogin = () => {
    signIn("google");
  };

  const handleLogout = () => {
    signOut();
  };

  return (
    <div>
      {status === "authenticated" ? (
        <p>Welcome, {session.user.email}!</p>
      ) : (
        <button onClick={handleLogin}>Sign in with Google</button>
      )}
      <button onClick={handleLogout}>Sign out</button>
    </div>
  );
}
```

These hooks can be used in the larger project to handle user authentication and agent data management. Components in the application can easily access user authentication status, session information, and trigger sign-in and sign-out actions using the `useAuth` hook. The `useAgent` hook allows components to create and save agents to the backend API, enabling seamless agent data management.
