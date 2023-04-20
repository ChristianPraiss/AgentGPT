[View code on GitHub](/.autodoc/docs/json/src/pages/api/webhooks)

The `stripe.ts` file in the `webhooks` folder is responsible for handling webhook events related to customer subscriptions in the agentgpt project. This webhook handler is crucial for keeping the user's subscription status up-to-date in the project's database, based on the events received from Stripe.

The code starts by importing necessary dependencies and creating a new instance of the Stripe API client using the `STRIPE_SECRET_KEY` environment variable. It then defines a `config` object to disable the default body parser for the Next.js API route and sets up the `cors` middleware to allow only `POST` and `HEAD` requests.

The core functionality of this file is in the `webhookHandler` function, which processes incoming webhook events from Stripe. The function first checks if the incoming request is a `POST` request and returns a `405 Method Not Allowed` response if it's not. If the request is valid, it reads the raw body of the request and verifies the Stripe signature using the `stripe.webhooks.constructEvent` method. If the signature is invalid, it returns a `400 Bad Request` response.

Upon receiving a valid webhook event, the function checks the event type. If the event is not related to customer subscriptions, it returns a success response. If the event is related to customer subscriptions, it retrieves the customer's email and finds the corresponding user in the database using the `prisma` ORM. Based on the event type, the function updates the user's subscription status in the database. For example, if the event is `customer.subscription.deleted`, the user's subscription status will be updated accordingly.

The `updateUserSubscription` function is a helper function that takes the user ID and subscription object as arguments and updates the user's subscription ID in the database based on the subscription status.

Finally, the `cors` middleware is applied to the `webhookHandler` function, and the resulting function is exported as the default export of the module.

Here's an example of how this webhook handler might be used in the project:

1. A user subscribes to a premium plan in the agentgpt project, and Stripe sends a `customer.subscription.created` webhook event.
2. The `webhookHandler` function receives the event, verifies the signature, and checks the event type.
3. The function retrieves the customer's email, finds the corresponding user in the database, and updates the user's subscription status to "active".
4. When the user logs in to the agentgpt project, their subscription status is now "active", granting them access to premium features.

In summary, the `stripe.ts` webhook handler plays a crucial role in managing user subscriptions in the agentgpt project by processing webhook events from Stripe and updating the user's subscription status in the database accordingly.
