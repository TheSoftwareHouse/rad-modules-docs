---
id: rad-admin-panel-index
title: Details
---

## Description:

Each of the services provides a REST API to manage resources. But if you would like you can run the admin panel with GUI. In the admin panel, you will be able to manage e.g. users and policies. Below you can check how simple it is to connect the panel.

If you didn't change default credential for admin user you can log in into the panel by using login: "super admin", password: "super admin"

If you will use the security module in production remember to change these credentials.

## Working example docker-compose.yaml

```
version: "3.7"

services:
  postgres:
    image: postgres:10-alpine
    environment:
      POSTGRES_PASSWORD: password
      POSTGRES_USERNAME: postgres
      POSTGRES_DB: users
    networks:
      - app

  redis:
    image: redis:4-alpine
    hostname: redis
    networks:
      - app

  security:
    image: tshio/security:0.0.46
    working_dir: /app/build/services/security
    command: api
    hostname: security
    volumes:
      - ./init-data-volume/:/app/services/security/init-data-volume
    environment:
      REACT_APP_SECURITY_API_URL: "http://localhost:50050"
    ports:
      - "50050:50050"

    depends_on:
      - postgres
      - redis
    networks:
      - app

  security-panel:
    image: tshio/rad-admin:0.0.3
    environment:
      REACT_APP_SECURITY_API_URL: "http://localhost:50050"
    ports:
      - 9000:80
    networks:
      - app

networks:
  app:

```
