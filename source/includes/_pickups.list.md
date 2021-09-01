## List all PickUps


```shell
curl "https://app.shipsmart.eu/api/shipping/v1/pickups"
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
	"pickups": [
    {
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
    },
    {"..."},
    {"..."}
	]
}
```

This endpoint retrieves all PickUps.

### HTTP Request

<span class="http-verb get">GET</span> `https://app.shipsmart.eu/api/shipping/v1/shipments`

Query params | Type | Description
--------- | ------- | -----------
pickup_id | <span class="type">string</span> | PickUp ID provided when creating the pickup. If multiple, separate with a comma.
pickup_reference_number | <span class="type">string</span> | Reference number of the pickup
status | <span class="type">string</span> | Search by current status of the pickup. valid options\: <code>pending</code>, <code>picked_up</code>, <code>canceled</code>
page | <span class="type">integer</span> | Which page number want to fetch, default: <code>1</code>
per_page | <span class="type">integer</span> | Number of Shipments per page to fetch, default: <code>25</code>, max: <code>100</code>



