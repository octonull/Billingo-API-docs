# VAT
VAT object representation

## Return a list of available VAT codes

### Endpoint

`GET /vat`

### Response 200 (application/json)

```json
{
   "success":true,
   "type":"vat",
   "data":[
      {
         "id":"1",
         "attributes":{
            "id":"1",
            "value":"0.27",
            "description":"27%"
         }
      },
      {
         "id":"2",
         "attributes":{
            "id":"2",
            "value":"0.05",
            "description":"5%"
         }
      },
      {
         "id":"3",
         "attributes":{
            "id":"3",
            "value":"0.18",
            "description":"18%"
         }
      },
      {
         "id":"4",
         "attributes":{
            "id":"4",
            "value":"0",
            "description":"AM"
         }
      },
      {
         "id":"5",
         "attributes":{
            "id":"5",
            "value":"0",
            "description":"EU"
         }
      }
   ]
}
```
