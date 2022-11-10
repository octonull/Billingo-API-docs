# Invoices
Invoice representation

JSON schemas:

- Invoice: [https://www.billingo.hu/json/schema/invoice.json](https://www.billingo.hu/json/schema/invoice.json)
- Invoice items: [https://www.billingo.hu/json/schema/invoice_item.json](https://www.billingo.hu/json/schema/invoice_item.json)
- Invoice payment: [https://www.billingo.hu/json/schema/invoice_pay.json](https://www.billingo.hu/json/schema/invoice_pay.json)



## Show the invoices

### Endpoint

`GET /invoices?page=1&max_per_page=20`

`GET /invoices/{id}`


### Parameters
- `id` (integer, optional) - If set, only return the given Invoice object
- `page` (integer, optional, default=1) - If set, return the given page
- `max_per_page` (integer, optional, default=20) - Sets the maximum number of results to return. Absolute maximum is 50!

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"invoices",
   "data":[
      {
         "id":1938103373,
         "attributes":{
            "date":"2012-07-30",
            "fulfillment_date":"2012-07-30",
            "due_date":"2015-08-07",
            "invoice_no":"2015-000001",
            "prefixed_invoice_no":"TST / 2015-000001",
            "total":"4445.000",
            "total_paid":"0.000",
            "comment":"",
            "currency":"HUF",
            "client_uid":115387686,
            "block_uid":0,
            "uid":1938103373,
            "items":[
               {
                  "description":"Teszt Term\u00e9k",
                  "net_unit_price":"3500.000",
                  "qty":"1.000",
                  "unit":"db",
                  "vat_id":"1",
                  "item_comment":"",
                  "entitlement": null
               }
            ],
            "client":{
               "name":"Teszt 2000 Kft.",
               "email":"daniel.fekete@voov.hu",
               "taxcode":"12345678-2-00",
               "billing_address":{
                  "street_name":"Valahol utca 300",
                  "street_type":"",
                  "house_nr":"",
                  "block":"",
                  "entrance":"",
                  "floor":"",
                  "door":"",
                  "city":"Sopron",
                  "postcode":"9400",
                  "country":"Magyarorsz\u00e1g"
               },
               "bank":{
                  "iban":"",
                  "swift":"",
                  "account_no":""
               },
               "tax_type": ""
            },
            "payment_method": {
              "id": 2,
              "lang_code": "hu",
              "name": "Átutalás",
              "advance_paid": "0"
            },
            "prefix": "TST"
         }
      }
   ]
}
```



## Save a new invoice

### Endpoint

`POST /invoices`

### Request (application/json)

```json
{
    "fulfillment_date": "2015-12-12",
    "due_date": "2015-12-20",
    "payment_method": 1,
    "comment": "",
    "template_lang_code": "hu",
    "electronic_invoice": 1,
    "currency": "HUF",
    "exchange_rate": 250.0,
    "client_uid": 000000000,
    "block_uid": 0,
    "type": 3,
    "round_to": 0,
  	"bank_account_uid": 000000000,
    "items": [
        {
            "description": "Test Item",
            "vat_id": 1,
            "qty": 1,
            "net_unit_price": 3500,
            "unit": "pc",
            "item_comment": "Item comment",
            "entitlement": null
        },
        {
            "product_uid": 1206264827,
            "qty": 1
        }
    ]
}
```

**Important:** The `block_uid` parameter should _always_ be `0` or the chosen invoice block's ID!

*Note: exchange rate parameter is optional. If not given, the currency daily rate will be downloaded from one of the providers*

*Note: round_to parameter is optional. One of [0, 1, 5, 10], defaults to 0 -> no rounding.*

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"invoices",
   "data":{
      "id":878790507,
      "attributes":{
         "fulfillment_date":"2015-12-12",
         "due_date":"2015-12-20",
         "total":4445,
         "comment":"",
         "currency":"HUF",
         "date":"2015-11-23",
         "invoice_no":"2015-000008",
         "client_uid":115387686,
         "block_uid":1263576876,
         "uid":878790507
      }
   }
}
```

### Setting by gross price
Every item can be set by the gross price. The API will automatically calculate the net unit price from the gross unit price based on the given VAT ID. Set the `gross_unit_price` parameter instead of the `net_unit_price`.

### Invoice types

- 0: Draft
- 1: Proforma invoice
- 2: Not used, reserved
- 3: Normal invoice



## Create download link

### Endpoint

`GET /invoices/{id}/code`

### Parameters

- `id` (string, required) - The Invoice object ID

### Response 200 (application/json)

```json
{
  "success": true,
  "data": {
    "code": "uiowerTI"
  }
}
```

### Access URL

`https://www.billingo.hu/access/c:{code}`

## Generate normal invoice from proforma invoice

### Endpoint

`GET /invoices/{id}/generate`

### Parameters

- `id` (string, required) - The proforma invoice object ID

### Response 200 (application/json)

```json
{
  "success": true,
  "id": 1444388311,
  "data": {
      "id": 1444388311
  }
}
```

## Download invoice

### Endpoint

`GET /invoices/{id}/download`

Please note that the invoice download endpoint is rate limited for every IP to 10 requests per minute.

### Parameters

- `id` (string, required) - The Invoice object ID

### Response 200 (application/pdf)

The invoice PDF is returned

## Cancel the invoice

### Endpoint

`GET /invoices/{id}/cancel`

### Parameters
- `id` (string, required) - The Invoice object ID

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"invoices",
   "data":{
      "id":1557544068,
      "attributes":{
         "date":"2015-11-23",
         "fulfillment_date":"2015-12-12",
         "due_date":"2015-11-23",
         "total":-4445,
         "comment":"",
         "currency":"HUF",
         "invoice_no":"2015-000009",
         "client_uid":115387686,
         "block_uid":1263576876,
         "uid":1557544068
      }
   }
}
```

## Cancel invoice

Invoice statuses:

- STATUS PAID = 1;
- STATUS UNPAID = 2;
- STATUS CANCELED = 4;

### Identifying canceled invoice:
Canceled invoice:
```json
   invoice_no: 2019-00001,
   status: 4, // (2 or 1 for normal invoice)
```

Cancel invoice:
```json
   invoice_no: 2019-00002,
   connected_invoice_no: 2019-00001,
   is_cancel_invoice: 1,
   status: 1,
```

## Send the invoice to the client email address

### Endpoint

`GET /invoices/{id}/send`

### Parameters

- `id` (string, required) - The Invoice object ID

### Response 200 (application/json)

```json
{"success":true}
```

## Pay the full or partial amount of the invoice

### Endpoint
`POST /invoices/{id}/pay`


### Parameters
- `id` (string, required) - The Invoice object ID

### Request (application/json)

```json
{
    "date": "2017-01-01",
    "amount": 12300,
    "payment_method": 2,
    "conversion_rate": 1
}
```

### Response 200 (application/json)

```json
{
    "success": true,
    "data": {
        "fully_paid": true,
        "outstanding": 0
    }
}
```

## Undo payment of the invoice

### Endpoint
`DELETE /invoices/{id}/pay`


### Parameters
- `id` (string, required) - The Invoice object ID

### Response 200 (application/json)

```json
{
    "success":true,
    "data": {
        "fully_paid": false,
        "outstanding": 5000
    }
}
```

## Get the available invoice blocks

### Endpoint

`GET /invoices/blocks`

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"invoice_blocks",
   "data":[
      {
         "id":1263576876,
         "attributes":{
            "name":"Test",
            "prefix":"TST",
            "uid":1263576876
         }
      }
   ]
}
```

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
