# Customize label queue

You can customize the label queue by setting a sample priority and by assigning samples to a specific labeler or reviewer. An in-depth explanation of how the label queue order is determined is available in [label-queue-mechanics.md](../background/label-queue-mechanics.md "mention").

## Set sample priority

The priority value of a sample determines its [order in the label queue](../background/label-queue-mechanics.md): samples with a higher priority value are labeled first. When a new sample is added to a dataset, its default priority is 0.

{% hint style="info" %}
Note that you can also assign a negative priority to a sample.
{% endhint %}

To change the priority of a group of samples, select the samples you want to update and click the "Edit" button. In the pop-up window, fill in the desired priority value, and press "Update".

![](<../.gitbook/assets/image (16).png>)

### Set the priority programmatically

You can also [set the priority value of a sample using the Python SDK](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample).



## Assign a specific labeler or reviewer

By default, a sample is not assigned to a specific labeler or reviewer, meaning that the sample can be labeled or reviewed by anyone.

&#x20;If you want to ensure that a specific sample is labeled or reviewed by a particular user, you can set the fields `assigned_labeler` and `assigned_reviewer` when [creating the sample using the Python SDK](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample).
