# Shipments

The Shipment resource is used to create, list, update and delete Shipments.

A Shipment will not be confirmed or paid for until you buy the label. This can be done by calling the `Buy Labels` endpoint or
by using the `buy_label` or `buy_label_synchronous` attribute in the Create Shipment request.
Once you Buy Labels for a Shipment through the <a href="#labels">Label API</a>, you will not be able to update or delete it.

<aside class="notice">
<div class="h3">Selecting a Specific Courier</div>
<p>You can specify a specific <span class="object"> Courier </span> <code> admin_name </code> to already assign to the Shipment, using the <code> courier </code> attribute.
If you don’t pass in a <span class="object"> Courier </span> <code> admin_name </code>, we will assign the best value for money Courier to your Shipment. Use the 
<a href="#couriers">Couriers API</a>  to get a list of available couriers and their admin names. </p>
</aside>
