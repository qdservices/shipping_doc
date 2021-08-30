## List all Boxes


```shell
curl "https://app.omniship.eu/api/shipping/v1/boxes"
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
	"boxes": [
    {
      "courier_name": null,
      "name": "test",
      "slug": "test",
      "length": 10,
      "width": 10,
      "height": 10,
      "weight": 0,
      "max_weight": null,
      "is_custom": true
    },
    {
      "courier_name": "FedEx",
      "name": "FedEx Tube",
      "slug": "fedex-tube",
      "length": 97,
      "width": 15,
      "height": 15,
      "weight": 9,
      "max_weight": null,
      "is_custom": false
    },
    {
      "courier_name": "FedEx",
      "name": "FedEx Envelope",
      "slug": "fedex-envelope",
      "length": 24,
      "width": 32,
      "height": 1,
      "weight": 0.5,
      "max_weight": 500,
      "is_custom": false
    },
    {"..."},
    {"..."}
	]
}
```

### HTTP Request

<span class="http-verb get">GET</span> `https://app.omniship.eu/api/shipping/v1/boxes`
