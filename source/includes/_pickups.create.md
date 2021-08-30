## Request a Pickup

```shell
curl "https://app.omniship.eu/api/shipping/v1/pickups"
  -X POST
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "courier": "fedex_international_priority",
        "preferred_date": "2021-08-26",
        "preferred_max_time": "18:30",
        "preferred_min_time": "13:00",
        "shipment_ids": [
          "SHIP0002166"
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
  "courier_name": "FedEx",
  "shipments": [
    [
      "SHIP0002166"
    ]
  ],
  "pickup": {
    "pickup_id": "PU0000001",
    "pickup_reference_number": "QNQA287",
    "preferred_min_time": "2021-08-26T13:00:00+00:00",
    "preferred_max_time": "2021-08-26T18:30:00+00:00",
    "pickup_fee": 0,
    "shipments_count": 1,
    "total_weight": 2,
    "status": "pending",
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

### HTTP Request

<span class="http-verb post">POST</span> `https://app.omniship.eu/api/shipping/v1/pickups`

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
courier_name | <span class="type">string</span> | <span class="required">required</span> Courier admin name. Use the Courier API to retrieve a list of available couriers.
preferred_date | <span class="type">date</span> | <span class="optional">optional</span> Date when the shipment(s) should be picked up. By default the current date is selected. Format: <code>yyyy-mm-dd</code>
preferred_max_time | <span class="type">time</span> | <span class="required">required</span> Latest pickup time. Format: <code>hh:mm</code>.
preferred_min_time | <span class="type">time</span> | <span class="required">required</span> Preferred time when shipment(s) ready for pickup. Format: <code>hh:mm</code>. 
shipment_ids | <span class="type">array</span> | <span class="required">required</span> Array of shipment_ids for which the pickup is requested.
