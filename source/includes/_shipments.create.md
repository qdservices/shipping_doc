## Create a Shipment

```shell
curl "https://app.shipsmart.eu/api/shipping/v1/shipments"
  -X POST
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
  -d '{
        "platform_name": "AMAZON",
        "platform_order_number": "#1234",
        "reference": "shipment reference",
        "sender_id": "ecorp",
        "destination_address": {
          "contact_name": "Jane Doe",
          "contact_email": "jane@example.eu",
          "contact_phone": "415-1234567",
          "line_1": "417 Melrose Place",
          "line_2": "FLOOR 5",
          "postal_code": "90210",
          "city": "Los Angeles",
          "state": "CA",
          "country": "US"
        },
        "parcels": [
          {
            "length": 24,
            "width": 32,
            "height": 5,
            "weight": 0.5,
            "quantity": 1
          }
        ],
        "customs_items": [
          {
            "description": "Shirts",
            "quantity": 2,
            "value": 20,
            "currency": "EUR",
            "weight": 500,
            "hs_code": "123456789",
            "origin_country": "NL"
          }
        ],
        "incoterms": "DDU",
        "courier": "fedex_international_priority",
        "exclude_rates": true,
        "buy_label_synchronous": true
      }'
```

> The above command returns JSON structured like this:

```
HTTP/1.1 201 Created
Content-Type:application/json;charset=UTF-8
```

```json
{
  "shipment": {
    "created_at": "2021-08-27T09:46:58+00:00",
    "updated_at": "2021-08-27T09:47:05+00:00",
    "id": "SHIP0002181",
    "mode": "test",
    "platform_name": "AMAZON",
    "platform_order_number": "#1234",
    "reference": "shipment reference",
    "incoterms": "DDU",
    "status": "label_generated",
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
      "contact_name": "Jane Doe",
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
        "id": "7a4a3c83-4e98-489e-a7ec-6d0861cebfd4",
        "box_name": "Custom Box",
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
        "id": "58503411-f9cc-419e-8cc1-0aa9e3cbc816",
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
    "selected_courier": {
      "carrier_id": "7605c1fc-683d-4860-a010-8fda26f2a79a",
      "carrier_admin_name": "fedex_international_priority",
      "carrier_display_name": "FedEx International Priority",
      "carrier_description": "A highly reliable, express, time-definite, customs-cleared, door-to-door service for your worldwide packages up to 68kg per unit.",
      "pickup_available": true,
      "min_delivery_time": 1,
      "max_delivery_time": 3
    },
    "label": {
      "date": "2021-08-27T11:47:05.000000Z",
      "file_type": "application\/pdf",
      "barcode": "794658261734",
      "url": "\/storage\/\/labels\/da470f08-20b3-4fa8-8464-724e4b8122c1.pdf",
      "epl2_url": null,
      "zpl_url": null,
      "pdf_url": "https:\/\/os-saas.test\/application\/labels\/da470f08-20b3-4fa8-8464-724e4b8122c1.pdf",
      "size": "4x6",
      "resolution": 200
    },
    "tracking_code": "794658261734"
  }
}
```

Before a shipment can be confirmed and a label can be purchased, a shipment needs to be created through this endpoint.

### HTTP Request

<span class="http-verb post">POST</span> `https://app.shipsmart.eu/api/shipping/v1/shipments`

### Arguments

Attribute | Type | Description
--------- | ----------- | ----------
platform_name | <span class="type">string</span> | <span class="optional">optional</span> Sales platform name. Maximum: 200 characters
platform_order_number | <span class="type">string</span> | <span class="optional">optional</span> Order number on the sales platform.
reference | <span class="type">string</span> | <span class="optional">optional</span> Reference information that prints on the shipping label (if courier allows it).
sender_id | <span class="type">string</span> | <span class="optional">optional</span> ID of the sender <span class="object">Address</span> object. The origin address for the shipment is set by this ID. If the sender id is omitted the default sender address is set as origin address. 
destination_address | <span class="type">object</span> | <span class="required">optional</span> <span class="object">Address</span> object that should be used as receiver address.
parcels | <span class="type">array</span> | <span class="required">required</span> Array of <span class="object">Parcel</span> objects with package details for the shipment to be sent.
customs_items | <span class="type">array</span> | <span class="required">required</span> Array of <span class="object">Customs Item</span> objects with details of the products in the shipment for customs.
incoterms | <span class="type">string</span> | <span class="optional">optional</span> The terms of sale of the Shipment. Valid values are `DDP`, `DDU`, `DAP`.
courier | <span class="type">string</span> | <span class="optional">optional</span> Select a specific couriers <code>admin_name</code> to create the shipment with. Use the <a href="#couriers">Couriers API</a> resource to retrieve a list of available couriers and their admin names.
exclude_rates | <span class="type">boolean</span> | <span class="optional">optional</span> When `true` rates will not be calculated for the shipment, which will lead to a faster response. Value is `false` by default.
buy_label | <span class="type">boolean</span> | <span class="optional">optional</span> When `true` a shipment is created and the label is bought in a single API call instead of two. Value is `false` by default.
buy_label_synchronous | <span class="type">boolean</span> | <span class="optional">optional</span> When `true` a label is generated synchronously and returned directly in the response. Value is `false` by default.

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
				<div class="td"><p><span class="required">required</span> Address contact name. Maximum: 35 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>company_name</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Address company name. Maximum: 35 characters </p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>contact_email</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Address contact email address. Maximum: 50 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>contact_phone</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required">required</span> Address contact phone number. Maximum: 18 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>line_1</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required">required</span> Address line 1. Maximum: 35 characters </p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>line_2</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Address line 2. Maximum: 35 characters </p></div>
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
      <div class="tr">
				<div class="td"><p><code>eori_number</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Economic Operators Registration and Identification (EORI) number</p></div>
			</div>
      <div class="tr">
				<div class="td"><p><code>vat_number</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> The consignee's tax identification number</p></div>
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
				<div class="td"><p><code>box</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Courier or Custom <span class="object">Box</span> slug. Use the <a href="#boxes">Boxes API</a> Resource to retrieve a list of available boxes. </p></div>
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
				<div class="td"><p><code>sku</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">optional</span> <span class="object">Product</span> sku. Use the Product API Resource to retrieve a list of available products.</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>description</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> sku is not given or null. Description of the item being shipped</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>quantity</code></p></div>
				<div class="td"><p><span>integer</span></p></div>
				<div class="td"><p><span class="optional">optional</span> Quantity of the item to be shipped, must be greater than zero. Defaults to <code>1</code></p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>value</code></p></div>
				<div class="td"><p><span>object</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> sku is not given or null. Value of a single item</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>currency</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">Optional</span> The currency of the item value. The account's default currency will be used if not specified</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>weight</code></p></div>
				<div class="td"><p><span>object</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> sku is not given or null. The weight of the item</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>hs_code</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="optional">Optional</span> Harmonized Tariff Code</p></div>
			</div>
			<div class="tr">
				<div class="td"><p><code>origin_country</code></p></div>
				<div class="td"><p><span>string</span></p></div>
				<div class="td"><p><span class="required_if">required if</span> sku is not given or null. Origin country of the item in Alpha 2 format. </p></div>
			</div>
		</div>
	</div>
</div>
