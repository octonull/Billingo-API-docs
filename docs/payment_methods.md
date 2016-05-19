# Payment Methods

Payment methods representation.

### Notes

Payment methods are currently read only, so only `GET` request is allowed!


## List the available payment methods

### Endpoint
`GET /payment_methods/{langcode}`


### Parameters

- `langcode` (string, required) - Can be any of hu, en, or de

### Response 200 (application/json)
```json
{
   "success":true,
   "type":"payment_methods",
   "data":[
      {
         "id":"2",
         "attributes":{
            "id":"2",
            "lang_code":"en",
            "name":"Wiretransfer",
            "advance_paid":"0"
         }
      },
      {
         "id":"4",
         "attributes":{
            "id":"4",
            "lang_code":"en",
            "name":"Cash on Delivery",
            "advance_paid":"0"
         }
      },
      {
         "id":"1",
         "attributes":{
            "id":"1",
            "lang_code":"en",
            "name":"Cash",
            "advance_paid":"1"
         }
      },
      {
         "id":"5",
         "attributes":{
            "id":"5",
            "lang_code":"en",
            "name":"Bankcard",
            "advance_paid":"1"
         }
      },
      {
         "id":"6",
         "attributes":{
            "id":"6",
            "lang_code":"en",
            "name":"SZEP card",
            "advance_paid":"0"
         }
      },
      {
         "id":"7",
         "attributes":{
            "id":"7",
            "lang_code":"en",
            "name":"PayPal",
            "advance_paid":"0"
         }
      },
      {
         "id":"8",
         "attributes":{
            "id":"8",
            "lang_code":"en",
            "name":"Postal check",
            "advance_paid":"0"
         }
      },
      {
         "id":"9",
         "attributes":{
            "id":"9",
            "lang_code":"en",
            "name":"Compensation",
            "advance_paid":"1"
         }
      },
      {
         "id":"10",
         "attributes":{
            "id":"10",
            "lang_code":"en",
            "name":"Health insurance card",
            "advance_paid":"0"
         }
      },
      {
         "id":"11",
         "attributes":{
            "id":"11",
            "lang_code":"en",
            "name":"Coupon",
            "advance_paid":"1"
         }
      },
      {
         "id":"12",
         "attributes":{
            "id":"12",
            "lang_code":"en",
            "name":"Voucher",
            "advance_paid":"1"
         }
      }
   ]
}
```
