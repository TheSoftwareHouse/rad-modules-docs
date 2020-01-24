---
id: security-generate-token
title: Security service communication
---

## How to communicate with Security service:

Our building blocks can communicate with others, e.g. scheduler service needs to run some async action that will have an impact on security service, but to do that service need to have access token to do some business logic otherwise it will receive an unauthorized response.

To receive the token the service needs to ask for one. To do that at first system administrator needs to create API key so we will know what/who created access token.

You can either use endpoint `/api/tokens/create-access-key` to create code or ask administrator to do so from admin panel directly. After you get API key it should be put in "x-api-key" header and send to POST `/api/tokens/generate-token` endpoint.

An example request should look like this :

```
{
    "attributes": [ "ADMIN_PANEL" ],
    "policy": ["user-operation/add-user"],
    "accessExpirationInSeconds": 3600,
    "refreshExpirationInSeconds": 3000
}
```

The result of the operation will be an access token with proper policies. With can be used to process a business logic operation by another service.
