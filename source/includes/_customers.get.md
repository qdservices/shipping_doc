## Retrieve a Specific Customer

```shell
curl "https://crossborder.omniship.eu/api/v1/customers/48"
  -H "Authorization: FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
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
  "name": "Post Delivery Amsterdam",
  "weight_unit": "grams",
  "created_at": "2021-06-30T13:54:39+02:00",
  "updated_at": "2021-06-30T13:57:39+02:00"
}
```

This endpoint retrieves a specific Customer.

### HTTP Request

<span class="http-verb get">GET</span> `https://crossborder.omniship.eu/api/v1/customers/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Customer
