# Bank accounts

Bank accounts object representation.

JSON Schema: [https://www.billingo.hu/json/schema/bank_account.json](https://www.billingo.hu/json/schema/bank_account.json)

## List bank accounts

### Endpoint

`GET /bank_accounts/{id}`


### Parameters
- `id` (integer, optional) - If set, only return the given bank account object

### Response 200 (application/json)
```json
{
   "success":true,
   "type":"bank_accounts",
   "data":[
      {
         "id":1263576876,
         "attributes":{
            "bank_name":"xxxxx",
            "account_no":"1212121212",
            "account_no_iban":"",
            "account_swift":"",
            "currency":"HUF",
            "uid":1263576876
         }
      },
      {
         "id":1938103373,
         "attributes":{
            "bank_name":"xxxxx",
            "account_no":"11111",
            "account_no_iban":"",
            "account_swift":"",
            "currency":"HUF",
            "uid":1938103373
         }
      },
      {
         "id":36596367,
         "attributes":{
            "bank_name":"Valami",
            "account_no":"1111-1111-1111",
            "account_no_iban":"",
            "account_swift":"",
            "currency":"HUF",
            "uid":36596367
         }
      }
   ]
}
```

## Create Bank Account object

### Endpoint


`POST /bank_accounts`

### Request (application/json)    
```json
{
    "bank_name": "Test Bank LLC.",
    "account_no": "397794553330472",
    "account_no_iban": "HU33107930243977945533304723",
    "account_swift": "TSTBNK",
    "currency": "EUR"
}
```


### Response 200 (application/json)

```json
{
   "success":true,
   "type":"bank_accounts",
   "data":{
      "id":1804116401,
      "attributes":{
         "bank_name":"Test Bank LLC.",
         "account_no":"397794553330472",
         "account_no_iban":"HU33107930243977945533304723",
         "account_swift":"TSTBNK",
         "currency":"EUR",
         "uid":1804116401
      }
   }
}
```

## Update Bank Accounts object

### Endpoint
`PUT /bank_accounts/{id}`

### Parameters
- `id` (integer, optional) - The BankAccount object to update

### Request (application/json)

```json
{
    "bank_name": "Test Bank LLC.",
    "account_no": "397794553330472",
    "account_no_iban": "HU33107930243977945533304723",
    "account_swift": "TSTBNK",
    "currency": "USD"
}
```

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"bank_accounts",
   "data":{
      "id":1804116401,
      "attributes":{
         "bank_name":"Test Bank LLC.",
         "account_no":"397794553330472",
         "account_no_iban":"HU33107930243977945533304723",
         "account_swift":"TSTBNK",
         "currency":"USD",
         "uid":1804116401
      }
   }
}
```
