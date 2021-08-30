## Request Rates

```shell
curl "https://app.omniship.eu/api/shipping/v1/rates"
  -X POST
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "origin_address": {
          "postal_code": "1091 KP",
          "city": "Amsterdam",
          "country": "NL"
        },
        "destination_address": {
          "postal_code": "1000",
          "city": "Bruxelles",
          "country": "BE"
        },
        "parcels": [
          {
            "box": "test",
            "quantity": 3,
            "weight": 2.5,
            "weight_unit": "kilograms"
          }
        ],
        "incoterms": "DDU",
        "apply_shipping_rules": true
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 201 Created
Content-Type:application/json;charset=UTF-8
```

```json
{
  "rates": [
    {
      "carrier_id": "56ea6a76-26a8-4d4e-a649-fadff28d1832",
      "carrier_admin_name": "fedex_international_economy",
      "carrier_display_name": "FedEx International Economy",
      "carrier_description": "A cost-saving solution for your less time-sensitive deliveries. A reliable, door-to-door, Customs-cleared, service between Europe, the Middle East and the US.",
      "pickup_available": true,
      "min_delivery_time": 2,
      "max_delivery_time": 6,
      "shipment_charge": 10.84,
      "fuel_surcharge": 2.66,
      "currency": "EUR"
    },
    {
      "carrier_id": "7605c1fc-683d-4860-a010-8fda26f2a79a",
      "carrier_admin_name": "fedex_international_priority",
      "carrier_display_name": "FedEx International Priority",
      "carrier_description": "A highly reliable, express, time-definite, customs-cleared, door-to-door service for your worldwide packages up to 68kg per unit.",
      "pickup_available": true,
      "min_delivery_time": 1,
      "max_delivery_time": 3,
      "shipment_charge": 23.21,
      "fuel_surcharge": 4.2,
      "currency": "EUR"
    }
  ]
}
```

### HTTP Request

<span class="http-verb post">POST</span> `https://app.omniship.eu/api/shipping/v1/rates`

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
sender_id | <span class="type">string</span> | <span class="optional">optional</span> ID of the sender <span class="object">Address</span> object. The origin address for the shipment is set by this ID. If the sender id is omitted the <code>origin_address</code> attribute is required.
origin_address | <span class="type">object</span> | <span class="required_if">required if</span> the <code>sender_id</code> is not given. Address object that should be used as the origin address.
destination_address | <span class="type">object</span> | <span class="required">required</span> <span class="object">Address</span> object that should be used as receiver address.
parcels | <span class="type">array</span> | <span class="required">required</span> Array of <span class="object">Parcel</span> objects with package details for the shipment to be sent.
incoterms | <span class="type">string</span> | <span class="optional">optional</span> The terms of sale of the Shipment. Valid values are `DDP`, `DDU`, `DAP`.
apply_shipping_rules | <span class="type">boolean</span> | <span class="optional">optional</span> Lets the algorithm apply the shipping rules created in the <a href="https://app.omniship.eu/settings?tab=rules" target="_blank">OMNISHIP portal</a>, for instance to exclude couriers. By default the value is `true`.

### <span class="object">Address</span> Object definitions:

<div class="magic-block-parameters">
	<div class="block-parameters-table">
		<div class="table">
			<div class="tr">
				<div class="th" style="min-width: 120px;">Field Name</div>
				<div class="th">Type</div>
				<div class="th">Description</div>
			</div>
			<div class="tr">
				<div class="td"><p><code>postal_code</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> Country is postal aware. Address postal code. </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>city</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required">required</span> Address city</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>state</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> Country has states. (US, CA, MX, IN)</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>country</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required">required</span> Address country code in Alpha 2 Format  (ISO 3166-1)</p></div>
			</div>
		</div>
	</div>
</div>

### <span class="object">Parcel</span> definitions:

<div class="magic-block-parameters">
	<div class="block-parameters-table">
		<div class="table">
			<div class="tr">
				<div class="th" style="min-width: 120px;">Field Name</div>
				<div class="th">Type</div>
				<div class="th">Description</div>
			</div>
      <div class="tr">
				<div class="td"><p><code>box</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Courier or Custom <span class="object">Box</span> <code>slug</code>. Use the <a href="#boxes">Boxes API</a> Resource to retrieve a list of available boxes. </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>length</code></p></div>
				<div class="td"><p><span>integer</span></p></div>
				<div class="td"><p><span class="optional">optional</span> The length of the parcel in cm </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>width</code></p></div>
				<div class="td"><p><span>integer</span></p></div>
				<div class="td"><p><span class="optional">optional</span> The width of the parcel in cm</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>height</code></p></div>
				<div class="td"><p><span>integer</span></p></div>
				<div class="td"><p><span class="optional">optional</span> The height of the parcel in cm</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>weight</code></p></div>
				<div class="td"><p><span>float</span></p></div>
				<div class="td"><p><span class="required">required</span> The weight of the parcel. By default the weight will be in kilograms, the weight can be set in grams by setting the <code>weight_unit</code> attribute</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>weight_unit</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">Optional</span> The unit in which the weight is measured. Valid values are: <code>kilograms</code>, <code>grams</code>. Default is <code>kilograms</code></p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>quantity</code></p></div>
				<div class="td"><p><span>integer</span></p></div>
				<div class="td"><p><span class="optional">optional</span> The quantity of parcels with the same measures. Default is <code>1</code></p></div>
			</div>
		</div>
	</div>
</div>

<aside class="notice">
When a courier <span class="object"> Box </span> is selected the <code> weight </code>, <code> dimensions </code> and 
<code> quantity </code> of the Courier <span class="object"> Box </span> will be applied. When a custom 
<span class="object"> Box </span> is selected the <code> weight </code> given in the request will be applied.
</aside>
