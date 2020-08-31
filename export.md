# Exporting data

To download your labeled data, you need to create a release on the Releases tab. A release is a snapshot of your dataset at a specific point in time.

By clicking the download link of a release, you obtain a release file in JSON format. This release file contains all information about the dataset, tasks, samples, and labels in the release.

{% hint style="info" %}
Note that the segmentation masks are encoded as a png image that appears black when opened in an image viewer. The png image contains all necessary information though. [Read more below](export.md#segmentation-bitmap).
{% endhint %}

## Exporting the release file to COCO format

You can export the release file to COCO format with the Python SDK:

```python
# pip install segments-ai
from segments import SegmentsDataset
from segments.utils import export_dataset

release_file = 'flowers-v1.0.json'
dataset = SegmentsDataset(release_file, task='segmentation', filter_by=['labeled', 'reviewed'])
export_dataset(dataset, 'coco')
```

## Structure of the release file

The general structure of the release file is as follows:

{% code title="" %}
```bash
{
    "name": "first release",
    "description": "This is a first release of Segments.ai playground dataset",
    "created_at": "2020-07-09 10:20:19.888887+00:00",
    "dataset": {
        "name": "flowers",
        "tasks": [
            ** list of tasks **
        ],
        "samples": {
            ** list of samples **
        }
    }
    
}
```
{% endcode %}

### Task

Each task entry contains the task's name, description and its defined categories \(with name and id\):

{% code title="" %}
```bash
{
    "name": "segmentation",
    "description": "",
    "task_type": "segmentation-bitmap",
    "attributes": {
        "categories": [
            {
                "name": "person",
                "id": 0
            },
            {
                "name": "donut",
                "id": 1
            }
        ]
    }
}
```
{% endcode %}

### Sample

Each sample entry contains information about the sample \(name, image URL, ...\) and a list of labels.

{% code title="" %}
```bash
{
    "name": "donuts.jpg",
    "data_type": "IMAGE",
    "attributes": {
        "image": {
            "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/segments/3b8b3da2-f09a-494b-999e-37250dfbf5b6.jpg"
        }
    },
    "labels": {
        /** list of labels **/    
    }
}
```
{% endcode %}

### Label

Each label contains information about the label\_status \(LABELED or REVIEWED\) and provides a list of annotations \(labeled objects\) together with a segmentation bitmap.

{% code title="" %}
```bash
{
    "label_status": "LABELED",
    "label_type": "segmentation-bitmap",
    "attributes": {
        "format_version": "0.1",
        "annotations": [
            {
                "id": 1,
                "category_id": 1
            },
            {
                "id": 2,
                "category_id": 1
            },
            {
                "id": 3,
                "category_id": 1
            },
            {
                "id": 4,
                "category_id": 1
            }
        ],
        "segmentation_bitmap": {
            "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/segments/504e7633-ef51-49c3-8b0e-d4eb9100532d.png"
        }
    }
}
```
{% endcode %}

### Segmentation bitmap

The`segmentation_bitmap_url`refers to a 32-bit RGBA png image. The alpha channel is set to 255, and the remaining 24-bit values in the RGB channels correspond to`instance_ids.`Because of this large dynamic range, these png images appear black in an image viewer.

