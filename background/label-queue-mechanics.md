# Label queue mechanics

When you upload a new sample, its initial status is _unlabeled_. Samples are always either _unlabeled_, _labeled_, _reviewed_, _rejected_, or _skipped_.

### Label queue

When you press the "Start labeling" button, a sample is fetched from the label queue.&#x20;

In the labeling workflow, you can press these buttons:

* **Submit**: sets the sample status to _labeled_, moving it to the review queue.
* **Skip**: sets the sample status to _skipped_.

The ordering of the label queue is determined as follows:

1. If there's a sample that you labeled but which got rejected in the reviewing step, that sample is returned first so you can immediately correct it.
2. If no such samples exist, _unlabeled_ samples are returned ordered by priority first (descending) and file name second (ascending). Read more about how you can [customize the queue priority](../guides/customize-label-queue-priority.md).
3. If no such samples exist, the label queue is empty and no more samples need to be labeled.

### Review queue

When you press the "Start reviewing" button, a sample is fetched from the review queue.&#x20;

In the reviewing workflow, you can press these buttons:

* **Accept**: sets the sample status to _reviewed_.
* **Reject**: sets the sample status to _rejected_, moving it back to the label queue.
* **Skip**: sets the sample status to _skipped_.

The ordering of the review queue is determined as follows:

1. If there's a sample which was previously rejected by this reviewer and has now been corrected (i.e., the label status went from rejected to labeled again), that sample is returned first.
2. If no such samples exist, an image which has been labeled but not reviewed yet is returned, according to the same ordering as the label queue.
3. If no such samples exist, the reviewing queue is empty and no more samples need to be reviewed.
