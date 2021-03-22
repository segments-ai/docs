# Exporting data

To download your labeled data, you need to create a release on the Releases tab. A release is a snapshot of your dataset at a specific point in time.

By clicking the download link of a release, you obtain a release file in JSON format. This release file contains all information about the dataset, tasks, samples, and labels in the release.

{% hint style="info" %}
Note that the segmentation masks are encoded as a png image that appears black when opened in an image viewer. The png image contains all necessary information though. [Read more below](export.md#segmentation-bitmap).
{% endhint %}

## Exporting the release file to COCO format

You can export the release file to [COCO format](https://cocodataset.org/#format-data) with the Python SDK. Set `export_format` to `coco-instance` for the object detection format, or to `coco-panoptic` for the panoptic segmentation format. For bounding box datasets, you can set the export format to `yolo`.

```python
# pip install segments-ai
from segments import SegmentsDataset
from segments.utils import export_dataset

# Initialize a SegmentsDataset from the release file
release_file = 'flowers-v1.0.json'
dataset = SegmentsDataset(release_file, labelset='ground-truth', filter_by=['labeled', 'reviewed'])

# Export to COCO panoptic format
export_dataset(dataset, export_format='coco-panoptic')
```

Alternatively, you can use the initialized SegmentsDataset to loop through the samples and labels, and visualize or process them in any way you please:

```python
import matplotlib.pyplot as plt
from segments.utils import get_semantic_bitmap

for sample in dataset:
    # Print the sample name and list of labeled objects
    print(sample['name'])
    print(sample['annotations'])
    
    # Show the image
    plt.imshow(sample['image'])
    plt.show()
    
    # Show the instance segmentation label
    plt.imshow(sample['segmentation_bitmap'])
    plt.show()
    
    # Show the semantic segmentation label
    semantic_bitmap = get_semantic_bitmap(sample['segmentation_bitmap'], sample['annotations'])
    plt.imshow(semantic_bitmap)
    plt.show()
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
        "task_type": "segmentation-bitmap",
        "task_attributes": {...} # the categories etc.
        "labelsets": [
            ** list of labelsets **
        ],
        "samples": {
            ** list of samples **
        }
    }
    
}
```
{% endcode %}

### Label set

Each `labelset` entry contains the labelset's name and description:

{% code title="" %}
```bash
{
    "name": "ground-truth",
    "description": ""
}
```
{% endcode %}

### Sample

Each sample entry contains information about the sample \(name, image URL, ...\) and a list of labels.

{% code title="" %}
```bash
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
{% endcode %}

### Label

Each label contains basic information such as the time it was created, the user who created it, its status \(e.g. LABELED\). The `attributes` field contains all info about the labeled objects. Its contents depend on the labeling type \(segmentation or bounding boxes\) and are described in more detail [here](label-types.md).

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

Please refer to [this blog post](https://segments.ai/blog/speed-up-image-segmentation-with-model-assisted-labeling) for an example of training a model on exported data.

