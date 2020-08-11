# Python SDK

## Setup

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

## Samples

### Get all samples in a dataset

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

## Labels

### Get a label

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
task = "segmentation"

label = client.get_label(sample_uuid, task)
print(label)
```

### Create or update a label for a sample

A label can be added to a sample in relation to a _task_ defined on the dataset, such as an image classification task or an image segmentation task.

The task specifies the format that is required for the label: for a classification task, the `attributes`field should contain different fields than for a segmentation task.

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
task_name = "segmentation"
attributes = {
    "segmentation_bitmap": {
        "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/bert/49f6aa10-8967-4305-985c-cdc1e8f89b93.png"
    },
    "annotations": [
        {
            "id": 1
            "category_id": 2
        },
        {
            "id": 2
            "category_id": 3
        }
    ]
}

client.add_label(sample_uuid, task_name, attributes)
```

{% hint style="info" %}
For a segmentation task, the`segmentation_bitmap_url`field should refer to a 32-bit RGBA png image with alpha channel set to 255 and values corresponding to`instance_id`
{% endhint %}

## Upload a file as an asset

Example with an image:

```python
from PIL import Image
from io import BytesIO

image = Image.open("/home/jane/flowers/violet.jpg")
file = BytesIO()
image.save(file, 'PNG')

asset = client.upload_asset(file, filename="violet.jpg")
image_url = asset["url"]
```

