---
id: security-details
title: Details
---

## How to download Security service:

You can download the Security service image by using docker command:

```
docker pull tshio/security
```

We keep the image on our public [DockerHub](https://hub.docker.com/r/tshio/security).

## How to set up Security service in your docker-compose file:

```
  security:
    image: security-service:latest
    command: [sh, -c, 'node-dev ./src/index.js']
    hostname: security
    environment:
      ACCESS_TOKEN_SECRET: secret1234
      RESET_PASSWORD_RANDOM: true
      ACCESS_TOKEN_EXPIRATION: 1000
    depends_on:
      - postgres
      - redis
    networks:
      - app
```

As you can see, I added some environment variables to the docker-compose file. The variables allow you to overwrite the default setting of the Security service. I just overwrite three of them but you can overwrite all of them (if you need to) a full list of available configuration is bellow.

Security service depends on two other containers to work correctly: DB (Postgres in this situation) and cache (Redis). Therefore we need to use depends_on property.

If you would like to initialize the database with users that you already have you can do it by putting the data about users in users.json file after you need to overwrite increment variable with the path to the file with data: `INITIAL_USERS_DATA_JSON_PATH`

users.json schema:

```
[
    {
      username: "user1",
      password: "passw0rd",
      attributes: ["attr1", "attr2"],
    },
    {
      username: "user2",
      password: "passw0rd",
      attributes: ["attr1", "attr2"],
    },
]

```

As you can see you can also initiate data for policy by providing data into policy.js file and overwriting environment variable with the path: `INITIAL_POLICIES_DATA_JSON_PATH`

policy.json schema:

```
[
    {
      resource: "res1",
      attribute: "attr1",
    },
    {
      resource: "res1",
      attribute: "attr2",
    },
    {
      resource: "res2",
      attribute: "attr1",
    },
    {
      resource: "res2",
      attribute: "attr1",
    },
    {
      resource: "res1",
      attribute: "attr1",
    },
    {
      resource: "res1",
      attribute: "attr1",
    },
  ]

```

## Configuration setting that you can overwrite via enviremnt variables

RESET_PASSWORD_REGEX:

- **_Description_**: Regexp that shows how the password suppose to look like
- **_Default_**: `".{8,}"`

RESET_PASSWORD_RANDOM:

- **_Description_**: The variable specifies if the user should provide a new password in reset password flow, or the password will be generated randomly by the system.
- **_Default_**: `false`

RESET_PASSWORD_RANDOM_MAX_LENGTH:

- **_Description_**: The variable specifies the length of the randomly generated password.
- **_Default_**: `8`

REDIS_URL:

- **_Description_**: The variable specifies URL to Redis.
- **_Default_**: `"redis://redis:6379"`

ACCESS_TOKEN_EXPIRATION:

- **_Description_**: The variable specifies how long the access token will be available in seconds
- **_Default_**: `600`

ACCESS_TOKEN_SECRET:

- **_Description_**: The variable specifies secret that will be used for generating the access token
- **_Default_**: `"secret1"`

REFRESH_TOKEN_EXPIRATION:

- **_Description_**: The variable specifies how long the refresh token will be available in seconds
- **_Default_**: `600`

REFRESH_TOKEN_SECRET:

- **_Description_**: The variable specifies secret that will be used for generating the refresh token
- **_Default_**: `"secret2"`

CONNECTION_STRING:

- **_Description_**: The variable specifies the database connection string
- **_Default_**: `"postgres://postgres:password@postgres:5432/users"`

DB_LOGGING:

- **_Description_**: The variable specifies if the logging in the database should be turned on
- **_Default_**: `true`

OAUTH_CLIENT_ID:

- **_Description_**: The variable specifies the id of external OAuth provider
- **_Default_**: `""`

OAUTH_SECRET:

- **_Description_**: The variable specifies the secret for external OAuth provider
- **_Default_**: `""`

OAUTH_ALLOWED_DOMAINS:

- **_Description_**: A comma separated list of domains that are allowed to login using oauth
- **_Default_**: `[]`

REDIRECT_URI:

- **_Description_**: The variable specifies the redirect URL for external OAuth provider
- **_Default_**: `"http://lvh.me:50050/api/users/oauth-redirect"`

INITIAL_USERS_DATA_JSON_PATH:

- **_Description_**: The variable specifies the path to file with initial data for the "User" table
- **_Default_**: `"/app/services/security/init-data-volume/users.json"`

INITIAL_POLICIES_DATA_JSON_PATH:

- **_Description_**: The variable specifies the path to file with initial data for the "Policies" table
- **_Default_**: `"/app/services/security/init-data-volume/policy.json"`

LOG_LEVEL:

- **_Description_**: The variable specifies the level of logging logs by the logger
- **_Default_**: `"debug"`

IS_USER_ACTIVATION_NEEDED:

- **_Description_**: The variable specifies if user after register needs to activate the account with an activation link
- **_Default_**: `false`

TIME_TO_ACTIVE_ACCOUNT_IN_DAYS:

- **_Description_**: The variable specifies how long can activate the registered account (in days)
- **_Default_**: `3`
