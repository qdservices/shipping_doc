# Labels

With the Label resource, you can confirm a Shipment that was created using the Shipment API. Calling Buy Labels will confirm a Shipment with the selected Courier and begin generating the Label & Shipping Documents after checking your account’s balance is sufficient.

If your Shipment does not have a Courier assigned to it yet, you can specify a courier_id to the Label resource to choose your Courier and confirm your Shipment. If there is no assigned Courier and you don’t include a courier_id, we will assign the best value for money Courier to your Shipment.

<aside class="warning">
<div class="h3">Asynchronous response</div>
<p>The Label & Shipping Documents will be generated asynchronously.
If you specified a Callback URL with the Company API, or through the OMNISHIP Dashboard, 
this URL will be called when the documents are ready.</p>
<p>Whilst these documents are being generated, the label_state will be set to pending. 
The possible states are not_created, pending, failed and generated.</p>
<p>For more information on asynchronous API response handling, please see the Asynchronous Responses section of the documentation.</p>
</aside>







