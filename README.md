# Containerized Settings Probot

A containerized [Settings Probot](https://github.com/probot/settings).

## Running

At a minimum, APP_ID and PRIVATE_KEY must be supplied to the container for the application to work. Webhook secret may also be passed:

```ps1
# PowerShell
$APP_ID=<YourAppId>
$PRIVATE_KEY=<YourRsaPrivateKey>
$WEBHOOK_SECRET=<YourWebHookSecret>
docker run -it -p 3000:3000 --name settings_probot -e APP_ID=$APP_ID -e PRIVATE_KEY=$PRIVATE_KEY -e WEBHOOK_SECRET=$WEBHOOK_SECRET trfc:settingsprobot 
```

### Running locally

To run locally, it may prove useful to use a webhook proxy. This can be set via `WEBHOOK_PROXY_URL`:

```ps1
# PowerShell
$APP_ID=<YourAppId>
$PRIVATE_KEY=<YourRsaPrivateKey>
$WEBHOOK_SECRET=<YourWebHookSecret>
$WEBHOOK_PROXY_URL=<YourWebHookProxyUrl>
docker run -it -p 3000:3000 --name settings_probot -e APP_ID=$APP_ID -e PRIVATE_KEY=$PRIVATE_KEY -e WEBHOOK_SECRET=$WEBHOOK_SECRET -e WEBHOOK_PROXY_URL=$WEBHOOK_PROXY_URL trfc:settingsprobot 
```