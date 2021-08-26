# Waybills

> Example:

```json
{
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
  ]
}
    
```

A waybill is a document that represents the contents of a shipment ready for transport. It details
the exact quantity, price and delivery details of the individual packages. 
Perform the simple operations mentioned below to create and manage your Waybill pre alert.

Attribute | Type | Description
--------- | ------- | -----------
`customer_code` | <span class=type>string</span> | Unique ID of a customer. This is used as an identifier.
`waybill_type` | <span class=type>string</span> | The type of waybill. Valid values are ('air', 'road', 'train', 'sea', 'other').
`waybill_number` | <span class=type>string</span> | Identifies the total shipment. If waybill type is 'air' a validation check is done on the format of the waybill_number given.
`reference` | <span class=type>string</span> | Unique identifier of the shipment. Usually an id of the original system where the pre-alert was uploaded.
`weight_unit` | <span class=type>string</span> | Unit of weight used in the pre-alert. Valid values are ('grams', 'kilograms')
`pre_alert_rows` | <span class=type>array</span> | A pre alert contains multiple pre_alert rows. Each pre alert row contains `order_number`, `package_barcode`, `bag_grade`, `shipping_method`, `weight`, `company_name`, `consignee_name`, `phone_number`, `email_address`, `street`, `house_number`, `house_number_extension`, `additional_address_info`, `city_or_town`, `state_or_province`, `zip_code`, `country_code`, `sku_code`, `sku_description`, `quantity`, `currency`, `price`, `shipping_costs`, `hs_code`, `website`







