## Retrieve a Specific Waybill

```shell
curl "https://crossborder.omniship.eu/api/v1/waybills/3265"
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
  "id": 3265,
  "type": "air",
  "number": "784-65428963",
  "reference": 71585,
  "total_weight": 16951,
  "total_bags": 4,
  "status": "created",
  "status_changed": "2021-06-29T14:23:39.000000Z",
  "status_changed_human": "2 minutes ago",
  "inbound": 0,
  "outbound": 0,
  "job_state": "finished",
  "date_received": "2021-06-29T14:23:33.000000Z",
  "updated_at": "2021-06-29T14:23:39.000000Z",
  "customer": "Global Freight System",
  "bags": [
    {
      "id": 2758501,
      "container_id": null,
      "air_waybill_id": 3265,
      "reference": "Z42104029016",
      "total_weight": 9239,
      "status": null,
      "inbound": false,
      "outbound": false,
      "custom": false,
      "customCountry": null,
      "country": "DE",
      "country_name": "Germany",
      "owner": null,
      "updated_at": "2021-06-29T14:23:39.000000Z"
    },
    {
      "id": 2758502,
      "container_id": null,
      "air_waybill_id": 3265,
      "reference": "Z42104029015",
      "total_weight": 2082,
      "status": null,
      "inbound": false,
      "outbound": false,
      "custom": false,
      "customCountry": null,
      "country": "DE",
      "country_name": "Germany",
      "owner": null,
      "updated_at": "2021-06-29T14:23:39.000000Z"
    },
    {
      "id": 2758503,
      "container_id": null,
      "air_waybill_id": 3265,
      "reference": "Z42104027049",
      "total_weight": 5569,
      "status": null,
      "inbound": false,
      "outbound": false,
      "custom": false,
      "customCountry": null,
      "country": "DE",
      "country_name": "Germany",
      "owner": null,
      "updated_at": "2021-06-29T14:23:39.000000Z"
    },
    {
      "id": 2758504,
      "container_id": null,
      "air_waybill_id": 3265,
      "reference": "Z4210402730",
      "total_weight": 61,
      "status": null,
      "inbound": false,
      "outbound": false,
      "custom": false,
      "customCountry": null,
      "country": "DE",
      "country_name": "Germany",
      "owner": null,
      "updated_at": "2021-06-29T14:23:39.000000Z"
    }
  ],
  "in_container": 0,
  "total": 4,
  "container_count": 0,
  "airline": {
    "id": 196,
    "prefix": "784",
    "code": "CZ",
    "name": "China Southern Airlines "
  }
}
```

This endpoint retrieves a specific Waybill.

### HTTP Request

<span class="http-verb get">GET</span> `https://crossborder.omniship.eu/api/v1/waybills/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Waybill
