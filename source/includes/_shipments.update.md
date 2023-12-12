## Update a Shipment

```shell
curl "https://app.omniship.eu/api/shipping/v1/shipments/SHIP0002184"
  -X PATCH
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "destination_address": {
          "contact_name": "Elliot Alderson"
        },
        "incoterms": "DAP",
        "exclude_rates": false
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
```
```json
{
  "shipment": {
    "created_at": "2021-08-27T13:45:16+00:00",
    "updated_at": "2021-08-27T13:45:38+00:00",
    "id": "SHIP0002184",
    "mode": "test",
    "platform_name": "AMAZON",
    "platform_order_number": "#1234",
    "reference": "shipment reference",
    "incoterms": "DAP",
    "status": "ready_to_process",
    "error_message": null,
    "origin_address": {
      "sender_id": "ecorp",
      "company_name": "E-Corp",
      "contact_name": "Elliot Alderson",
      "contact_email": "ealderson@ecorp.com",
      "contact_phone": "(212) 555-0179",
      "line_1": "Gustav Mahlerplein 53",
      "line_2": null,
      "postal_code": "1082 MA",
      "city": "Amsterdam",
      "state": null,
      "country": "NL",
      "country_full": "Netherlands",
      "eori_number": null,
      "vat_number": null
    },
    "destination_address": {
      "company_name": null,
      "contact_name": "Elliot Alderson",
      "contact_email": "jane@example.eu",
      "contact_phone": "415-1234567",
      "line_1": "417 Melrose Place",
      "line_2": "FLOOR 5",
      "postal_code": "90210",
      "city": "Los Angeles",
      "state": "CA",
      "country": "US",
      "country_full": "United States",
      "eori_number": null,
      "vat_number": null
    },
    "parcels": [
      {
        "id": "11b322a5-5242-4cd3-bd7d-3edc6d2332a0",
        "box_name": "Custom Box",
        "tracking_number": null,
        "length": 24,
        "width": 32,
        "height": 5,
        "dimensions_unit": "cm",
        "weight": 0.5,
        "weight_unit": "kg",
        "quantity": 1,
        "is_custom": true
      }
    ],
    "customs_items": [
      {
        "id": "1b7fca7a-1118-4ce4-baf7-13f85697ef07",
        "sku": null,
        "description": "Shirts",
        "quantity": 2,
        "value": 20,
        "currency": "EUR",
        "weight": 500,
        "weight_unit": "grams",
        "hs_code": "123456789",
        "origin_country": "NL"
      }
    ],
    "rates": [
      {
        "carrier_id": "7605c1fc-683d-4860-a010-8fda26f2a79a",
        "carrier_admin_name": "fedex_international_priority",
        "carrier_display_name": "FedEx International Priority",
        "carrier_description": "A highly reliable, express, time-definite, customs-cleared, door-to-door service for your worldwide packages up to 68kg per unit.",
        "pickup_available": true,
        "min_delivery_time": 1,
        "max_delivery_time": 3,
        "shipment_charge": 22.91,
        "fuel_surcharge": 3.64,
        "currency": "EUR"
      },
      {
        "carrier_id": "56ea6a76-26a8-4d4e-a649-fadff28d1832",
        "carrier_admin_name": "fedex_international_economy",
        "carrier_display_name": "FedEx International Economy",
        "carrier_description": "A cost-saving solution for your less time-sensitive deliveries. A reliable, door-to-door, Customs-cleared, service between Europe, the Middle East and the US.",
        "pickup_available": true,
        "min_delivery_time": 2,
        "max_delivery_time": 6,
        "shipment_charge": 23.07,
        "fuel_surcharge": 3.66,
        "currency": "EUR"
      }
    ],
    "selected_courier": {
      "carrier_id": "7605c1fc-683d-4860-a010-8fda26f2a79a",
      "carrier_admin_name": "fedex_international_priority",
      "carrier_display_name": "FedEx International Priority",
      "carrier_description": "A highly reliable, express, time-definite, customs-cleared, door-to-door service for your worldwide packages up to 68kg per unit.",
      "pickup_available": true,
      "min_delivery_time": 1,
      "max_delivery_time": 3,
      "shipment_charge": 22.91,
      "fuel_surcharge": 3.64,
      "currency": "EUR"
    },
    "label": null,
    "tracking_code": null
  }
}
```

This endpoint updates a new Shipment in OMNISHIP. A <span class="object">shipment</span> can only be updated if a label is not bought.

### HTTP Request

<span class="http-verb patch">PATCH</span> `https://app.omniship.eu/api/shipping/v1/shipments/<ID>`

### URL Parameters

| Parameter | Description                                                           |
|-----------|-----------------------------------------------------------------------|
| ID        | The Shipment ID of the <span class="object">Shipment</span> to update |

### Arguments

| Attribute             | Type                              | Description                                                                                                                                                                                          |
|-----------------------|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| platform_name         | <span class="type">string</span>  | Sales platform name. Maximum: 200 characters                                                                                                                                                         |
| platform_order_number | <span class="type">string</span>  | Order number on the sales platform.                                                                                                                                                                  |
| reference             | <span class="type">string</span>  | Reference information that prints on the shipping label (if courier allows it).                                                                                                                      |
| sender_id             | <span class="type">string</span>  | ID of the sender <span class="object">Address</span> object. The origin address for the shipment is set by this ID. If the sender id is omitted the default sender address is set as origin address. |
| destination_address   | <span class="type">object</span>  | <span class="object">Address</span> object that should be used as receiver address.                                                                                                                  |
| parcels               | <span class="type">array</span>   | Array of <span class="object">Parcel</span> objects with package details for the shipment to be sent.                                                                                                |
| customs_items         | <span class="type">array</span>   | Array of <span class="object">Customs Item</span> objects with details of the products in the shipment for customs.                                                                                  |
| incoterms             | <span class="type">string</span>  | The terms of sale of the Shipment. Valid values are `DDP`, `DDU`, `DAP`.                                                                                                                             |
| courier               | <span class="type">string</span>  | Select a specific courier to create the shipment with.                                                                                                                                               |
| exclude_rates         | <span class="type">boolean</span> | When `true` rates will not be calculated for the shipment, which will lead to a faster response. Value is `false` by default.                                                                        |

### Address Object definitions:

<div class="magic-block-parameters">
	<div class="block-parameters-table">
		<div class="table">
			<div class="tr">
				<div class="th" style="min-width: 120px;">Field Name</div>
				<div class="th">Type</div>
				<div class="th">Description</div>
			</div>
			<div class="tr">
				<div class="td"><p><code>contact_name</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address contact name. Maximum: 35 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>company_name</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address company name. Maximum: 35 characters </p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>contact_email</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address contact email address. Maximum: 50 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>contact_phone</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address contact phone number. Maximum: 18 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>line_1</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address line 1. Maximum: 35 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>line_2</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address line 2. Maximum: 35 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>postal_code</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> Country is postal aware. Address postal code. </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>city</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address city</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>state</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> Country has states. (US, CA, MX, IN)</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>country</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Address country code in Alpha 2 Format  (ISO 3166-1)</p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>eori_number</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>Economic Operators Registration and Identification (EORI) number</p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>vat_number</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p>The consignee's tax identification number</p></div>
			</div>
		</div>
	</div>
</div>

### Parcel definitions:

<div class="magic-block-parameters">
	<div class="block-parameters-table">
		<div class="table">
			<div class="tr">
				<div class="th" style="min-width: 120px;">Field Name</div>
				<div class="th">Type</div>
				<div class="th">Description</div>
			</div>
      <div class="tr">
				<div class="td"><p><code>id</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> updating an existing <span class="object">Parcel</span> object. Id of the object updating.</p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>box</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> adding a new <span class="object">Parcel</span> object to the shipment. 
            Courier or Custom <span class="object">Box</span> slug. Use the Boxes API Resource to retrieve a list of available boxes. </p></div>
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
				<div class="td"><p><span class="required_if">required_when</span> adding a new <span class="object">Parcel</span> object to the shipment. 
          By default the weight will be in kilograms, the weight can be set in grams by setting the <code>weight_unit</code> attribute</p></div>
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
<code> quantity </code> of the Courier <span class="object">Box</span> will be applied. When a custom 
<span class="object"> Box </span> is selected the <code> weight </code> given in the request will be applied.
</aside>

### CustomsItem definitions:

<div class="magic-block-parameters">
	<div class="block-parameters-table">
		<div class="table">
			<div class="tr">
				<div class="th" style="min-width: 120px;">Field Name</div>
				<div class="th">Type</div>
				<div class="th">Description</div>
			</div>
      <div class="tr">
				<div class="td"><p><code>id</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> updating an existing <span class="object">Customs Item</span> object. Id of the object updating.</p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>sku</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> <span class="object">Product</span> sku. Use the Product API Resource to retrieve a list of available products.</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>description</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> adding a new <span class="object">Custom Item</span> object to the shipment and 
            a  sku is not given or null. Description of the item being shipped</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>quantity</code></p></div>
				<div class="td"><p><span>integer</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Quantity of the item to be shipped, must be greater than zero. Defaults to <code>1</code></p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>value</code></p></div>
				<div class="td"><p><span>object</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> adding a new <span class="object">Custom Item</span> object to the shipment and 
            a sku is not given or null. Value of a single item</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>currency</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">Optional</span> The currency of the item value. The account's default currency will be used if not specified</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>weight</code></p></div>
				<div class="td"><p><span>object</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> adding a new <span class="object">Custom Item</span> object to the shipment and 
            a sku is not given or null. The weight of the item</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>hs_code</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">Optional</span> Harmonized Tariff Code</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>origin_country</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required when</span> adding a new <span class="object">Custom Item</span> object to the shipment and 
            a sku is not given or null. Origin country of the item in Alpha 2 format. </p></div>
			</div>
		</div>
	</div>
</div>
