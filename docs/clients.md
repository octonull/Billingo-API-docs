# Clients

Clients object representation.

JSON Schema: [https://www.billingo.hu/json/schema/client.json](https://www.billingo.hu/json/schema/client.json)

## `GET /clients/{id}`

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

## `POST /clients`

Create a client.
If the name and (if given) the taxcode is the same as an already saved client, without modifying it, we return
the original client object.

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

## `PUT /clients/{id}`

Update a client with the given ID. On success it returns the modified client object.

### Parameters
- `id` (integer, required) - The ID of the Client object

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

## `DELETE /clients/{id}`

### Parameters
- `id` (integer, required) - The ID of the Client object

### Response 200 (application/json)

```json
{"success":true}
```
