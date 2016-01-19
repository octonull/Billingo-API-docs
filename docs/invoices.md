# Invoices
Invoice representation

JSON schemas:

- Invoice: [https://www.billingo.hu/json/schema/invoice.json](https://www.billingo.hu/json/schema/invoice.json)
- Invoice items: [https://www.billingo.hu/json/schema/invoice_item.json](https://www.billingo.hu/json/schema/invoice_item.json)
- Invoice payment: [https://www.billingo.hu/json/schema/invoice_pay.json](https://www.billingo.hu/json/schema/invoice_pay.json)

## Show the invoices

### Endpoint

`GET /invoices/{id}`


### Parameters
- `id` (integer, optional) - If set, only return the given Invoice object

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
            "total":"4445.000",
            "total_paid":"0.000",
            "comment":"",
            "currency":"HUF",
            "client_uid":115387686,
            "block_uid":1263576876,
            "uid":1938103373,
            "items":[
               {
                  "description":"Teszt Term\u00e9k",
                  "net_unit_price":"3500.000",
                  "qty":"1.000",
                  "unit":"db",
                  "vat_id":"1",
                  "item_comment":""
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
               }
            }
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
    "client_uid": 115387686,
    "block_uid": 1263576876,
    "type": 3,
    "items": [
        {
            "description": "Test Item",
            "vat_id": 1,
            "qty": 1,
            "net_unit_price": 3500,
            "unit": "pc"
        }
    ]
}
```

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

### Invoice types

- 0: Draft
- 1: Proforma invoice
- 2: Not used, reserved
- 3: Normal invoice

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
`GET /invoices/{id}/pay`


### Parameters
- `id` (string, required) - The Invoice object ID

### Request (application/json)

```json
{
    "date": "2017-01-01",
    "amount": 12300,
    "payment_method": 2
}
```

### Response 200 (application/json)

```json
{"success":true}
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
