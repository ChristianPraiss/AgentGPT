[View code on GitHub](/.autodoc/docs/json/src/env)

The code in the `env` folder is responsible for validating, formatting, and ensuring the correct usage of environment variables in the agentgpt project. It consists of three files: `client.mjs`, `schema.mjs`, and `server.mjs`.

`client.mjs` validates and formats the client-side environment variables. It imports `clientEnv` and `clientSchema` from `schema.mjs`, and uses the `safeParse` method to validate `clientEnv`. If the validation is successful, the validated environment variables are stored in `_clientEnv`. The `formatErrors` function is used to provide informative error messages in case of validation failures. The code also checks if any variable names in `_clientEnv` do not start with `"NEXT_PUBLIC_"` and throws an error if any invalid names are found. The validated environment variables are exported as `env`.

Example usage of `client.mjs`:
```javascript
import { env } from "./env.mjs";

console.log(env.MY_ENV_VAR); // logs the value of MY_ENV_VAR
```

`schema.mjs` defines the schema for environment variables used in the project. It contains two schema objects: `serverSchema` for server-side environment variables and `clientSchema` for client-side environment variables. The `requiredForProduction` function ensures that certain variables are required in production but optional in development and test environments. The `stringToBoolean` function preprocesses environment variables that are expected to be boolean values. The `serverEnv` and `clientEnv` objects destructure the `process.env` object and assign the values to the corresponding environment variables defined in the schema objects.

Example usage of `schema.mjs`:
```javascript
import { serverEnv } from "agentgpt";

const dbUrl = serverEnv.DATABASE_URL;
const isProduction = serverEnv.NODE_ENV === "production";
```

`server.mjs` ensures that the application is not built with invalid environment variables. It imports `serverSchema`, `serverEnv`, `clientEnv`, and `formatErrors`. It uses `serverSchema` to parse `serverEnv` and stores the result in `_serverEnv`. If the parsing is unsuccessful, it logs an error message with the invalid environment variables and throws an error. The code also checks each key in `_serverEnv.data` to see if it starts with "NEXT_PUBLIC_" and throws an error if it does. Finally, it exports an object `env` that combines `_serverEnv.data` and `clientEnv`.

Example usage of `server.mjs`:
```javascript
import { env } from "./env.mjs";

const API_KEY = env.API_KEY;
const API_URL = env.API_URL;

fetch(`${API_URL}/data`, {
  headers: {
    Authorization: `Bearer ${API_KEY}`,
  },
})
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

In summary, the code in the `env` folder plays a crucial role in managing environment variables for the agentgpt project. It ensures that the variables are valid, correctly formatted, and used appropriately throughout the application.
