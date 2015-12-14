# Expenses
Expenses representation

JSON Schema: [https://www.billingo.hu/json/schema/expense.json](https://www.billingo.hu/json/schema/expense.json)

## List of expenses

### Endpoint

`GET /expenses`

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"expenses",
   "data":[
      {
        "id": 1263576876,
         "attributes": {
           "categories_id": "6",
           "name": "Teszt",
           "invoice_no": "1",
           "gross_price": "5000.00",
           "vat": "1",
           "uid": 1263576876,
           "client_uid": 1482050150,
           "client": {
             "name": "Teszt Kft.",
             "email": "daniel.fekete@voov.hu",
             "taxcode": "HU111111",
             "billing_address": {
               "street_name": "Deák tér 66-68",
               "street_type": "",
               "house_nr": "",
               "block": "",
               "entrance": "",
               "floor": "",
               "door": "",
               "city": "Sopron",
               "postcode": "9400",
               "country": "Magyarország"
             },
             "bank": {
               "iban": "",
               "swift": "",
               "account_no": ""
             }
           }
         }
      }
   ]
}
```

## List of available expense categories

### Endpoint

`GET /expenses/categories/{langcode}`

### Parameters

- `langcode` (string, required) - Only `hu` is supported at the moment

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"expense_categories",
   "data":[
      {
         "id":"1",
         "attributes":{
            "id":"1",
            "lang_code":"hu",
            "name":"Category name"
         }
      }
   ]
}
```

## Create Expense object

### Endpoint

`POST /expenses`

### Request (application/json)
```json
{
    "categories_id": 2,
    "name": "Office Supplies",
    "invoice_no": "2015/123456",
    "client_uid": 123456789,
    "gross_price": 1200,
    "vat": 1,
    "currency": "EUR",
    "due_date": "2017-01-15"
}
```

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"expenses",
   "data":{
      "id":1482050150,
      "attributes":{
         "categories_id":2,
         "name":"Office Supplies",
         "invoice_no":"2015\/123456",
         "gross_price":1200,
         "vat":1,
         "uid":1482050150,
         "client_uid":638745398
      }
   }
}
```

## Update Expense object

### Endpoint

`PUT /expenses/{id}`

### Parameters
- `id` (integer, required) - The ID of the Expense object

### Request (application/json)

```json
{
    "categories_id": 4,
    "name": "Office Supplies",
    "invoice_no": "2015/123456",
    "client_uid": 123456789,
    "gross_price": 1200,
    "vat": 1,
    "currency": "EUR",
    "due_date": "2017-01-15"
}
```

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"expenses",
   "data":{
      "id":1482050150,
      "attributes":{
         "categories_id":4,
         "name":"Office Supplies",
         "invoice_no":"2015\/123456",
         "gross_price":1200,
         "vat":1,
         "uid":1482050150,
         "client_uid":638745398
      }
   }
}
```
