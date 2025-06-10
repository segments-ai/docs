# Upload model predictions

## Uploading as pre-labels

Once you've trained an initial machine learning model on your labeled data, you can upload the model predictions as _pre-labels_ to further speed up your labeling workflow.

To add a label to a sample programmatically, use the [`client.add_label()`](https://sdkdocs.segments.ai/en/latest/client.html#create-a-label) function in the Python SDK. Note that the format of the `attributes` field depends on the [label type](../reference/label-types.md).

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
