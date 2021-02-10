# Products

Products object representation.

JSON Schema: [https://www.billingo.hu/json/schema/product.json](https://www.billingo.hu/json/schema/product.json)

## List of products

### Endpoint

`GET /products?page=1&max_per_page=20`

`GET /products/{id}`

### Parameters
- `id` (integer, optional) - If set, only return the given client object
- `page` (integer, optional, default=1) - If set, return the given page
- `max_per_page` (integer, optional, default=20) - Sets the maximum number of results to return. Absolute maximum is 50!

### Response 200 (application/json)


```json
{
  "success": true,
  "type": "products",
  "data": [
    {
      "id": 443677079,
      "attributes": {
        "name": "Test Product",
        "comment": "",
        "price": 7874,
        "unit": "db",
        "vat_id": 1,
        "currency_code": "HUF",
        "deleted": 0,
        "categories_id": 0,
        "parent_product_id": 0,
        "min_qty": 0,
        "max_qty": 0,
        "opt_qty": 0,
        "sales_price": 0,
        "is_service": 0,
        "barcode": "",
        "product_code": "",
        "item_nr": "",
        "width": 0,
        "height": 0,
        "depth": 0,
        "weight": 0,
        "deleted_at": null,
        "archived_at": "0000-00-00 00:00:00",
        "created_at": "-0001-11-30 00:00:00",
        "updated_at": "-0001-11-30 00:00:00",
        "description": "27%",
        "master_variation_id": 0,
        "purchase_price": 0,
        "fokonyv_arbev": "",
        "fokonyv_afa": "",
        "vat": {
          "id": 1,
          "value": 0.27,
          "description": "27%"
        },
        "entitlement": null
      }
    }
  ]
}
```

## Create product

### Endpoint

`POST /products`


### Request (application/json)


```json

{
    "name": "API teszt termék",
    "price": 5200,
    "unit": "db",
    "currency_code": "HUF",
    "vat_id": 1,
    "fokonyv_arbev": 0,
    "fokonyv_afa": 0,
    "entitlement": ""
}
```


### Response 200 (application/json)


```json
{
  "success": true,
  "type": "products",
  "data": {
    "id": 1206264827,
    "attributes": {
      "name": "API teszt termék",
      "price": 5200,
      "unit": "db",
      "currency_code": "HUF",
      "vat_id": 1,
      "fokonyv_arbev": "",
      "fokonyv_afa": "",
      "updated_at": "2017-10-04 15:26:26",
      "created_at": "2017-10-04 15:26:26",
      "entitlement": null
    }
  }
}
```

## Update product

### Endpoint

`PUT /products/{id}`

### Request (application/json)

```json
{
    "name": "API teszt termék - EDIT",
    "price": 5200,
    "unit": "db",
    "currency_code": "HUF",
    "vat_id": 1
}
```

### Response 200 (application/json)

```json
{
  "success": true,
  "type": "products",
  "data": {
    "id": 1206264827,
    "attributes": {
      "name": "API teszt termék - EDIT",
      "comment": null,
      "price": 5200,
      "unit": "db",
      "vat_id": 1,
      "currency_code": "HUF",
      "deleted": 0,
      "categories_id": 0,
      "parent_product_id": 0,
      "min_qty": 0,
      "max_qty": 0,
      "opt_qty": 0,
      "is_service": 0,
      "barcode": "",
      "product_code": "",
      "item_nr": "",
      "width": 0,
      "height": 0,
      "depth": 0,
      "weight": 0,
      "deleted_at": null,
      "archived_at": "0000-00-00 00:00:00",
      "created_at": "2017-10-04 15:26:26",
      "updated_at": "2017-10-04 15:26:37",
      "description": "27%",
      "master_variation_id": 0,
      "fokonyv_arbev": "",
      "fokonyv_afa": "",
      "vat": {
        "id": 1,
        "value": 0.27,
        "description": "27%"
      },
      "entitlement": null
    }
  }
}
```


## Delete product

### Endpoint

`DELETE /api/products/{id}`


### Response 200 (application/json)

```json
{"success":true}
```
