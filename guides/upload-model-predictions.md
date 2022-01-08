# Upload model predictions

## Uploading as pre-labels

Once you've trained an initial machine learning model on your labeled data, you can upload the model predictions as _pre-labels_ to further speed up your labeling workflow.

To add a label to a sample programmatically, use the [`client.add_label()`](../reference/python-sdk.md#create-a-label) function in the Python SDK. Note that the format of the `attributes` field depends on the [label type](../reference/sample-and-label-types/label-types.md).

```json
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9123"
labelset = "ground-truth"
attributes = {
    "format_version": "0.1",
    "annotations": [
        {
          "id": 1,
          "category_id": 1,
          "type": "bbox",
          "points": [
            [12.34, 56.78],
            [90.12, 34.56]
          ]
        }
    ]
}

client.add_label(sample_uuid, labelset, attributes)
```

The sample will now have a label status of _prelabeled_, and will appear in the label queue along with any unlabeled samples. Instead of having to label the sample from scratch, the labelers can now focus on verifying and correcting the pre-label though.

## Uploading in a separate label set

Instead of uploading the labels as pre-labels of the ground truth label set, you can also upload them in a separate label set. Doing so unlocks a few features:

* You can visualize the ground truth and predicted labels side by side.
* When labeling, you can copy the label from any label set with the click of a button, to avoid labeling from scratch.
* You can upload a prediction score along with the label, allowing you to sort and browse your predictions by accuracy.
* You can search through the ground-truth and uploaded labels simultaneously. For example,  `ground-truth.car:>0 my-predictions.car:=0` matches samples where the "ground-truth" label contains strictly more than 0 "car" objects AND the "my-predictions" label contains 0 "car" objects. For more information, see [how to search through the dataset](search-functionality.md).

![](<../.gitbook/assets/image (5).png>)

![](<../.gitbook/assets/image (12).png>)

First, create a new label set:

1. Go to the Samples tab.
2. Click the "Add new label set" link.
3. Choose a name and optionally a description for the new label set.
4. Click the "Create" button.

Then, refer to this label set when adding a label to a sample using [`client.add_label()`](../reference/python-sdk.md#create-a-label):

```json
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9123"
labelset = "name-of-your-labelset"
attributes = {
    "format_version": "0.1",
    "annotations": [
        {
          "id": 1,
          "category_id": 1,
          "type": "bbox",
          "points": [
            [12.34, 56.78],
            [90.12, 34.56]
          ]
        }
    ]
}
score = 0.92

client.add_label(sample_uuid, labelset, attributes, score=score)
```



