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

api_key = "eabdde840de8c8853329c086bc4165591cb3d521"
client = SegmentsClient(api_key)
```

## Datasets

### List datasets

#### Example

```python
user = "jane"
datasets = client.get_datasets(user)

for dataset in datasets:
    print(dataset["name"], dataset["description"])
```

#### Signature

```python
client.get_datasets(user=None)

"""Get a list of datasets.

Args:
    user (str, optional): The user for which to get the datasets. Leave empty to get datasets of current user. Defaults to None.

Returns:
    list: a list of dictionaries representing the datasets.
"""
```

### Get a dataset

#### Example

```python
dataset_identifier = "jane/flowers"
dataset = client.get_dataset(dataset_identifier)
print(dataset)
```

#### Signature

```python
client.get_dataset(dataset_identifier)

"""Get a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.

Returns:
    dict: a dictionary representing the dataset.
"""
```

### Create a dataset

#### Example

```python
dataset_name = "flowers"
description = "A dataset containing flowers of all kinds."
category = "garden"

dataset = client.add_dataset(dataset_name, description, category)
print(dataset)
```

#### Signature

```python
client.add_dataset(name, description='', task_type='segmentation-bitmap', task_attributes=None, category='other', public=False, readme='')

"""Add a dataset.

Args:
    name (str): The dataset name. Example: flowers.
    description (str, optional): The dataset description. Defaults to ''.
    task_type (str, optional): task_type (str, optional): The dataset's task type. One of 'segmentation-bitmap', 'segmentation-bitmap-highres', 'vector', 'bboxes', 'keypoints'. Defaults to 'segmentation-bitmap'.
    task_attributes (dict, optional): The dataset's task attributes. Defaults to None.
    category (str, optional): The dataset category. Defaults to 'other'.
    public (bool, optional): The dataset visibility. Defaults to False.
    readme (str, optional): The dataset readme. Defaults to ''.

Returns:
    dict: a dictionary representing the newly created dataset.
"""
```

### Update a dataset

#### Example

```python
dataset_identifier = "jane/flowers"
description = "A dataset containing flowers of all kinds."

dataset = client.update_dataset(dataset_identifier, description)
print(dataset)
```

#### Signature

```python
client.update_dataset(dataset_identifier, description=None, task_type=None, task_attributes=None, category=None, public=None, readme=None)

"""Update a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    description (str, optional): The dataset description.
    task_type (str, optional): The dataset's task type. One of 'segmentation-bitmap', 'segmentation-bitmap-highres', 'vector', 'bboxes', 'keypoints'.
    task_attributes (dict, optional): The dataset's task attributes.
    category (str, optional): The dataset category.
    public (bool, optional): The dataset visibility.
    readme (str, optional): The dataset readme.

Returns:
    dict: a dictionary representing the updated dataset.
"""
```

### Delete a dataset

#### Example

```python
dataset_identifier = "jane/flowers"
client.delete_dataset(dataset_identifier)
```

#### Signature

```python
client.delete_dataset(dataset_identifier)

"""Delete a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
"""
```

### Add a collaborator to a dataset

#### Example

```python
dataset_identifier = "jane/flowers"
username = "john"
role = "reviewer"
client.delete_dataset(dataset_identifier, username, role)
```

#### Signature

```python
client.add_dataset_collaborator(dataset_identifier, username, role='labeler')

"""Add a collaborator to a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    username (str): The username of the collaborator to be added.
    role (str, optional): The role of the collaborator to be added. One of labeler, reviewer, admin. Defaults to labeler.

Returns:
    dict: a dictionary containing the newly added collaborator with its role.
"""
```

## Samples

### List samples

#### Example

```python
dataset_identifier = "jane/flowers"
samples = client.get_samples(dataset_identifier)

for sample in samples:
    print(sample["name"], sample["uuid"])
```

#### Signature

```python
client.get_samples(dataset_identifier, per_page=1000, page=1)

"""Get the samples in a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    per_page (int, optional): Pagination parameter indicating the maximum number of samples to return. Defaults to 1000.
    page (int, optional): Pagination parameter indicating the page to return. Defaults to 1.

Returns:
    list: a list of dictionaries representing the samples.
"""
```

### Get a sample

#### Example

```python
sample = client.get_sample(uuid="602a3eec-a61c-4a77-9fcc-3037ce5e9606")
print(sample)
```

#### Signature

```python
client.get_sample(uuid)

"""Get a sample.

Args:
    uuid (str): The sample uuid.

Returns:
    dict: a dictionary representing the sample.
"""
```

### Create a sample

#### Example

```python
dataset_identifier = "jane/flowers"
name = "violet.jpg"
attributes = {
    "image": {
        "url": "https://example.com/violet.jpg"
    }
}

# metadata and priority are optional fields
metadata = {
    "city": "London",
    "weather": "cloudy",
    "robot_id": 3
}
priority = 10 # Samples with higher priority value will be labeled first. Default is 0.

sample = client.add_sample(dataset_identifier, name, attributes, metadata, priority)
print(sample)
```

#### Signature

```python
client.add_sample(dataset_identifier, name, attributes, metadata=None, priority=None)

"""Add a sample to a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the sample.
    attributes (dict): The sample attributes. Please refer to the online documentation.
    metadata (dict, optional): Any sample metadata. Example: {'weather': 'sunny', 'camera_id': 3}.
    priority (float, optional): Priority in the labeling queue. Samples with higher values will be labeled first. Default is 0.

Returns:
    dict: a dictionary representing the newly created sample.
"""
```

If the image is on your local computer, you should first upload it to a cloud storage service like Amazon S3, Google Cloud Storage, Imgur, or [our asset storage service](python-sdk.md#upload-a-file-as-an-asset).

{% hint style="warning" %}
If you create a sample with a URL from a public S3 bucket and you see an error on the platform, make sure to [properly configure your bucket's CORS settings](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html).
{% endhint %}

### Update a sample

#### Example

```python
uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
metadata = {
    "city": "London",
    "weather": "cloudy",
    "robot_id": 3
}
priority = 10 # Samples with higher priority value will be labeled first. Default is 0.

sample = client.update_sample(uuid, metadata=metadata, priority=priority)
print(sample)
```

#### Signature

```python
client.update_sample(uuid, name=None, attributes=None, metadata=None, priority=None)

"""Update a sample.

Args:
    uuid (str): The sample uuid.
    name (str, optional): The name of the sample.
    attributes (dict, optional): The sample attributes. Please refer to the online documentation.
    metadata (dict, optional): Any sample metadata. Example: {'weather': 'sunny', 'camera_id': 3}.
    priority (float, optional): Priority in the labeling queue. Samples with higher values will be labeled first. Default is 0.

Returns:
    dict: a dictionary representing the updated sample.
"""
```

### Delete a sample

#### Example

```python
client.delete_sample(uuid="602a3eec-a61c-4a77-9fcc-3037ce5e9606")
```

#### Signature

```python
client.delete_sample(uuid)

"""Delete a sample.

Args:
    uuid (str): The sample uuid.
"""
```

## Labels

### Get a label

#### Example

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"

label = client.get_label(sample_uuid)
print(label)
```

#### Signature

```python
client.get_label(sample_uuid, labelset='ground-truth')

"""Get a label.

Args:
    sample_uuid (str): The sample uuid.
    labelset (str): The labelset this label belongs to. Defaults to 'ground-truth'.

Returns:
    dict: a dictionary representing the label.
"""
```

### Create a label

A label can be added to a sample in relation to a _label set_, such as the default ground-truth label set, or a newly created label set for model predictions. You can create a new label set by clicking the "Add new label set" link on the Samples tab.

The content of the `attributes` field depends on the [label type](label-types.md).

#### Example

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
labelset = "ground-truth"
attributes = {
    "format_version": "0.1",
    "annotations": [
        {
            "id": 1,
            "category_id": 2
        },
        {
            "id": 2,
            "category_id": 3
        }
    ],
    "segmentation_bitmap": {
        "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/bert/49f6aa10-8967-4305-985c-cdc1e8f89b93.png"
    },
}

client.add_label(sample_uuid, labelset, attributes)
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

#### Signature

```python
client.add_label(sample_uuid, labelset, attributes, label_status='PRELABELED')

"""Add a label to a sample.

Args:
    sample_uuid (str): The sample uuid.
    labelset (str): The labelset this label belongs to.
    attributes (dict): The label attributes. Please refer to the online documentation.
    label_status (str, optional): The label status. Defaults to 'PRELABELED'.
    score (float, optional): The label score. Defaults to None.

Returns:
    dict: a dictionary representing the newly created label.
"""
```

### Update a label

#### Example

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
labelset = "ground-truth"
attributes = {
    "format_version": "0.1",
    "annotations": [
        {
            "id": 1,
            "category_id": 2
        },
        {
            "id": 2,
            "category_id": 3
        }
    ],
    "segmentation_bitmap": {
        "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/bert/49f6aa10-8967-4305-985c-cdc1e8f89b93.png"
    },
}

client.update_label(sample_uuid, labelset, attributes)
```

#### Signature

```python
client.update_label(sample_uuid, labelset, attributes=None, label_status='PRELABELED', score=None)

"""Update a label.

Args:
    sample_uuid (str): The sample uuid.
    labelset (str): The labelset this label belongs to.
    attributes (dict): The label attributes. Please refer to the online documentation.
    label_status (str, optional): The label status. Defaults to 'PRELABELED'.
    score (float, optional): The label score. Defaults to None.

Returns:
    dict: a dictionary representing the updated label.
"""
```

### Delete a label

#### Example

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
labelset = "ground-truth"
client.delete_label(sample_uuid, labelset)
```

#### Signature

```python
client.delete_label(sample_uuid, labelset)

"""Delete a label.

Args:
    sample_uuid (str): The sample uuid.
    labelset (str): The labelset this label belongs to.
"""
```

## Releases

### List releases

#### Example

```python
dataset_identifier = "jane/flowers"
releases = client.get_releases(dataset_identifier)

for release in releases:
    print(release["name"], release["description"], release["attributes"]["url"])
```

#### Signature

```python
client.get_releases(dataset_identifier)

"""Get the releases in a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.

Returns:
    list: a list of dictionaries representing the releases.
"""
```

### Get a release

#### Example

```python
dataset_identifier = "jane/flowers"
name = "v0.1"

release = client.get_release(dataset_identifier, name)
print(release)
```

#### Signature

```python
client.get_release(dataset_identifier, name)

"""Get a release.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the release.

Returns:
    dict: a dictionary representing the release.
"""
```

### Create a release

#### Example

```python
dataset_identifier = "jane/flowers"
name = "v0.1"
description = "My first release."

release = client.add_release(dataset_identifier, name, description)
print(release)
```

#### Signature

```python
client.add_release(dataset_identifier, name, description='')

"""Add a release to a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the release.
    description (str, optional): The release description.

Returns:
    dict: a dictionary representing the newly created release.
"""
```

### Delete a release

#### Example

```python
dataset_identifier = "jane/flowers"
name = "v0.1"

client.delete_release(dataset_identifier, name)
```

#### Signature

```python
client.delete_release(dataset_identifier, name)

"""Delete a release.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the release.
"""
```

## Upload a file as an asset

#### Example

```python
filename = "/home/jane/flowers/violet.jpg"
with open(filename, "rb") as f:
    asset = client.upload_asset(f, filename="violet.jpg")
    
image_url = asset["url"]
```

#### Signature

```python
client.upload_asset(file, filename='label.png')

"""Upload an asset.

Args:
    file (object): A file object.
    filename (str, optional): The file name. Defaults to label.png.

Returns:
    dict: a dictionary representing the uploaded file.
"""
```



