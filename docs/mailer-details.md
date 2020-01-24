---
id: mailer-details
title: Details
---

## How to download Mailer service:

You can download the Mailer service image by using docker command:

```
docker pull tshio/mailer
```

We keep the image on our public [DockerHub](https://hub.docker.com/r/tshio/mailer).

## How to set up Mailer service in your docker-compose file:

```
  mailer:
    image: tshio/mailer:latest
    command: api
    hostname: mailer
    environment:
      TRANSPORT_SMTP_PORT: 1025
      TRANSPORT_SMTP_SECURE: "false"
    networks:
      - app
```

As you can see, I added some environment variables to the docker-compose file. The variables allow you to overwrite the default setting of the Mailer service. I just overwrite two of them but you can overwrite all of them (if you need to) a full list of available configuration is bellow.

## Configuration setting that you can overwrite via environment variables

HTTP_PORT:

- **_Description_**: The variable specifies the protocol on with the service will be available.
- **_Default_**:`"50050"`

PROTOCOL_PROTOCOL

- **_Description_**: The variable specifies the protocol of mailer service communication.
- **_Default_**:`"http"`

TRANSPORT_TYPE

- **_Description_**: The variable specifies the protocol of sending mails notifications.
- **_Default_**:`"smtp"`

TRANSPORT_SMTP_POOL

- **_Description_**: The variable specifies the if pool in SMTP configuration will be available.
- **_Default_**:`false`

TRANSPORT_SMTP_HOST

- **_Description_**: The variable specifies host name of our SMTP Server.
- **_Default_**:`""`

TRANSPORT_SMTP_PORT

- **_Description_**: The variable specifies port of our SMTP Server.
- **_Default_**: `465`

TRANSPORT_SMTP_SECURE

- **_Description_**: The variable specifies the connection with our SMTP is secure.
- **_Default_**: `false`

TRANSPORT_SMTP_AUTH_USER

- **_Description_**: The variable specifies the username for our SMTP server.
- **_Default_**:`""`

TRANSPORT_SMTP_AUTH_PASSWORD

- **_Description_**: The variable specifies the password for our SMTP server.
- **_Default_**:`""`

TRANSPORT_SMTP_DEBUG

- **_Description_**: The variable specifies if SMTP server should be in debug mode.
- **_Default_**:`false`

TRANSPORT_SMTP_TEMPLATES_ROOT

- **_Description_**: The variable specifies the path to mail templates.
- **_Default_**:`"/app/services/mailer/mail-templates/"`

TRANSPORT_SENDGRID_AUTH_KEY

- **_Description_**: The variable specifies the auth key of the SendGrid account if you would like to use it instead of using a local SMTP server.
- **_Default_**:`""`

LOG_LEVEL

- **_Description_**: The variable specifies the level of logging logs by the logger available options: `"error"`, `"warn"`, `"help"`, `"info"`, `"debug"`, `"verbose"`, `"silly"`
- **_Default_**:`"debug"`

REQUEST_LOGGER_FORMAT:

- **_Description_**: All requests are logged so the DevOps can check if the request comes from a user or other service (we use morgan library to log information). We created our format to display information but fill free to use one of build-in morgan library available options: `"combined"`, `"common"`, `"dev"`, `"short"`, `"tiny"`
- **_Default_**: `":remote-addr :method :url :status :response-time ms - req-body :body - api-key :apiKey - authorization :authorization"`

REQUEST_BODY_KEYS_TO_HIDE

- **_Description_**: We don't want to look at our users' private data so by default we hide some common properties. If you want to cheng that please provide your string with words you want to hide separated witch coma `,`
- **_Default_**: `"password,token,accessToken,accessKey,authorization"`
