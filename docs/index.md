---
id: index
title: Getting started
---

# rad-modules

## Configuration

After checkout of a repository, please perform the following steps in exact sequence:

1. Copy docker-compose.override
    ```
    $ cp docker-compose.override.yml.dist docker-compose.override.yml
    ```
2. Run `npm i`

3. Run `cd ./services/security && npm i`

4. Run `cd ./services/scheduler && npm i`

5. Run `cd ./services/gateway && npm i`

6. Run `cd ./services/mailer && npm i`

7. Run `npm run docker-build-watcher`

8. Run `npm run docker-build-scheduler`

9. Run `npm run docker-build-security`

10. Run `npm run docker-build-mailer`

11. Run watch - `npm run watch`

Alternatively you can use Make:

1. Run `make install`

2. Run `make docker-build`

## Dev setup

This app is fully dockerized, so in order to use it you have to have docker and docker-compose installed. What's more you need to have npm in order to run npm scripts.

1. In order to run specifc container run:

    ```
    docker-compose up <container-name>
    ```

2. In order to watch files for dev purpose type:

    ```
    npm run watch
    ```

3. If you need to close all containers run:

    ```
    npm run down
    ```

## Code generation

We're using Plop for routes, models, actions, commands and handlers generation.

```
npm run plop
```

## Code style

We're using Prettier and ESLint to keep code clean. In order to reformat/check code run:

```
npm run lint
npm run format
```

## Migrations

Migrations should be stored inside migrations directory of specific service.

Easiest way to create a migration is to generate it from entity/ies. Run inside specific service directory:

```
npm run generate-migration -- <migration-name>
```

This should generate a migration for all connected entities.