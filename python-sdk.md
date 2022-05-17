---
description: The Python SDK is a convenient wrapper for the API.
---

# Python SDK

## Setup

{% hint style="success" %}
Please refer to the [Python SDK quickstart](tutorials/python-sdk-quickstart.md) for a full example of working with the Python SDK.
{% endhint %}

First install the SDK.

```bash
pip install segments-ai --upgrade
```

Import the `segments` package in your python file and and set up a client with an API key. An API key can be created on your [user account page](https://segments.ai/account).

```python
from segments import SegmentsClient

api_key = "YOUR_API_KEY"
client = SegmentsClient(api_key)
```

## Datasets

### List datasets

#### Example

```python
datasets = client.get_datasets()

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
task_type = "segmentation-bitmap"

dataset = client.add_dataset(dataset_name, description, task_type)
print(dataset)
```

| Task type                                 | Value                              |
| ----------------------------------------- | ---------------------------------- |
| Image segmentation labels (bitmap)        | `segmentation-bitmap`              |
| Image bounding box labels                 | `bboxes`                           |
| Image vector labels                       | `vector`                           |
| Pointcloud cuboid labels                  | `pointcloud-cuboid`                |
| Pointcloud cuboid labels (sequence)       | `pointcloud-cuboid-sequence`       |
| Pointcloud segmentation labels            | `pointcloud-segmentation`          |
| Pointcloud segmentation labels (sequence) | `pointcloud-segmentation-sequence` |
| Text named entity labels                  | `text-named-entities`              |
| Text span categorization labels           | `text-span-categorization`         |

#### Signature

```python
client.add_dataset(self, name, description='', task_type='segmentation-bitmap', task_attributes=None, category='other', public=False, readme='', enable_skip_labeling=True, enable_skip_reviewing=False, enable_ratings=False)

"""Add a dataset.

Args:
    name (str): The dataset name. Example: flowers.
    description (str, optional): The dataset description. Defaults to ''.
    task_type (str, optional): The dataset's task type. One of 'segmentation-bitmap', 'segmentation-bitmap-highres', 'vector', 'bboxes', 'keypoints'. Defaults to 'segmentation-bitmap', 'pointcloud-segmentation', 'pointcloud-detection'.
    task_attributes (dict, optional): The dataset's task attributes. Defaults to None.
    category (str, optional): The dataset category. Defaults to 'other'.
    public (bool, optional): The dataset visibility. Defaults to False.
    readme (str, optional): The dataset readme. Defaults to ''.
    enable_skip_labeling (bool, optional): Enable the skip button in the labeling workflow. Defaults to True.
    enable_skip_reviewing (bool, optional): Enable the skip button in the reviewing workflow. Defaults to False.
    enable_ratings: Enable star-ratings for labeled images. Defaults to False.

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
client.update_dataset(self, dataset_identifier, description=None, task_type=None, task_attributes=None, category=None, public=None, readme=None, enable_skip_labeling=None, enable_skip_reviewing=None, enable_ratings=None)

"""Update a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    description (str, optional): The dataset description.
    task_type (str, optional): The dataset's task type. One of 'segmentation-bitmap', 'segmentation-bitmap-highres', 'vector', 'bboxes', 'keypoints', 'pointcloud-segmentation', 'pointcloud-detection'.
    task_attributes (dict, optional): The dataset's task attributes.
    category (str, optional): The dataset category.
    public (bool, optional): The dataset visibility.
    readme (str, optional): The dataset readme.
    enable_skip_labeling (bool, optional): Enable the skip button in the labeling workflow.
    enable_skip_reviewing (bool, optional): Enable the skip button in the reviewing workflow.
    enable_ratings: Enable star-ratings for labeled images.

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
client.add_dataset_collaborator(dataset_identifier, username, role)
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
get_samples(self, dataset_identifier, name=None, label_status=None, metadata=None, sort='name', direction='asc', per_page=1000, page=1)

"""Get the samples in a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str, optional): Name to filter by. Defaults to None (no filtering).
    label_status (list, optional): List of label statuses to filter by. Defaults to None (no filtering).
    metadata (list, optional): List of 'key:value' metadata attributes to filter by. Defaults to None (no filtering).
    sort (str, optional): What to sort results by. One of 'name', 'created', 'priority'. Defaults to 'name'.
    direction (str, optional): Sorting direction. One of 'asc' (ascending) or 'desc' (descending). Defaults to 'asc'.
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
client.get_sample(uuid, labelset=None)

"""Get a sample.

Args:
    uuid (str): The sample uuid.
    labelset (str, optional): If defined, this additionally returns the label for the given labelset. Defaults to None. 

Returns:
    dict: a dictionary representing the sample.
"""
```

### Create a sample

The content of the `attributes` field depends on the [sample type](reference/sample-and-label-types/sample-types.md).

{% hint style="info" %}
If the image file is on your local computer, you should first upload it to a cloud storage service like Amazon S3, Google Cloud Storage, Imgur, or [our asset storage service](python-sdk.md#upload-a-file-as-an-asset).
{% endhint %}

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

A label is added to a sample in relation to a _label set_, such as the default _ground-truth_ label set, or a newly created label set for [uploading model predictions](guides/upload-model-predictions.md). You can create a new label set by clicking the "Add new label set" link on the Samples tab.

The content of the `attributes` field depends on the [label type](reference/sample-and-label-types/label-types.md).

#### Example

```python
sample_uuid = "602a3eec-a61c-4a77-9fcc-3037ce5e9606"
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
        },
    ]
}

client.add_label(sample_uuid, labelset, attributes)
```

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
            "category_id": 1,
            "type": "bbox",
            "points": [
              [12.34, 56.78],
              [90.12, 34.56]
            ]
        },
    ]
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

## Label sets

A label is added to a sample in relation to a _label set_, such as the default _ground-truth_ label set, or a newly created label set for [uploading model predictions](guides/upload-model-predictions.md).

### List label sets

#### Example

```python
dataset_identifier = "jane/flowers"
labelsets = client.get_labelsets(dataset_identifier)

for labelset in labelsets:
    print(labelset["name"], labelset["description"])
```

#### Signature

```python
client.get_labelsets(dataset_identifier)

"""Get the labelsets in a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.

Returns:
    list: a list of dictionaries representing the labelsets.
"""
```

### Get a label set

#### Example

```python
dataset_identifier = "jane/flowers"
name = "model-predictions"

labelset = client.get_labelset(dataset_identifier, name)
print(labelset)
```

#### Signature

```python
client.get_labelset(dataset_identifier, name)

"""Get a labelset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the labelset.

Returns:
    dict: a dictionary representing the labelset.
"""
```

### Create a label set

You can also create a new label set by clicking the "Add new label set" link on the Samples tab.

#### Example

```python
dataset_identifier = "jane/flowers"
name = "model-predictions-resnet50"

client.add_labelset(dataset_identifier, name)
```

#### Signature

```python
client.add_labelset(dataset_identifier, name, description='')

"""Add a labelset to a dataset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the labelset.
    description (str, optional): The labelset description.

Returns:
    dict: a dictionary representing the labelset.
"""
```

### Delete a label set

#### Example

```python
dataset_identifier = "jane/flowers"
name = "model-predictions"

client.delete_labelset(dataset_identifier, name)
```

#### Signature

```python
client.delete_labelset(dataset_identifier, name)

"""Delete a labelset.

Args:
    dataset_identifier (str): The dataset identifier, consisting of the name of the dataset owner followed by the name of the dataset itself. Example: jane/flowers.
    name (str): The name of the labelset.
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

