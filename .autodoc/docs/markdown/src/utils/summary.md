[View code on GitHub](/.autodoc/docs/json/src/utils)

The `.autodoc/docs/json/src/utils` folder contains utility functions, constants, and types that are used throughout the `agentgpt` project. These utilities are essential for setting up the client-side API, working with different versions of the GPT model, managing tasks, and interacting with the Stripe API.

For example, `api.ts` sets up the client-side API for the tRPC API, creating the `api` object used to make requests to the server-side API. It also sets up the `httpBatchLink` and `loggerLink` for the API requests and defines the input and output types for the API methods.

`constants.ts` defines constants related to different versions of the GPT model and default limits on how many times the model can be run for different types of users. This allows the project to work with different GPT models and set default limits for users.

`helpers.ts` contains utility functions for managing tasks and performing type checking and string manipulation. For example, the `extractTasks` function can be used to manage tasks like this:

```javascript
const text = "Here are some tasks: ['Task 1', 'Task 2', 'No tasks added']";
const completedTasks = ['Task 1'];
const tasks = extractTasks(text, completedTasks);
console.log(tasks); // ['Task 2']
```

`interfaces.ts` defines the `RequestBody` interface, which is used to ensure that the request body for a specific endpoint in the project is properly formatted and contains all the necessary information for the machine learning model to generate an appropriate response.

`parsers.ts` defines parsers for structured output in the LangChain library, which can be used to validate and parse user input and provide a consistent format for output from the project.

`prompts.ts` provides functionality for generating prompts and creating an instance of the OpenAI class for the AgentGPT project. It can be used in conjunction with other modules and classes to build a complete AI system for task creation and execution.

`stripe-utils.ts` defines functions for retrieving customer information from the Stripe API, such as `getCustomerId` and `getCustomerEmail`. These functions can be used to interact with the Stripe API and manage customer information.

`types.ts` defines the `ModelSettings` type, which is used to configure and customize the machine learning model used throughout the project.

Overall, the code in this folder provides essential utilities and configurations for the `agentgpt` project, enabling it to work with different GPT models, manage tasks, interact with the Stripe API, and more.
