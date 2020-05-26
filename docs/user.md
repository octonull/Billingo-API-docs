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

`GET /user/tax-code`

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "user",
    "data": {
        "tax_code": "12345678-2-10"
    }
}
```
