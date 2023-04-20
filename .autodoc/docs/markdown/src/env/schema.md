[View code on GitHub](/src/env/schema.mjs)

This code defines the schema for environment variables used in a Next.js project and ensures that the app is not built with invalid environment variables. 

The `serverSchema` object defines the schema for server-side environment variables, including `DATABASE_URL`, `NODE_ENV`, `NEXTAUTH_SECRET`, `NEXTAUTH_URL`, `OPENAI_API_KEY`, `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, `GITHUB_CLIENT_ID`, `GITHUB_CLIENT_SECRET`, `DISCORD_CLIENT_ID`, `DISCORD_CLIENT_SECRET`, `STRIPE_SECRET_KEY`, `STRIPE_WEBHOOK_SECRET`, and `STRIPE_SUBSCRIPTION_PRICE_ID`. 

The `clientSchema` object defines the schema for client-side environment variables, including `NEXT_PUBLIC_VERCEL_ENV`, `NEXT_PUBLIC_FF_AUTH_ENABLED`, `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY`, `NEXT_PUBLIC_FF_SUB_ENABLED`, `NEXT_PUBLIC_FF_MOCK_MODE_ENABLED`, and `NEXT_PUBLIC_VERCEL_URL`. 

The `requiredForProduction` function is used to ensure that certain environment variables are required in production but optional in development and test environments. 

The `stringToBoolean` function is used to preprocess environment variables that are expected to be boolean values. 

The `serverEnv` and `clientEnv` objects are used to manually destructure the `process.env` object and assign the values to the corresponding environment variables defined in the schema objects. 

Overall, this code ensures that the app is built with valid environment variables and provides a convenient way to access and use these variables throughout the project. 

Example usage:
```
import { serverEnv } from "agentgpt";

const dbUrl = serverEnv.DATABASE_URL;
const isProduction = serverEnv.NODE_ENV === "production";
```
## Questions: 
 1. What is the purpose of the `serverSchema` and `clientSchema` objects?
   
   Answer: The `serverSchema` and `clientSchema` objects specify the schema for the server-side and client-side environment variables respectively. They ensure that the app is not built with invalid environment variables.

2. What is the purpose of the `requiredForProduction` function?
   
   Answer: The `requiredForProduction` function returns a Zod schema that requires a string value if the `NODE_ENV` environment variable is set to "production", and makes the string value optional otherwise.

3. Why is the `stringToBoolean` function defined?
   
   Answer: The `stringToBoolean` function returns a Zod schema that preprocesses a string value to a boolean value. It is used to ensure that environment variables that are expected to be boolean values are correctly parsed.