---
id: mailer-configuration
title: Configuration
---

## Mailer service:

PROTOCOL_PROTOCOL:

- **_Description_**: The variable specifies the protocol that will be used to create the service instance
- **_Default_**: `"http"`

TRANSPORT_TYPE:

- **_Description_**: The variable specifies the transport type for mail sending service
- **_Default_**: `"smtp"`

TRANSPORT_SMTP_POOL:

- **_Description_**: The boolean variable specifies if the pooling will be turned on
- **_Default_**: `true`

TRANSPORT_SMTP_HOST:

- **_Description_**: The variable specifies the host name for mail sending service
- **_Default_**: ``

TRANSPORT_SMTP_PORT:

- **_Description_**: The variable specifies the port for mail sending service
- **_Default_**: `465`

TRANSPORT_SMTP_SECURE:

- **_Description_**: The boolean variable specifies if the mailing service connection should be secure
- **_Default_**: `true`

TRANSPORT_SMTP_AUTH_USER:

- **_Description_**: The variable specifies a username that will be used to login into SMTP service
- **_Default_**: ``

TRANSPORT_SMTP_AUTH_PASSWORD:

- **_Description_**: The variable specifies a password that will be used to login into SMTP service
- **_Default_**: ``

TRANSPORT_SMTP_DEBUG:

- **_Description_**: The boolean variable specifies if the debugging should be allowed in mailing service
- **_Default_**: `false`

TRANSPORT_SMTP_TEMPLATES_ROOT:

- **_Description_**: The variable specifies the path to file with mail templates
- **_Default_**: `"/app/services/mailer/mail-templates/"`

TRANSPORT_SENDGRID_AUTH_KEY:

- **_Description_**: The variable specifies the auth key for SendGrid service if the users will choose that system to send emails
- **_Default_**: ``

LOG_LEVEL

- **_Description_**: The variable specifies the level of logging logs by the logger
- **_Default_**: `"debug"`
