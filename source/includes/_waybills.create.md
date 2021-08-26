## Create a Waybill

```shell
curl "https://crossborder.omniship.eu/api/v1/waybills"
  -X POST
  -H "Authorization: FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "customer_code": "GFS",
        "waybill_type": "air",
        "waybill_number": "784-65428952",
        "reference": 71577,
        "weight_unit": "grams",
        "pre_alert_rows": [
            {
                "order_number": "GSHML800Y0007SD",
                "package_barcode": "01505272372693",
                "bag_grade": "Z42104029016",
                "shipping_method": "DE DPD",
                "weight": "551.00",
                "company_name": null,
                "consignee_name": null,
                "phone_number": null,
                "email_address": null,
                "street": null,
                "house_number": null,
                "house_number_extension": null,
                "additional_address_info": null,
                "city_or_town": "Stödtlen",
                "state_or_province": null,
                "zip_code": "73495",
                "country_code": "DE",
                "sku_code": null,
                "sku_description": null,
                "quantity": 0,
                "currency": null,
                "price": null,
                "shipping_costs": null,
                "hs_code": null,
                "website": null
            },
            {"..."},
            {"..."}
        ],
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 200 Created
Content-Type:application/json;charset=UTF-8
```

```json
{
  "id": 3263,
  "number": "784-65428961",
  "reference": 71583,
  "total_weight": null,
  "total_bags": null,
  "status": "pre_upload",
  "status_changed": "2021-06-29T11:41:18.000000Z",
  "status_changed_human": "1 second ago",
  "inbound": 0,
  "outbound": 0,
  "job_state": "uploading",
  "date_received": "2021-06-29T11:41:18.000000Z",
  "updated_at": "2021-06-29T11:41:18.000000Z",
  "customer": "Global Freight System",
  "bags": [],
  "in_container": 0,
  "total": 1,
  "container_count": 0,
  "airline": {
    "id": 196,
    "prefix": "784",
    "code": "CZ",
    "name": "China Southern Airlines "
  }
}
```

This endpoint creates a new Waybill pre alert in OMNISHIP cross border. 

### HTTP Request

<span class="http-verb post">POST</span> `https://crossborder.omniship.eu/api/v1/waybills`

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
customer_code | <span class="type">string</span> | <span class="required">required</span> The unique customer code. This code should reflect a customer code in the database.
waybill_type | <span class="type">string</span> | <span class="required">required</span> The type of waybill. Valid values are `air`, `road`, `train`, `other`
waybill_number | <span class="type">string</span> | <span class="required">required</span> Unique number of the waybill. This number cannot already exist in the database for the same customer.
reference | <span class="type">string</span> | <span class="required">required</span> Unique reference usually the ID of the external system where shipment is uploaded from.
weight_unit | <span class="type">string</span> | <span class="optional">optional</span> The weight unit used for the weights in the pre-alert. Valid values are `grams`, `kilograms`. When omitted or empty the default customer weight unit will be used.
pre_alert_rows | <span class="type">array</span> | <span class="required">required</span> Line with details of the specific shipment. Each line must contain `order_number`, `bag_grade`, `country_code`.

### Pre Alert Row Parameters

Attribute | Type | Description
--------- | ------- | ---------
`order_number` | <span class="type">string</span> | <span class="required">required</span> Order number for the shipment line.
`package_barcode` | <span class="type">string</span> | <span class="optional">optional</span> Barcode of the package. Usually the final mile carrier barcode.
`bag_grade` | <span class="type">string</span> | <span class="requried">required</span> Barcode of the bag/box containing the packages.
`shipping_method` | <span class="type">string</span> | <span class="optional">optional</span> Method of shipping. Can be used as an identifier of the implementation hub.
`weight` | <span class="type">number</span> | <span class="required">required</span> Weight of the package described on the shipping line. The weight will be reflected using the weight_unit given.
`company_name` | <span class="type">string</span> | <span class="optional">optional</span> Name of the company of the package consignee.
`consignee_name` | <span class="type">string</span> | <span class="optional">optional</span> Name of the of the package consignee.
`phone_number` | <span class="type">string</span> | <span class="optional">optional</span> Phone number of the of the package consignee.
`email_address` | <span class="type">string</span> | <span class="optional">optional</span> Email address of the of the package consignee.
`street` | <span class="type">string</span> | <span class="optional">optional</span> Street address of the of the package consignee.
`house_number` | <span class="type">number</span> | <span class="optional">optional</span> House number of the of the package consignee.
`house_number_extension` | <span class="type">string</span> | <span class="optional">optional</span> House number extension of the of the package consignee.
`additional_address_info` | <span class="type">string</span> | <span class="optional">optional</span> Additional address info i.e. `Apt 10`.
`city_or_town` | <span class="type">string</span> | <span class="optional">optional</span> City or town of the of the package consignee.
`state_or_province` | <span class="type">string</span> | <span class="optional">optional</span> State or province of the of the package consignee.
`zip_code` | <span class="type">string</span> | <span class="optional">optional</span> Zip code of the of the package consignee.
`country_code` | <span class="type">string</span> | <span class="required">required</span> Country code of the of the package consignee. (needs to be ISO 3166 2-char code)
`sku_code` | <span class="type">string</span> | <span class="optional">optional</span> SKU code of the of the item(s) in the package.
`sku_description` | <span class="type">string</span> | <span class="optional">optional</span> Description of the of the item(s) in the package.
`quantity` | <span class="type">number</span> | <span class="optional">optional</span> Quantity items in the package.
`currency` | <span class="type">string</span> | <span class="optional">optional</span> Currency of the value of the item in the package.
`price` | <span class="type">number</span> | <span class="optional">optional</span> Value of the item in the package.
`shipping_costs` | <span class="type">number</span> | <span class="optional">optional</span> Shipping costs of the package.
`hs_code` | <span class="type">string</span> | <span class="optional">optional</span> HS tariff code for customs.
`website` | <span class="type">url</span> | <span class="optional">optional</span> URL of the details page of the specified item.

