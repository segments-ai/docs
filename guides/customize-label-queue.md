# Customize label queue

You can customize the label queue by setting a sample priority and by assigning samples to a specific labeler or reviewer. An in-depth explanation of how the label queue order is determined is available in [label-queue-mechanics.md](../background/label-queue-mechanics.md "mention").

## Set sample priority

The priority value of a sample determines its [order in the label queue](../background/label-queue-mechanics.md): samples with a higher priority value are labeled first. When a new sample is added to a dataset, its default priority is 0.

{% hint style="info" %}
Note that you can also assign a negative priority to a sample.
{% endhint %}

To change the priority of a group of samples, select the samples you want to update and click the "Edit" button. In the pop-up window, fill in the desired priority value, and press "Update".

<figure><img src="../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>

### Set the priority programmatically

You can also [set the priority value of a sample using the Python SDK](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample).

## Assign a specific labeler or reviewer

By default, a sample is not assigned to a specific labeler or reviewer, meaning that the sample can be labeled or reviewed by anyone. See [label-queue-mechanics.md](../background/label-queue-mechanics.md "mention")for more details.

If you want to ensure that a specific sample is labeled or reviewed by a particular user, you can set an assigned labeler and reviewer for it.

To change the assigned labeler and/or reviewer of a group of samples, select the samples you want to update and click the "Edit" button. In the pop-up window, fill in the username in the appropriate field, and press "Update".

### Assign programmatically

You can also set the `assigned_labeler` and `assigned_reviewer` fields [using the Python SDK](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample).
