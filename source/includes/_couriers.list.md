## List all Couriers


```shell
curl "https://app.shipsmart.eu/api/shipping/v1/couriers"
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
```
```json
{
	"couriers": [
    {
      "courier_name": "FedEx",
      "admin_name": "fedex_international_economy",
      "service_name": "FedEx International Economy",
      "pickup_available": true,
      "transit_from": 2,
      "transit_till": 6,
      "max_weight": 68
    },
    {
      "courier_name": "FedEx",
      "admin_name": "fedex_international_priority",
      "service_name": "FedEx International Priority",
      "pickup_available": true,
      "transit_from": 1,
      "transit_till": 3,
      "max_weight": 68
    },
    {
      "courier_name": "FedEx",
      "admin_name": "fedex_priority_overnight",
      "service_name": "FedEx Priority Overnight",
      "pickup_available": true,
      "transit_from": 1,
      "transit_till": 1,
      "max_weight": 68
    },
    {"..."},
    {"..."}
	]
}
```

### HTTP Request

<span class="http-verb get">GET</span> `https://app.shipsmart.eu/api/shipping/v1/couriers`
