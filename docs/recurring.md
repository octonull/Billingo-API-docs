# Recurring
Recurring profiles

JSON schemas:

- Recurring profile: [https://www.billingo.hu/json/schema/recurring.json](https://www.billingo.hu/json/schema/recurring.json)


## Show my recurring profile(s)

### Endpoint

`GET /recurring`

`GET /recurring/{id}`


### Parameters
- `id` (integer, optional) - If set, only return the given recurring object

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "recurring_profiles",
    "data": [
        {
            "id": 179370222,
            "attributes": {
                "frequency": "2M",
                "due_days": 10,
                "fulfillment_shift": 5,
                "send_invoice": true,
                "max_qty": 2,
                "used_qty": null,
                "comment": "valami",
                "stopped": false,
                "last_recurring_date": null,
                "created_at": "2017-10-26 09:28:14",
                "updated_at": "2017-10-26 11:19:25",
                "start_date": "2017-10-27",
                "uid": 179370222,
                "base_invoice_uid": 1998940267,
                "invoices": [
                    /// list of invoices
                ]
            }
        } ...
    ]
}
```

## Create a new recurring profile

### Endpoint

`POST /recurring`

### Request (application/json)

```json
{
    "base_invoice_uid": 00000000,
    "frequency": "2M",
    "due_days": 10,
    "fulfillment_shift": 5,
    "send_invoice": true,
    "max_qty": 2,
    "comment": "valami",
    "stopped": false,
    "start_date": "2017-10-27"
}
```

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "recurring_profiles",
    "data": {
        "id": 853896719,
        "attributes": {
            "frequency": "2M",
            "due_days": 10,
            "fulfillment_shift": 5,
            "send_invoice": true,
            "max_qty": 2,
            "comment": "valami",
            "stopped": false,
            "start_date": "2017-10-27",
            "updated_at": "2017-10-27 09:15:23",
            "created_at": "2017-10-27 09:15:23",
            "base_invoice_uid": 726237622,
            "invoice": {
                /// invoice object data
            }
        }
    }
}
```

## Update a recurring profile

### Endpoint

`PUT /recurring/{id}`

### Request (application/json)

```json
{
    "base_invoice_uid": 00000000,
    "frequency": "2M",
    "due_days": 10,
    "fulfillment_shift": 5,
    "send_invoice": true,
    "max_qty": 2,
    "comment": "valami",
    "stopped": false,
    "start_date": "2017-10-27"
}
```

### Response 200 (application/json)

```json
{
    "success": true,
    "type": "recurring_profiles",
    "data": {
        "id": 853896719,
        "attributes": {
            "frequency": "2M",
            "due_days": 10,
            "fulfillment_shift": 5,
            "send_invoice": true,
            "max_qty": 2,
            "comment": "valami",
            "stopped": false,
            "start_date": "2017-10-27",
            "updated_at": "2017-10-27 09:15:23",
            "created_at": "2017-10-27 09:15:23",
            "base_invoice_uid": 726237622,
            "invoices": []
        }
    }
}
```

## Pause a recurring profile

### Endpoint

`POST /recurring/{id}/stop`

### Response 200 (application/json)

```json
{
    "success": true,
}
```

## Resume a recurring profile

### Endpoint

`POST /recurring/{id}/resume`

### Response 200 (application/json)

```json
{
    "success": true,
}
```

