## Delete a Shipment

```shell
curl "https://app.omniship.eu/api/shipping/v1/shipments/SHIP0002184"
  -X DELETE
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```
HTTP/1.1 204 No Content
Content-Type:application/json;charset=UTF-8
```

Shipments can only be deleted if there is no label bought.

### HTTP Request

<span class="http-verb delete">DELETE</span> `https://app.omniship.eu/api/shipping/v1/shipments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The Shipment ID of the <span class="object">Shipment</span> to delete
