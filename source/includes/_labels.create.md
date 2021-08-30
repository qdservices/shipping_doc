## Confirm and buy Labels

```shell
curl "https://app.omniship.eu/api/shipping/v1/labels"
  -X POST
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "shipments": [
          {
            "shipment_id": "SHIP0002167"
          }
        ]
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 201 Created
Content-Type:application/json;charset=UTF-8
```

```json
{
  "labels": {
    "message": "Your labels are being generated",
    "total_costs": 12.26,
    "labels": [
      {
        "shipment_id": "SHIP0002167",
        "platform_order_number": "#1234",
        "status": "processing",
        "label_url": null,
        "tracking_number": null
      }
    ]
  }
}
```

### HTTP Request

<span class="http-verb post">POST</span> `https://app.omniship.eu/api/shipping/v1/rates`

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
shipments | <span class="type">array</span> | <span class="required">required</span> Array of shipment id's where labels should be created for.
courier | <span class="type">string</span> | <span class="optional">optional</span> Courier for which the label should be retrieved.
