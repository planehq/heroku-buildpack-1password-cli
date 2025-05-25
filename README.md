# Heroku Buildpack for 1Password CLI

This buildpack allows you to easily install and configure the 1Password CLI tool on your Heroku app.

## Usage

To use this buildpack, follow these steps:

1. Add the buildpack to your Heroku app:

  ```bash
  heroku buildpacks:add https://github.com/planehq/heroku-buildpack-1password-cli
  ```

2. Create a service account on 1Password by following these steps:

  - Log in to your 1Password account.
  - Go to the "Settings" section.
  - Click on "Service Accounts" in the sidebar.
  - Click on "New Service Account" and provide a name for the account.
  - Generate a new token for the service account and copy it.

  Once you have created the service account, set the `OP_SERVICE_ACCOUNT_TOKEN` environment variable with the generated token:

  ```bash
  heroku config:set OP_SERVICE_ACCOUNT_TOKEN=your_service_account_token
  ```

  This token will be used by the buildpack to authenticate with 1Password CLI.

3. Deploy your app:

  ```bash
  git push heroku master
  ```

4. Verify that the 1Password CLI is installed and authenticated:

  ```bash
  heroku run op user get --me
  ```

## Preloading secrets from 1password into ENV vars

In order to run processes with ENV set from 1password secrets, follow the
[Load secrets into the environment](https://developer.1password.com/docs/cli/secrets-environment-variables/) guide.

## License

This buildpack is released under the MIT License. See [LICENSE](LICENSE) for more information.
