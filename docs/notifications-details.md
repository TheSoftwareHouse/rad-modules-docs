---
id: notifications-details
title: Details
---

## How to download Notifications service:

You can download the Notifications service image by using docker command:

```
docker pull tshio/notifications
```

We keep the image on our public [DockerHub](https://hub.docker.com/r/tshio/notifications).

## How to set up Notifications service in your docker-compose file:

```
  notifications:
    image: tshio/notifications:latest
    command: api
    hostname: notifications
    environment:
      ACCESS_TOKEN_EXPIRATION: 800
    networks:
      - app
```

As you can see, I added some environment variables to the docker-compose file. The variables allow you to overwrite the default setting of the Notifications service. I just overwrite one of them but you can overwrite all of them (if you need to) a full list of available configuration is bellow.

## Configuration setting that you can overwrite via environment variables

ACCESS_TOKEN_EXPIRATION

- **_Description_**: The variable specifies how long the access token will be available in seconds
- **_Default_**: `600`

ACCESS_TOKEN_SECRET

- **_Description_**: The variable specifies secret that will be used for generating the access token
- **_Default_**: `"secret1"`

LOG_LEVEL

- **_Description_**: The variable specifies the level of logging logs by the logger
- **_Default_**: `"debug"`
