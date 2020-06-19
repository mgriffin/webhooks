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
SECRET_TOKEN="your-secret-token"
```

Change `your-secret-token` to the proper secret token.
You can then use `http://[ngrok-hostname]/payload-with-token` as the webhook target.

## ngrok

You can install ngrok from the website, or through homebrew:

```
brew cask install ngrok
```

When it's installed, run it with:

```
ngrok http 4567
```

This will give you a URL that you can use for the hostname of your webhook target.
There's also a localhost URL that you can use to check for traffic to the server.
