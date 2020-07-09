# Release

A release contains a snapshot of the dataset and can be used to download the labeled samples. The format is JSON.

The release contains information about the dataset, tasks and a list of samples together with its labels. The general structure is as follows:

{% code %}
```bash
{
    "name": "first release",
    "description": "This is a first release of Segments.ai playground dataset",
    "created_at": "2020-07-09 10:20:19.888887+00:00",
    "tasks": [
        ** list of tasks **
    ],
    "samples": [
        ** list of samples **
    ]
}
```
{% endcode %}

## Task

Each task entry contains the task's name, description and its defined categories (with name and id):

{% code %}
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

## Sample

Each sample entry contains information about the sample (name, image url, ...) and a list of labels.

{% code %}
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

Each label contains information about the label_status (LABELED or REVIEWED) and provides a list of annotations (labeled objects) together with a segmentation bitmap.

{% code %}
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

To retrieve the bitmask of each annotation, you can index the segmentation bitmap (a 32-bit RGBA png) with the annotation id.


