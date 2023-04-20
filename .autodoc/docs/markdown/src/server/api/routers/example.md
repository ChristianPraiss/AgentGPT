[View code on GitHub](/src/server/api/routers/example.ts)

The code above defines a router for the agentgpt project using the trpc library. The router is named `exampleRouter` and contains two procedures: `hello` and `getSecretMessage`.

The `hello` procedure is a public procedure that takes an input object with a single property `text` of type string. It returns an object with a single property `greeting` that concatenates the input `text` with the string "Hello". This procedure can be used to greet a user with a personalized message.

Here is an example of how to use the `hello` procedure:

```javascript
const response = await exampleRouter.query("hello", { text: "world" });
console.log(response.greeting); // "Hello world"
```

The `getSecretMessage` procedure is a protected procedure that does not take any input. It returns a string that can only be accessed by authenticated users. This procedure can be used to retrieve sensitive information that should not be accessible to the general public.

Here is an example of how to use the `getSecretMessage` procedure:

```javascript
const response = await exampleRouter.query("getSecretMessage", null, {
  headers: {
    Authorization: "Bearer <your_access_token>",
  },
});
console.log(response); // "you can now see this secret message!"
```

Overall, this code defines a router that can be used to handle incoming requests and provide responses based on the defined procedures. The `hello` procedure can be used to greet users with personalized messages, while the `getSecretMessage` procedure can be used to retrieve sensitive information that requires authentication.
## Questions: 
 1. What is the purpose of the `zod` library being imported?
- The `zod` library is being used for input validation and type checking.

2. What is the difference between `publicProcedure` and `protectedProcedure`?
- `publicProcedure` is accessible to anyone, while `protectedProcedure` requires authentication to access.

3. What is the expected output of the `hello` procedure?
- The `hello` procedure expects an input object with a `text` property of type string, and returns an object with a `greeting` property that concatenates the input `text` with the string "Hello".