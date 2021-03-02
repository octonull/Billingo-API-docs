# VAT
VAT object representation

## Return a list of available VAT codes

### Endpoint

`GET /vat`

### Query parameters

- `v` (*optional*) The value to filter for (eg. 0.27)
- `d` (*optional*) The description to filter for (eg. AM)

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
            "description":"27%",
            "info_text": ""
         }
      },
      {
         "id":"2",
         "attributes":{
            "id":"2",
            "value":"0.05",
            "description":"5%",
            "info_text":  null
         }
      },
      {
         "id":"3",
         "attributes":{
            "id":"3",
            "value":"0.18",
            "description":"18%",
            "info_text":  null
         }
      },
      {
         "id":"4",
         "attributes":{
            "id":"4",
            "value":"0",
            "description":"AM",
            "info_text":  "adómentes"
         }
      },
      {
         "id":"5",
         "attributes":{
            "id":"5",
            "value":"0",
            "description":"EU",
            "info_text":  "EU-n belül"
         }
      }
   ]
}
```


## Get EU VAT code

EU based companies whom sell services to EU countries need to apply the buyer country's VAT to the full price.

### Endpoint

`GET /vat/eu`

### Query parameters

- `country` (**required**) the ISO3166 country code given by the user (eg. DE)
- `ip` (**required**) the IP address of the user
- `business_country` (**required**) the ISO3166 country code for the operating business
- `vat_code` (*optional*) the EU VAT code for the user (eg. DE13816200)

### Response 200 (application/json)

```json
{
  "success": true,
  "data": {
    "set_country": "DE",
    "ip_country": "HU",
    "country_match": false,
    "company": null,
    "tax_rate": 0.19,
    "billingo_vat": {
      "id": 13,
      "value": "0.19",
      "description": "19.0% - DE"
    }
  }
}
```

- `ip_country` the country code from the given IP
- `country_match` boolean value, true if the given country code and the IP country matches
- `company` returns company data from the EU registry or null if `vat_code` is not set
- `tax_rate` the tax rate for the set country
- `billingo_vat` will return a Billingo vat object that can be used to save an invoice


