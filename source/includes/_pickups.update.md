## Mark a PickUp as picked_up

```shell
curl "https://app.omniship.eu/api/shipping/v1/pickups/PU0000001"
  -X PATCH
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "picked_up_timestamp": "2021-08-25T14:00"
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
```
```json
{
  "pickup": {
    "pickup_id": "PU0000001",
    "pickup_reference_number": "QNQA287",
    "preferred_min_time": "2021-08-26T13:00:00+00:00",
    "preferred_max_time": "2021-08-26T18:30:00+00:00",
    "pickup_fee": 0,
    "shipments_count": 1,
    "total_weight": 2,
    "status": "picked_up",
    "picked_up_timestamp": "2021-08-25T14:00:00+00:00",
    "address": {
      "company_name": null,
      "contact_name": "Fred Tuijnman",
      "contact_email": "ftuijnman@nicoud.nl",
      "contact_phone": "+31-(0)72 567 1000",
      "line_1": "Newtonstraat 46",
      "line_2": null,
      "postal_code": "1704 SB",
      "city": "Heerhugowaard",
      "state": null,
      "country": "NL",
      "country_full": "Netherlands",
      "eori_number": null,
      "vat_number": null
    }
  }
}
```

This endpoint manually sets the state of PickUp in OMNISHIP to picked_up.

### HTTP Request

<span class="http-verb patch">PATCH</span> `https://app.omniship.eu/api/shipping/v1/shipments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The PickUp ID of the <span class="object">PickUp</span> to mark as picked up

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
picked_up_timestamp | <span class="type">date</span> | Timestamp of the pickup of the shipment(s). Format: <code>yyyy-mm-ddThh:mm</code>.
