---
description: The Python SDK is a convenient wrapper for the API.
---

# Python SDK

## Setup

{% hint style="success" %}
Please refer to [this blog post](https://segments.ai/blog/speed-up-image-segmentation-with-model-assisted-labeling) for a full example of working with the Python SDK.
{% endhint %}

First install the SDK.

```bash
pip install segments-ai --upgrade
```

Import the `segments` package in your python file and and set up a client with an API key. An API key can be created on your [user account page](https://segments.ai/account).

```python
from segments import SegmentsClient

api_key = "eabdde840de8c8853329c086bc4165591cb3d74c"
client = SegmentsClient(api_key)
```

## Datasets

### List datasets

```python
user = "jane"
datasets = client.get_datasets(user)

for dataset in datasets:
    print(dataset["name"], dataset["description"])
```

### Get a dataset

```python
dataset_identifier = "jane/flowers"
dataset = client.get_dataset(dataset_identifier)
print(dataset)
```

### Create a dataset

```python
dataset_name = "flowers"
description = "A dataset containing flowers of all kinds."
category = "garden"

dataset = client.add_dataset(dataset_name, description, category)
print(sample)
```

### Delete a dataset

```python
dataset_identifier = "jane/flowers"
client.delete_dataset(dataset_identifier)
```

## Samples

### List samples

```python
dataset = "jane/flowers"
samples = client.get_samples(dataset)

for sample in samples:
    print(sample["name"], sample["uuid"])
```

### Get a sample

```python
sample = client.get_sample(uuid="602a3eec-a61c-4a77-9fcc-3037ce5e9606")
print(sample)
```

### Create a sample

```python
dataset = "jane/flowers"
name = "violet.jpg"
attributes = {
    "image": {
        "url": "https://example.com/violet.jpg"
    }
}

sample = client.add_sample(dataset, name, attributes)
print(sample)
```

If the image is on your local computer, you should first upload it to a cloud storage service like Amazon S3, Google Cloud Storage, Imgur, or [our asset storage service](python-sdk.md#upload-a-file-as-an-asset).

{% hint style="warning" %}
If you create a sample with a URL from a public S3 bucket and you see an error on the platform, make sure to [properly configure your bucket's CORS settings](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html).
{% endhint %}

### Delete a sample

```python
client.delete_sample(uuid="602a3eec-a61c-4a77-9fcc-3037ce5e9606")
```

## Labels

### Get a label

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
task = "segmentation"

label = client.get_label(sample_uuid, task)
print(label)
```

### Create or update a label

A label can be added to a sample in relation to a _label set_, such as the default ground-truth label set, or a newly created label set for model predictions.

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
task_name = "ground-truth" # name of the label set
attributes = {
    "segmentation_bitmap": {
        "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/bert/49f6aa10-8967-4305-985c-cdc1e8f89b93.png"
    },
    "annotations": [
        {
            "id": 1,
            "category_id": 2
        },
        {
            "id": 2,
            "category_id": 3
        }
    ]
}

client.add_label(sample_uuid, task_name, attributes)
```

{% hint style="info" %}
The`segmentation_bitmap_url`refers to a 32-bit RGBA png image. The alpha channel is set to 255, and the remaining 24-bit values in the RGB channels correspond to`instance_ids.`

The easiest way to transform a segmentation bitmap into this format and upload it is by using the util function`bitmap2file`:

```python
from segments.utils import bitmap2file

# segmentation_bitmap is a numpy array of type np.uint32, with values corresponding to instance_ids
file = bitmap2file(segmentation_bitmap)
asset = client.upload_asset(file, "label.png")
segmentation_bitmap_url = asset["url"]
```

For a full example of uploading model-generated labels to Segments.ai, please refer to [this blogpost](https://segments.ai/blog/speed-up-image-segmentation-with-model-assisted-labeling).
{% endhint %}

### Delete a label

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
task_name = "segmentation"
client.delete_label(sample_uuid, task)
```

## Upload a file as an asset

Example with an image:

```python
filename = "/home/jane/flowers/violet.jpg"
with open(filename, "rb") as f:
    asset = client.upload_asset(f, filename="violet.jpg")
    
image_url = asset["url"]
```

