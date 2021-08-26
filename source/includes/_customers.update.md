## Update a Customer

```shell
curl "https://crossborder.omniship.eu/api/v1/customers/48"
  -X PATCH
  -H "Authorization: FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "name": "Post Delivery Rotterdam"
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
```
```json
{
  "id": 48,
  "code": "PDA",
  "name": "Post Delivery Rotterdam",
  "weight_unit": "grams",
  "created_at": "2021-06-30T13:54:39+02:00",
  "updated_at": "2021-06-30T14:25:36+02:00"
}
```

This endpoint updates a new Customer in OMNISHIP cross border. This is helpful if you want to change the name, or you want to change the weight unit.

### HTTP Request

<span class="http-verb patch">PATCH</span> `https://crossborder.omniship.eu/api/v1/customers/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Customer to update

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
code | <span class="type">string</span> | Unique code to identify a customer. Must be unique in the database.
name | <span class="type">string</span> | Name of the customer.
weight_unit | <span class="type">string</span> | The default weight unit used for the weights in the pre-alert uploads. Valid values are `grams`, `kilograms`.
