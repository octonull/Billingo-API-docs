# Invoice Query

### Endpoint

`GET /invoices/query?start_date=2017-02-01&page=1&max_per_page=20`

### Parameters

- `page` (integer, optional, default=1) - If set, return the given page
- `max_per_page` (integer, optional, default=20) - Sets the maximum number of results to return. Absolute maximum is 50!
- `start_date` (date, optional, default=first day of month)
- `end_date` (date, optional, default=current date)
- `num_start` (integer, optional) - Starting number of the invoice, should not contain year or any other formatting
- `num_end` (integer, optional) - Ending number of the invoice, should not contain year or any other formatting
- `year_start` (integer, optional) - Year for `num_start` parameter
- `year_end` (integer, optional) - Year for the `num_end` parameter
- `payment_method` (integer, optional) - The payment method ID (same ID as used when creating invoices)
- `block` (integer, optional) - The block ID (same ID as used when creating invoices)

### Invoice number query example

When querying for invoice numbers you must set `year_start` and `num_start` and/or `year_end` and `num_end` parameters together. 

When looking for invoices numbered 2017-000010 to 2017-000020 you must set the query like:

`year_start=2017&num_start=10&year_end=2017&num_end=20`

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
            "block_uid":0,
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
            },
           "payment_method": {
             "id": 2,
             "lang_code": "hu",
             "name": "Átutalás",
             "advance_paid": "0"
        	}
         }
      }
   ]
}
```

