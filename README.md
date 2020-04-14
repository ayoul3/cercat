# cercat

`certcat` is for **Certificate Catcher**. It's monitores issued certificates from [CertStream](https://certstream.calidog.io/) stream and send an alert to **Slack** if a domain matchs a specified **regexp**.

```bash
               websocket    +----------+   POST
CertSteam <-----------------> certcat  +-----------> Slack
                            | (regexp) |
                            +----------+
```

![screenshot](https://github.com/falcosecurity/falcosidekick/raw/master/screenshot.png)

It's highly inspired by [CertStreamMonitor](https://github.com/AssuranceMaladieSec/CertStreamMonitor/blob/master/README.md), the first idea was to improve performances for catching with a **Golang** version.

## Configuration

Two methods are available for configuration and can be mixed :
- *config file*
- *environment variables* (they override values in *config file*)

### With config file

```bash
---
SlackWebhookURL: "" #Slack Webhook URL
SlackIconURL: "" #Slack Icon (Avatar) URL
SlackUsername: "" #Slack Username
Regexp: ".*\\.fr$" #Regexp to match. Can't be empty. It uses Golang regexp format.
Workers: 20 #Number of workers for consuming feed from CertStream
```

### With env vars

- **SLACKWEBHOOKURL**: Slack Webhook URL
- **SLACKICONURL**: Slack Icon (Avatar) URL
- **SLACKUSERNAME**: Slack Username
- **REGEXP**: Regexp to match, if empty, '.*' is used. Use Golang regexp format.
- **WORKERS**: Number of workers for consuming feed from CertStream

## Run

```
usage: cercat [<flags>]

Flags:
      --help                   Show context-sensitive help (also try --help-long and --help-man).
  -c, --configfile=CONFIGFILE  config file
```

## License

MIT

## Author

Thomas Labarussias - [@Issif](https://www.github.com/issif)