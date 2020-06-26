# Able: Push to GitHub

This repository is a simple express web server that consumes webhook requests from Able and pushes them to a target GitHub repo. This can be used to back up your posts from Able and to power a static blog like Gatsby.

You can deploy this app to your preferred service or find one-click deploy buttons for Heroku and Glitch lower down. We plan to update this project to support more use cases in the future. PRs are welcome.

‌

## Installation

This is a basic express app. You can start off by cloning the Git repo:

```shell
git clone https://github.com/able-bio/push-to-github
```

Then, `cd` into the repo root and install the dependencies:

```shell
npm install
```

‌

## Configuration

There are some simple environment variables that you’ll need to set for this app in a `.env` file. You can rename the existing `.env.example` file in the repo to `.env` if you like. These are the variables you’ll need to set:

* `ABLE_TOKEN` - create a webhook in your Able account and grab the token [here](https://able.bio/settings/posts/webhook)
* `GITHUB_TOKEN` -  a GitHub personal access token which you can create [here](https://github.com/settings/tokens)
* `GITHUB_USER` - your GitHub username
* `GITHUB_REPO` - name of the GitHub repo you want to push to
* `CONTENT_PATH` - the path for where markdown files should be stored in the repo

Here’s an example of the `.env.example` file contents:

```
# Token that you can get from the webhook section in your Posts page inside Able settings
# It is used to verify if the request is coming from Able
ABLE_TOKEN=able_webhook_token

# An OAuth2 token that can be generated from Github settings to allow API based access to your repos
# Don't forget to grant access to repos when generating the token
GITHUB_TOKEN=personal_oauth_token

# Your github user name
GITHUB_USER=username

# Github repo where you want the updates to be pushed to
GITHUB_REPO=reponame

# Path for where the post files are inside your repo
# This is an absolute path value from your project root directory
CONTENT_PATH=content/blog
```

‌

## Running the server

You can start the dev server by running

```shell
npm run dev
```

This script uses the `.env` file to inject necessary environment variables and [`nodemon`](https://github.com/remy/nodemon/) to auto reload the dev server.

When trying to debug your development server, you can use something like [ngrok](https://ngrok.com/) to expose your localhost server to be able to listen to webhook requests from Able.

You can also run

```
npm start
```

to run your server \(but that will not run a dev-server\). This is recommended when you are deploying your server.

You can also look into using something like [pm2](https://github.com/Unitech/pm2) to manage your node.js apps in production.

‌

## Deployment

You can deploy this repo just like any simple Node.js app. Just follow the application deployment instructions for the platform you are using.

_**NOTE:** Once you’ve deployed this app remember to go back to your Able webhook settings and point the webhook at your app. Just add the URL for your app as the webhook’s Production URL or Test URL._

‌

### Using Heroku

Heroku makes it really easy to deploy Node.js applications with their one-click deploy button. Just click on the **Deploy to Heroku** button, fill in the necessary `ENV` variable values listed in the form and you should be ready to go.

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

‌

### Using Glitch

Glitch is also a great service that supports one-click set up for a Node.js app.

Click on the **Remix on Glitch** button below to deploy a copy of this git repo to your Glitch account. From there, all you have to do is add the correct `ENV` variable values in a `.env` file in glitch. You can use the `.env.example` and related details mentioned above for reference.

[![Remix on Glitch](https://cdn.glitch.com/2703baf2-b643-4da7-ab91-7ee2a2d00b5b%2Fremix-button.svg)](https://glitch.com/edit/#!/import/git?url=https://github.com/able-bio/push-to-github.git)

‌

## Contributing

If you’d like to extend this app, feel free to submit a PR.

‌