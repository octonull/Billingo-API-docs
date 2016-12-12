# Billingo API Changelog

Current version: 2.1.1

## Changes since 2.1

- Fixed bank account problem, the `Invoices` endpoint will now accept the `bank_account_uid` parameter in the JSON

  ​

## Changes since 2.0

- Added pagination to data returned from the `Invoices` , `Clients` and `Expenses` endpoints. 

  ​

## Changes since 1.0

We have rewritten the whole API backend to be tied much closer to the main app.
Because of this we had to change a lot since the last version.

- IDs from the last release will **NOT** work, please refresh your cached Clients, Payment method and VAT ids.
- We have standardized as much as we could including responses, JSON requests and authentication (more about this below)
- We opened a lot of new endpoints for the public (ie. sending invoices in email)