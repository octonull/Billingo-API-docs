# Billingo API v2 Usage (depreceted)


**This solution is no longer supported. A newer and better API v3 is ready to use, you can find the [documentation here](https://api.billingo.hu).**


Current version: **2.1.2**

## API URL

This API enables subscribers of Billingo to connect third-party applications (ie. their e-commerce site)
and generate electronic or traditional invoices automatically.

The Billingo API is available at the following URL: `https://www.billingo.hu/api`


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

## Entitlement

- `TRAVEL_AGENCY`: Különbözet szerinti szabályozás - utazási irodák -
- `SECOND_HAND`: Különbözet szerinti szabályozás - használt cikkek -
- `ARTWORK`: Különbözet szerinti szabályozás - műalkotások -
- `ANTIQUES`: Különbözet szerinti szabályozás - gyűjteménydarabok és régiségek -
- `AAM`: Alanyi adómentesség
- `TAM`: Tevékenység közérdekű jellegére vagy egyéb sajátos jellegére tekintettel áfamentes (Áfa tv. 85-87.§)
- `KBAET`: Más tagállamba irányuló áfamentes termékértékesítés (Áfa tv. 89. §)
- `EAM`: Áfamentes termékexport, azzal egy tekintet alá eső értékesítések, nemzetközi közlekedéshez kapcsolódó áfamentes ügyletek (Áfa tv. 98-109. §)
- `NAM_1`: Áfamentes közvetítői tevékenység (Áfa tv. 110. §)
- `NAM_2`: Termékek nemzetközi forgalmához kapcsolódó áfamentes ügylet (Áfa tv. 111-118. §)
- `ATK`: Áfa tv. tárgyi hatályán kívüli ügylet
- `EUFAD37`: Áfa tv. 37. § (1) bekezdése alapján a szolgáltatás teljesítése helye az EU más tagállama (áfa fizetésére a vevő köteles)
- `EUFADE`: Áfa tv. szerint egyéb rendelkezése szerint a teljesítés helye EU más tagállama (áfa fizetésére a vevő köteles)
- `EUE`: EU más tagállamában áfaköteles (áfa fizetésére az értékesítő köteles)
- `HO`: Áfa tv. szerint EU-n kívül teljesített ügylet
