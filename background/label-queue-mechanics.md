# Label queue mechanics

When you upload a new sample, its initial status is _unlabeled_. Samples are always either _unlabeled_, _labeled (or labeling in progress)_, _reviewed (or reviewing in progress)_, _rejected_, or _skipped_.

As a reminder, a [sample ](main-concepts.md#sample)can be an individual image or point cloud, or can be an entire image or point cloud sequence.

Samples can be labeled individually and statuses can be individually changed by accessing a sample via a dataset's Samples tab.

Segments.ai offers a labeling & reviewing queue mechanism with automatic assignments such that collaborators can efficiently work on a dataset together.

<figure><img src="../.gitbook/assets/labelingreviewing.png" alt="&#x27;Start Labeling&#x27; and &#x27;Start Reviewing&#x27; workflows"><figcaption><p>'Start Labeling' and 'Start Reviewing' workflows</p></figcaption></figure>

{% hint style="info" %}
Samples can still be labeled individually and statuses can be individually changed by accessing a sample via a dataset's Samples tab.
{% endhint %}

### Label queue

When you press the blue "Start labeling" button, a single sample is fetched from the label queue.&#x20;

In the labeling workflow, you can press these buttons:

* **Submit**: sets the sample status to _labeled (_moving it to the review queue) and provides the next sample from the queue.
* **Skip**: sets the sample status to _skipped_.
* **Save** _(to be enabled in the dataset settings)_: sets the sample status to _labeling in progress_ but will not yet provide the next sample from the queue. Can be helpful when labeling larger samples.

The ordering of the label queue is determined as follows:

1. If there's a sample that was still in progress of being labeled by you, that sample is returned first so you can complete it before continuing
2. If there's a sample that you labeled but which got rejected in the reviewing step, that sample is thereafter returned so you can immediately correct it.
3. If no such samples exist, _unlabeled_ and _prelabeled_ samples are returned ordered by priority first (descending) and file name second (ascending). Read more about how you can [customize the queue priority](../guides/customize-label-queue-priority.md).
4. If no such samples exist, the label queue is empty and no more samples need to be labeled.

{% hint style="success" %}
**Multiple collaborators can hit the blue "Start Labeling" button.** They will each receive a uniquely assigned sample to label and jointly label the entire dataset.
{% endhint %}

### Review queue

When you press the blue "Start reviewing" button, a sample is fetched from the review queue.&#x20;

In the reviewing workflow, you can press these buttons:

* **Accept**: sets the sample status to _reviewed_.
* **Reject**: sets the sample status to _rejected_, moving it back to the label queue.
* **Skip** _(to be enabled in the dataset settings)_: sets the sample status to _skipped_.
* **Save** _(to be enabled in the dataset settings)_: sets the sample status to _reviewing in progress_ but will not yet provide the next sample from the reviewing queue. Can be helpful when reviewing larger samples.

The ordering of the review queue is determined as follows:

1. If there's a sample that was still in progress of being reviewed by you, that sample is returned first so you can complete it before continuing
2. If there's a sample which was previously rejected by this reviewer and has now been corrected (i.e., the label status went from rejected to labeled again), that sample is returned first.
3. If no such samples exist, an image which has been labeled but not reviewed yet is returned, according to the same ordering as the label queue.
4. If no such samples exist, the reviewing queue is empty and no more samples need to be reviewed.

{% hint style="success" %}
**Multiple collaborators can hit the blue "Start Reviewing" button**. They will each receive a uniquely assigned sample to review and jointly review the entire dataset.
{% endhint %}
