# Billingo API 2.0 Usage

## API URL

This API enables subscribers of Billingo to connect third-party applications (ie. their e-commerce site)
and generate electronic or traditional invoices automatically.

The Billingo API is available at the following URL: `https://www.billingo.hu/api`


## Changes since 1.0

We have rewritten the whole API backend to be tied much closer to the main app.
Because of this we had to change a lot since the last version.

- IDs from the last release will **NOT** work, please refresh your cached Clients, Payment method and VAT ids.
- We have standardized as much as we could including responses, JSON requests and authentication (more about this below)
- We opened a lot of new endpoints for the public (ie. sending invoices in email)

## Authentication

The authentication method changed to JSON Web Tokens (JWT for short). The authentication should
be sent in the `Authorization` HTTP header for **every** call.

### JSON Web Tokens

JWT are a standardized ([RFC7519](https://tools.ietf.org/html/rfc7519)) and open way for two parties to share
authentication information securely. We are using the HMAC-256 algorithm for secure signatures.

JWTs are made up from three parts separated by dots (`.`). The first is the *header*, the
second is the *payload* and finally the *signature*. Before encoding the following are
JSON objects.

- Header contains (usually) two parts:
    - `alg` which should be the algorithm used for the signature, `HS256` in our case
    - `typ` this should be `JWT`
- Payload contains the claims we authenticate with the signature:
    - `sub`: The user public key (Subject)
    - `iat`: Issued At, the UNIX timestamp when the signature was created
    - `exp`: Expiry, UNIX timestamp when the signature will expire
    - `iss`: Issuer, the origin URI
    - `jti`: Unique token ID, MD5 of the concatenated `sub` and `iat`

**Never** set the expiry to be more than half a minute, tokens that are set for long
expire time might be vulnerable to replay attacks.

Both of the above are Base64Url encoded, which form the first two parts of the token.
The last part of the token is the signature, which is made using the two Base64Url encoded parts of the signature
separated with a dot and signed with the chosen algorithm (HMAC-SHA256 in our case) with
the user's private key.

Much more information and client libraries for almost all programming languages can be found
on the following links:

- http://jwt.io/
- https://auth0.com/learn/json-web-tokens

We recommend that you make yourself familiar with JWT before using our API.

### Example header

`Authorization: Beamer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJmMWI3YzhkZDM0YTkwYzFkMzI4MDgyMTQ2NzJiY2QyZSIsImlhdCI6MTQ0NzkyOTU0OCwiZXhwIjoxNDQ3OTI5NTQ4fQ.2frxLVGY4QDnB7mG1XWnWvAM36LSU58nocU1Ws5Sjzo`

*Note: The header value always starts with the text Beamer followed by a space and then the JWT*

## JSON Schema

We are using [JSON Schema](http://json-schema.org/) (draft v4.) which describe the JSON objects you should send with
`POST` and `PUT` requests.
The link to the schemas are found below, at their appropriate places.

## Successful responses

When a request is successful, the response is always a JSON object. Every response contains a `success` attribute which
can be either `true` or `false`.

- `GET`, `POST`, `PUT` requests:
    - `type`: The type name for the response, for example a call on `/clients` will return `clients`
    - `data`: An array with the response object(s)
- `DELETE` request only contains `success` attribute.

## Errors

Besides the HTTP error code, we return a JSON object in the response body with the
following attributes:

- `success`: always `false` on error
- `error`: Textual representation of the error

If failing to insert or update objects (when JSON schema is otherwise valid), we
also return a `errors` array with the failures.
