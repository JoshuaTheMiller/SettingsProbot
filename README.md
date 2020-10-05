<div align="center">

# Containerized Settings Probot

[![MediumLink](https://img.shields.io/badge/Read%20about%20another%20image%20on%20-Medium-lightgrey?style=flat-square)][medium] [![MIT License](https://img.shields.io/dub/l/vibe-d.svg?style=flat-square)](https://github.com/JoshuaTheMiller/SettingsProbot-Image/blob/main/LICENSE) 

[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/trfc/settingsprobot?style=flat-square)][dockerHub] [![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/trfc/settingsprobot?style=flat-square)][dockerHub] ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/trfc/settingsprobot/latest?style=flat-square) [![Docker Pulls](https://img.shields.io/docker/pulls/trfc/settingsprobot?style=flat-square)][dockerHub]

*A containerized [Settings Probot](https://github.com/probot/settings).*

</div>

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

[dockerHub]: https://hub.docker.com/repository/docker/trfc/settingsprobot
[medium]: https://bit.ly/MediumTerrariaServer
