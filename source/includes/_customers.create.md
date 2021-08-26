## Create a Customer

```shell
curl "https://crossborder.omniship.eu/api/v1/customers"
  -X POST
  -H "Authorization: FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "code": "ADS",
        "name": "Amsterdam Delivery Service",
        "weight_unit": "grams"
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 201 Created
Content-Type:application/json;charset=UTF-8
```

```json
{
  "id": 50,
  "code": "ADS",
  "name": "Amsterdam Delivery Service",
  "weight_unit": "grams",
  "created_at": "2021-06-30T14:03:18+02:00",
  "updated_at": "2021-06-30T14:03:18+02:00"
}
```

This endpoint creates a new Customer in OMNISHIP cross border. 

### HTTP Request

<span class="http-verb post">POST</span> `https://crossborder.omniship.eu/api/v1/waybills`

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
code | <span class="type">string</span> | <span class="required">required</span> The unique customer code. This code must be unique. Usually a three letter abbreviation of the customer name.
name | <span class="type">string</span> | <span class="required">required</span> The name of the customer.
weight_unit | <span class="type">string</span> | <span class="required">required</span> The default weight unit used for the weights in the Waybill pre-alert uploads. Valid values are `grams`, `kilograms`.
