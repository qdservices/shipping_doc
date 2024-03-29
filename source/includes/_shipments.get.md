## Get a Shipment

```shell
curl "https://app.omniship.eu/api/shipping/v1/shipments/SHIP0002184"
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

This endpoint retrieves a specific Shipment.

### HTTP Request

<span class="http-verb get">GET</span> `https://app.omniship.eu/api/shipping/v1/shipments/<ID>`

### URL Parameters

| Parameter | Description                     |
|-----------|---------------------------------|
| ID        | The Shipment ID of the Shipment |
