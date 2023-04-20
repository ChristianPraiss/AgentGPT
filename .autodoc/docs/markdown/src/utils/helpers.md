[View code on GitHub](/src/utils/helpers.ts)

This file contains several utility functions that are used in the larger agentgpt project. 

The `isArrayOfType` function checks whether an array is of a specified type. It takes in an array and a type, and returns a boolean indicating whether the array is of the specified type. This function is useful for type checking in the project.

The `extractTasks` function takes in a string and an array of completed tasks, and returns an array of tasks that have not been completed. It does this by first extracting an array of tasks from the input string using the `extractArray` function, and then filtering out tasks that have already been completed or are not real tasks using the `realTasksFilter` function. This function is likely used in the project to manage tasks.

The `extractArray` function takes in a string and extracts an array of strings from it. It does this by using a regular expression to match an outer array of strings (including nested arrays) in the input string, and then parsing the matched string to get the array. This function is useful for extracting arrays from strings in the project.

The `realTasksFilter` function takes in a string and returns a boolean indicating whether the string represents a real task. It does this by checking the string against several regular expressions that match strings that do not represent real tasks. This function is used by the `extractTasks` function to filter out non-real tasks.

Overall, these utility functions are used in the agentgpt project to manage tasks and perform type checking and string manipulation. An example usage of the `extractTasks` function might look like this:

```
const text = "Here are some tasks: ['Task 1', 'Task 2', 'No tasks added']";
const completedTasks = ['Task 1'];
const tasks = extractTasks(text, completedTasks);
console.log(tasks); // ['Task 2']
```
## Questions: 
 1. What is the purpose of the `isArrayOfType` function?
- The `isArrayOfType` function checks whether an array is of the specified type and returns a boolean value.

2. What is the purpose of the `extractTasks` function?
- The `extractTasks` function takes in a string and an array of completed tasks, and returns an array of tasks that are not completed and are extracted from the input string.

3. What is the purpose of the `realTasksFilter` function?
- The `realTasksFilter` function filters out tasks that are not real tasks, such as "No tasks added", "Task complete", and "Do nothing".