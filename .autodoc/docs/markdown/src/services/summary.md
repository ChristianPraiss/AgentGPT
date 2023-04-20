[View code on GitHub](/.autodoc/docs/json/src/services)

The `agent-service.ts` file in the `src/services` folder provides a set of functions and an interface for interacting with an AI agent service that assists users in achieving goals by offering prompts and suggestions for tasks to complete. The code defines three main functions: `startGoalAgent`, `executeTaskAgent`, and `createTasksAgent`, as well as the `AgentService` interface.

The `startGoalAgent` function initializes a new goal by taking a `modelSettings` object and a `goal` string as arguments. It creates a new `LLMChain` object, which is a language model that generates text based on a given prompt. The function uses the `startGoalPrompt` prompt to initiate a new goal, passing the `goal` string as a parameter. The `LLMChain` object generates a completion based on the prompt and returns it as a string. The `extractTasks` function is then called to extract any tasks from the completion text, and the resulting array of tasks is returned.

Example usage:

```javascript
const modelSettings = { ... };
const goal = "Learn to play guitar";
const tasks = await startGoalAgent(modelSettings, goal);
```

The `executeTaskAgent` function prompts the user to execute a task related to a given goal. It takes a `modelSettings` object, a `goal` string, and a `task` string as arguments. It creates a new `LLMChain` object with the `executeTaskPrompt` prompt, passing the `goal` and `task` strings as parameters. The `LLMChain` object generates a completion based on the prompt and returns it as a string.

Example usage:

```javascript
const modelSettings = { ... };
const goal = "Learn to play guitar";
const task = "Practice chord transitions";
const result = await executeTaskAgent(modelSettings, goal, task);
```

The `createTasksAgent` function prompts the user to create a list of tasks related to a given goal. It takes a `modelSettings` object, a `goal` string, an array of `tasks`, a `lastTask` string, a `result` string, and an optional array of `completedTasks` as arguments. It creates a new `LLMChain` object with the `createTasksPrompt` prompt, passing the `goal`, `tasks`, `lastTask`, and `result` strings as parameters. The `completedTasks` array is used to keep track of any tasks that have already been completed. The `LLMChain` object generates a completion based on the prompt and returns it as a string. The `extractTasks` function is then called to extract any new tasks from the completion text, and the resulting array of tasks is returned.

Example usage:

```javascript
const modelSettings = { ... };
const goal = "Learn to play guitar";
const tasks = ["Learn basic chords", "Practice chord transitions"];
const lastTask = "Learn basic chords";
const result = "Successfully learned basic chords";
const newTasks = await createTasksAgent(modelSettings, goal, tasks, lastTask, result);
```

The `AgentService` interface defines the three functions mentioned above, each with specific arguments and return types. The `OpenAIAgentService` object implements the `AgentService` interface and uses the functions defined in this code to interact with an AI agent service. The `MockAgentService` object is used for testing and provides mock data for the functions.

This code can be integrated into a larger project to incorporate the AI agent service into an application or system, helping users achieve their goals by providing task suggestions and prompts.
