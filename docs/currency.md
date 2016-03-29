# Currency



## Convert value 

### Endpoint

`GET /currency`

### Query parameters

- `from` (**required**) the currency to convert from (eg. EUR)
- `to` (**required**) currency to convert to (eg. USD)
- `value` (**required**) the amount to convert

### Example

`https://www.billingo.hu/api/currency?from=EUR&to=USD&value=100`

### Response 200 (application/json)

```json
{
  "success": true,
  "data": {
    "value": 111.81166910218
  }
}
```

