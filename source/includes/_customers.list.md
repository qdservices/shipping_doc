## List all Customers


```shell
curl "https://crossborder.omniship.eu/api/v1/customers"
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
	"data": [
    {
      "id": 1,
      "code": "YDH",
      "name": "YDH Express",
      "weight_unit": "grams",
      "created_at": "2020-05-26T18:51:14+02:00",
      "updated_at": "2020-08-04T13:38:44+02:00"
    },
    {
      "id": 2,
      "code": "YAN",
      "name": "Yanwen (B2C Europe)",
      "weight_unit": "grams",
      "created_at": "2020-05-26T23:21:48+02:00",
      "updated_at": "2020-05-28T10:41:17+02:00"
    },
    {
      "id": 3,
      "code": "GTS",
      "name": "GTS",
      "weight_unit": "grams",
      "created_at": "2020-05-26T23:32:57+02:00",
      "updated_at": "2020-05-26T23:32:57+02:00"
    },
    {"..."},
    {"..."}
	]
}
```

This endpoint retrieves all Customers.

### HTTP Request

<span class="http-verb get">GET</span> `https://crossborder.omniship.eu/api/v1/customers`

