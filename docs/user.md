# User

## Get sandbox mode is enabled

### Endpoint

`GET /user/is-sandbox`

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "user",
    "data": {
        "is_sandbox": true
    }
}
```

## Get VAT number

### Endpoint

`GET /user/vat-number`

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "user",
    "data": {
        "vat-number": "12345678-2-10"
    }
}
```
