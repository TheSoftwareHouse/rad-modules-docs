---
id: scheduler-details
title: Details
---

## How to download Scheduler service:

You can download the Scheduler service image by using docker command:

```
docker pull tshio/scheduler
```

We keep the image on our public [DockerHub](https://hub.docker.com/r/tshio/scheduler).

## How to set up Scheduler service in your docker-compose file:

```
  scheduler:
    image: tshio/scheduler:latest
    command: api
    hostname: scheduler
    depends_on:
      - redis
    networks:
      - app
```

Scheduler service depends on other container to work correctly: Cache (Redis). Therefore we need to use depends_on property.

## Configuration setting that you can overwrite via environment variables

LOG_LEVEL

- **_Description_**: The variable specifies the level of logging logs by the logger
- **_Default_**: `"debug"`
