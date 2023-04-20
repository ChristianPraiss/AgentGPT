[View code on GitHub](/.autodoc/docs/json/src/pages/agent)

The `index.tsx` file in the `agent` folder is responsible for rendering the chat window for a specific agent, along with buttons to share, delete, and go back to the main page. This file is a part of the AgentGPT project and is a crucial component for interacting with individual agents.

The `AgentPage` component uses several hooks and custom components to achieve its functionality. It first initializes a state variable `showCopied` using the `useState` hook, which is used to toggle the display of a toast message when the share button is clicked. It then uses the `useRouter` hook to get the `id` parameter from the query string, which is used to fetch the agent data from the API using the `getAgent` query.

The component extracts the `tasks` property from the `getAgent.data` object and assigns it to the `messages` variable, which is an array of `Message` objects representing the chat history for the agent. It also defines a `shareLink` function that returns a URL-encoded link to the current page, which is used when the share button is clicked.

The `AgentPage` component renders a `DefaultLayout` component that contains a `ChatWindow` component, a row of buttons, and a `Toast` component. The `ChatWindow` component displays the chat history for the agent, along with the agent's name as the title. The row of buttons contains three `Button` components, each with an icon and a label. The first button has a share icon and calls the `window.navigator.clipboard.writeText` method to copy the share link to the clipboard when clicked. The second button has a trash icon and calls the `deleteAgent.mutate` method to delete the agent when clicked. The third button has a backspace icon and calls the `router.push` method to navigate back to the main page when clicked.

The `Toast` component displays a message when the share link is copied to the clipboard. The `model` prop is set to `[showCopied, setShowCopied]`, which binds the `showCopied` state variable to the `Toast` component.

Here's an example of how the `AgentPage` component might be used:

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

In this example, the `AgentPage` component is imported and used within the `App` component. When the `App` component is rendered, it will display the chat window for the specified agent, along with the buttons to share, delete, and go back to the main page.
