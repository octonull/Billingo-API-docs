# API Authentication

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

`Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJmMWI3YzhkZDM0YTkwYzFkMzI4MDgyMTQ2NzJiY2QyZSIsImlhdCI6MTQ0NzkyOTU0OCwiZXhwIjoxNDQ3OTI5NTQ4fQ.2frxLVGY4QDnB7mG1XWnWvAM36LSU58nocU1Ws5Sjzo`

**Important: In the earlier editions we made a typo calling the Bearer text as "Beamer", the API will work with both texts!**

*Note: The header value always starts with the text Bearer followed by a space and then the JWT*



## Server time

There can be a time difference between your server and ours. If you get errors messages saying that the signature is expired, you should check both times, and adjust your `iat` and `exp` parameters accordingly. You can use the `leeway` parameter in the official PHP library.

You can also check the Billingo server time at the following URL:

[https://www.billingo.hu/time](https://www.billingo.hu/time)

or to get the data in a JSON format:

[https://www.billingo.hu/time?type=json](https://www.billingo.hu/time?type=json)

Both of these endpoints are available without authentication