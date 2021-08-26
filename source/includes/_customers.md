# Customers

> Example:

```json
{
  "id": 48,
  "code": "PDA",
  "name": "Post Delivery Amsterdam",
  "weight_unit": "grams",
  "created_at": "2021-06-30T13:54:39+02:00",
  "updated_at": "2021-06-30T13:57:39+02:00"
}
    
```

A customer is the owner of an uploaded shipment. The customer code is needed to identify the customer on uploading
a new Waybill pre alert.

Attribute | Type | Description
--------- | ------- | -----------
`id` | <span class=type>integer</span> | Unique ID of a customer. This is used as an identifier.
`code` | <span class=type>string</span> | Unique code to identify a customer.
`name` | <span class=type>string</span> | Name of the customer
`weight_unit` | <span class=type>string</span> | The default weight unit used for a customer on upload.
`created_at` | <span class=type>string</span> | Date when the customer resource was first created.
`updated_at` | <span class=type>string</span> | Date when the customer was last updated.







