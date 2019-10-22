# Clients

Clients object representation.

JSON Schema: [https://www.billingo.hu/json/schema/client.json](https://www.billingo.hu/json/schema/client.json)

## List of clients

### Endpoint

`GET /clients?page=1&max_per_page=20`

`GET /clients/{id}`

### Parameters
- `id` (integer, optional) - If set, only return the given client object
- `page` (integer, optional, default=1) - If set, return the given page
- `max_per_page` (integer, optional, default=20) - Sets the maximum number of results to return. Absolute maximum is 50!

### Response 200 (application/json)

```json
{
    "success":true,
    "type":"clients",
    "data":[
        {
            "id":1278331717,
            "attributes":{
                "name":"Gigazoom LLC.",
                "email":"rbrooks5@amazon.com",
                "taxcode":"",
                "type": "",
                "fokonyv_szam": "",
                "phone": "",
                "defaults": {
                    "payment_method":"1",
                    "electronic_invoice":"0",
                    "invoice_due_days":"3",
                    "invoice_currency":"HUF",
                    "invoice_template_lang_code":"hu"
                },
                "billing_address":{
                    "street_name":"Moulton",
                    "street_type":"Terrace",
                    "house_nr":"2797",
                    "block":"",
                    "entrance":"",
                    "floor":"",
                    "door":"",
                    "city":"Preston",
                    "postcode":"PR1",
                    "country":"United Kingdom",
                    "district": ""
                },
                "bank":{
                    "iban":"",
                    "swift":"",
                    "account_no":""
                }
            }
        }
    ]
}
```

## Create a client

### Endpoint

`POST /clients`

### Notes

If the `name`, the `taxcode`, and the billing address is the same as an already saved client, without modifying it, we return the original client object. However for the billing address matching to work properly, it is important that it must be split into `street_name`, `street_type` and `house_nr`.

If the optional `force` parameter is set to `true`, the client will be saved regardless if it exists or not.

### Request (application/json)

```json
{
    "name": "Gigazoom LLC.",
    "email": "rbrooks5@amazon.com",
    "taxcode": "123456",
    "force": false,
    "billing_address": {
        "street_name": "Moulton",
        "street_type": "Terrace",
        "house_nr": "2797",
        "block": "A", 
        "entrance": "B", 
        "floor": "3.", 
        "door": "17",
        "city": "Preston",
        "postcode": "PR1",
        "district": "XII", 
        "country": "United Kingdom"
    },
    "phone": "",
    "bank": {
        "account_no": "12345678-12345678-12345678", 
        "iban": "", 
        "swift": ""
    },
    "fokonyv_szam": "", 
    "type": "2", 
    "defaults": {
        "payment_method":"1",
        "electronic_invoice":"0",
        "invoice_due_days":"3",
        "invoice_currency":"HUF",
        "invoice_template_lang_code":"hu"
    }    
}
```

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "clients",
    "data": {
        "id": 1963092040,
        "attributes": {
            "name": "Gigazoom LLC.2",
            "email": "rbrooks5@amazon.com",
            "taxcode": "12345678-0-00",
            "type": 2,
            "fokonyv_szam": "",
            "phone": "00123456789",
            "defaults": {
                "payment_method": "1",
                "electronic_invoice": "0",
                "invoice_due_days": "3",
                "invoice_currency": "HUF",
                "invoice_template_lang_code": "hu"
            },
            "billing_address": {
                "street_name": "Moulton",
                "street_type": "Terrace",
                "house_nr": "2797",
                "block": "A",
                "entrance": "B",
                "floor": "3.",
                "door": "17",
                "city": "Preston",
                "postcode": "PR1",
                "district": "XII",
                "country": "Egyesült Királyság"
            },
            "bank": {
                "iban": "",
                "swift": "",
                "account_no": "12345678-12345678-12345678"
            }
        }
    }
}
```

## Update a client

### Endpoint

`PUT /clients/{id}`

### Parameters
- `id` (integer, required) - The ID of the Client object


### Notes

On success it returns the modified client object.

### Request (application/json)

```json
{
    "name": "Gigazoom LLC.",
    "email": "rbrooks5@amazon.com",
    "taxcode": "123456",
    "force": false,
    "billing_address": {
        "street_name": "Moulton",
        "street_type": "Terrace",
        "house_nr": "2797",
        "block": "A", 
        "entrance": "B", 
        "floor": "3.", 
        "door": "17",
        "city": "Preston",
        "postcode": "PR1",
        "district": "XII", 
        "country": "United Kingdom"
    },
    "phone": "",
    "bank": {
        "account_no": "12345678-12345678-12345678", 
        "iban": "", 
        "swift": ""
    },
    "fokonyv_szam": "", 
    "type": "2", 
    "defaults": {
        "payment_method":"1",
        "electronic_invoice":"0",
        "invoice_due_days":"3",
        "invoice_currency":"HUF",
        "invoice_template_lang_code":"hu"
    }    
}
```

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "clients",
    "data": {
        "id": 1963092040,
        "attributes": {
            "name": "Gigazoom LLC.2",
            "email": "rbrooks5@amazon.com",
            "taxcode": "12345678-0-00",
            "type": 2,
            "fokonyv_szam": "",
            "phone": "00123456789",
            "defaults": {
                "payment_method": "1",
                "electronic_invoice": "0",
                "invoice_due_days": "3",
                "invoice_currency": "HUF",
                "invoice_template_lang_code": "hu"
            },
            "billing_address": {
                "street_name": "Moulton",
                "street_type": "Terrace",
                "house_nr": "2797",
                "block": "A",
                "entrance": "B",
                "floor": "3.",
                "door": "17",
                "city": "Preston",
                "postcode": "PR1",
                "district": "XII",
                "country": "Egyesült Királyság"
            },
            "bank": {
                "iban": "",
                "swift": "",
                "account_no": "12345678-12345678-12345678"
            }
        }
    }
}
```

## Delete client

### Endpoint

`DELETE /clients/{id}`

### Parameters
- `id` (integer, required) - The ID of the Client object

### Response 200 (application/json)

```json
{"success":true}
```
