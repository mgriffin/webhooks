# A simple server for GitHub repository webhooks

This is a simple sinatra app that you can use to test webhooks from GitHub.com or on a GitHub Enterprise Server.

## Usage

- Clone the repository
- Run `./script/bootstrap` to install the required Gems
- Run `./script/server` to run the server locally
- If you want to make this accessible from the internet, use something like [ngrok](https://ngrok.com/)

You will also have to set up a webhook on GitHub.com or on a GitHub Enterprise instance that can access this server.
The webhook URL will be `http://[ngrok-hostname]/payload` for the basic webhook receiver.

If you want to test webhook validation using a secret key there is another step.

- Create a `.env` file with this content:

```
SECRET-TOKEN="your-secret-token"
```

Change `your-secret-token` to the proper secret token.
You can then use `http://[ngrok-hostname]/payload-with-token` as the webhook target.
