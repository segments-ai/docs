# Customize label queue priority

The priority value of a sample determines its [order in the label queue](../background/label-queue-mechanics.md): samples with a higher priority value are labeled first. When a new sample is added to a dataset, its default priority is 0.

{% hint style="info" %}
Note that you can also assign a negative priority to a sample.
{% endhint %}

To change the priority of a group of samples, select the samples you want to update and click the "Edit" button. In the pop-up window, fill in the desired priority value, and press "Update".

![](<../.gitbook/assets/image (16).png>)

### Set the priority programmatically

You can also [set the priority value of a sample using the Python SDK](../python-sdk.md#create-a-sample).
