## Cancel a Pickup

```shell
curl "https://app.shipsmart.eu/api/shipping/v1/pickups/PU0000001"
  -X DELETE
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```
HTTP/1.1 204 No Content
Content-Type:application/json;charset=UTF-8
```

### HTTP Request

<span class="http-verb delete">DELETE</span> `https://app.shipsmart.eu/api/shipping/v1/pickups/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The Pickup ID of the <span class="object">PickUp</span> to cancel
