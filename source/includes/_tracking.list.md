## List all Trackings


```shell
curl "https://app.omniship.eu/api/shipping/v1/tracking"
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
  "trackers": [
    {
      "updated_at": "2022-08-03T12:41:22.000000Z",
      "shipment_id": "SHIP0116354",
      "platform_order_number": "SHIP0116354",
      "tracking_code": "3SKABE076200888",
      "status": "delivered",
      "latest_event": "Shipment delivered,2022-08-03 12:51:40",
      "tracking_url": "https:\/\/www.internationalparceltracking.com\/Main.aspx#\/track\/3SKABE076200888\/NL\/5652 AG",
      "tracking_details": [
        {
          "checkpoint_date": "2022-08-03 12:51:40",
          "tracking_detail": "Shipment delivered",
          "location": null,
          "status": "delivered",
          "sub_status": "delivered001"
        },
        {
          "checkpoint_date": "2022-08-03 10:14:41",
          "tracking_detail": "Driver is en route",
          "location": null,
          "status": "in transit",
          "sub_status": "transit001"
        },
        {
          "checkpoint_date": "2022-08-03 10:00:26",
          "tracking_detail": "Shipment has been sorted",
          "location": null,
          "status": "in transit",
          "sub_status": "transit001"
        },
        {
          "checkpoint_date": "2022-08-03 00:47:56",
          "tracking_detail": "Shipment received by PostNL",
          "location": null,
          "status": "in transit",
          "sub_status": "transit001"
        },
        {
          "checkpoint_date": "2022-08-02 22:18:30",
          "tracking_detail": "Shipment expected, but not yet arrived at PostNL",
          "location": null,
          "status": "in transit",
          "sub_status": "transit001"
        }
      ]
    },
    {},
    {}
  ]
}
```

This endpoint retrieves all Trackers.

### HTTP Request

<span class="http-verb get">GET</span> `https://app.omniship.eu/api/shipping/v1/tracker`

| Query params          | Type                              | Description                                                                            |
|-----------------------|-----------------------------------|----------------------------------------------------------------------------------------|
| shipment_id           | <span class="type">string</span>  | Shipment ID provided when creating the shipment. If multiple, separate with a comma.   |
| platform_order_number | <span class="type">string</span>  | Order number of the sales platform                                                     |
| created_at_from       | <span class="type">date</span>    | Search for trackers created since this date                                            |
| created_at_till       | <span class="type">date</span>    | Search for trackers created since this date                                            |
| page                  | <span class="type">integer</span> | Which page number want to fetch, default: <code>1</code>                               |
| per_page              | <span class="type">integer</span> | Number of Shipments per page to fetch, default: <code>25</code>, max: <code>100</code> |
