# Structure of the release file

The general structure of the release file is as follows:

{% code title="" %}
```json
{
    "name": "first release",
    "description": "This is a first release of Segments.ai playground dataset",
    "created_at": "2020-07-09 10:20:19.888887+00:00",
    "dataset": {
        "name": "flowers",
        "task_type": "segmentation-bitmap",
        "task_attributes": {...} // the categories etc.
        "labelsets": [
            /** list of labelsets **/
        ],
        "samples": {
            /** list of samples **/
        }
    }
    
}
```
{% endcode %}

### Sample

Each sample entry contains information about the sample (name, image URL, ...) and a list of labels.

```json
{
    "name": "donuts.jpg",
    "attributes": {
        "image": {
            "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/segments/3b8b3da2-f09a-494b-999e-37250dfbf5b6.jpg"
        }
    },
    "labels": {
        /** list of labels, indexed by labelset **/    
    }
}
```

### Label

The `attributes` field of a label contains all the info about the labeled objects. Its contents depend on the type of the label (image segmentation, cuboid,...). See [label-types.md](../../reference/label-types.md "mention") for an overview of the attributes per label type. Each label also contains basic information such as the time it was created, the user who created it, its status (e.g. LABELED).

{% code title="" %}
```bash
{
    "label_status": "LABELED",
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

### Label set

Each `labelset` entry contains the labelset's name and description:

```json
{
    "name": "ground-truth",
    "description": ""
}
```
