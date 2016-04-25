# Clients

Clients object representation.

JSON Schema: [https://www.billingo.hu/json/schema/client.json](https://www.billingo.hu/json/schema/client.json)

## List of clients

### Endpoint

`GET /clients/{id}`

### Parameters
- `id` (integer, optional) - If set, only return the given client object

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
               "country":"United Kingdom"
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

If the name and (if given) the taxcode is the same as an already saved client, without modifying it, we return
the original client object. If the optional `force` parameter is set to `true`, the client will be saved regardless
if it exists or not.

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
        "city": "Preston",
        "postcode": "PR1",
        "country": "United Kingdom"
    }
}
```

### Response 200 (application/json)

```json
{  
   "success":true,
   "type":"clients",
   "data":{  
      "id":1278331717,
      "attributes":{  
         "name":"Gigazoom LLC.",
         "email":"rbrooks5@amazon.com",
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
            "country":"United Kingdom"
         },
         "bank":{  
            "iban":"",
            "swift":"",
            "account_no":""
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
    "billing_address": {
        "street_name": "Moulton",
        "street_type": "Terrace",
        "house_nr": "2797",
        "city": "Preston",
        "postcode": "PR2",
        "country": "United Kingdom"
    }
}
```

### Response 200 (application/json)

```json
{  
   "success":true,
   "type":"clients",
   "data":{  
      "id":1278331717,
      "attributes":{  
         "name":"Gigazoom LLC.",
         "email":"rbrooks5@amazon.com",
         "taxcode":"",
         "billing_address":{  
            "street_name":"Moulton",
            "street_type":"Terrace",
            "house_nr":"2797",
            "block":"",
            "entrance":"",
            "floor":"",
            "door":"",
            "city":"Preston",
            "postcode":"PR2",
            "country":"United Kingdom"
         },
         "bank":{  
            "iban":"",
            "swift":"",
            "account_no":""
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
