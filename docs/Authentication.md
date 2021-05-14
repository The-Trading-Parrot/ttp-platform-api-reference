# Authentication

Your client will ask the user to authenticate himself through the TTP website (thetradingparrot.com) by using the OAuth2 _Authorization Code_ grant type.

You will ask your user to `Login with thetradingparrot.com`, obtaing the access token and use that to authenticate your API requests. The details are explained in this document.

## Authoriztion flow

The Authorization Code grant type is a **2 part** process. The code token must be requested and then exchanged for an access token.

The host to use is ```https://thetradingparrot.com``` .

### Step 1: Getting an Auth code

Request:

```bash
GET
/oauth/authorize
```

Required request prameters:


`client_id` – The client ID making the request
`redirect_uri` – The URL to redirect back to; this parameter must match the one you communicated when the OAuth2 client has been created
`response_type` – Must be `code`


Response:

```bash
code (string) – The authorization code.
```

You can perform this request by implementing a "Login with thetradingparrot.com" link that will redirect the user to the TTP website.

### Step 2: Gaining an Access Token

Once you have the authorization code, you must make another request to obtain an access token. The authorization code is only valid for approximately 30 seconds.

Request:

```bash
POST
/oauth/token
```

Required request body parameters:

`grant_type` – Must be `authorization_code`
`code` – The code previously returned from the authorization server
`client_id` – Your client id
`client_secret` – Your client secret
`redirect_uri` – URL to redirect the user back to (matching the one used before to authorize)

Response:

```json
{
    "access_token": "aph6jiiwsvgyt9j4fohayegypbo65f8fpjodpdckuiqho0p4wf",
    "expires_in": 86400,
    "token_type": "Bearer",
    "scope": "basic",
    "refresh_token": "g1b4cph2kjnwojzofajvqsfzb2oltjthtermizvlnzsaqjl2o9"
}
```

## Authenticating requests

You can now use the `access_token` returned above to authenticate all API requests using the HTTP bearer authentication, by passing the `Authorization: Bearer <access_token>` in the request headers.

## Refresh token

You can refresh the user access_token by invoking:

```bash
GET
/oauth?=token
```

Required parameters:

```bash
grant_type – "refresh_token"
refresh_token – A Valid Refresh Token.
```

Response:

```json
{
    "access_token": "nziindid3if24vrjbp6cdzyxiuybrcjjsd6grks7",
    "expires_in": 86400,
    "token_type": "Bearer",
    "scope": "basic",
    "request_token": "khaskdjhkhasdnaiwbwsh123"
}
```
