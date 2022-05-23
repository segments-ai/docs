# Export data

To download your labeled data, create a release on the Releases tab of your dataset. A release is a snapshot of your dataset at a specific point in time.

By clicking the download link of a release, you obtain a release file in JSON format. This release file contains all information about the dataset, tasks, samples, and labels in the release.

Please refer to [this blog post](https://segments.ai/blog/speed-up-image-segmentation-with-model-assisted-labeling) for an example of training a model on exported data.

## Structure of the release file

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

The `attributes` field of a label contains all the info about the labeled objects. Its contents depend on the type of the label (image segmentation, cuboid,...). See [label-types.md](reference/label-types.md "mention") for an overview of the attributes per label type. Each label also contains basic information such as the time it was created, the user who created it, its status (e.g. LABELED).

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

## Exporting the release file to different formats

You can export the release file to different formats with the Python SDK. Use the `export_dataset`util function for this, setting the `export_format` parameter to one of the following:

| Value            | Description                                                                                                                                                                               |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `coco-instance`  | [COCO instance](https://cocodataset.org/#format-data) segmentation format                                                                                                                 |
| `coco-panoptic`  | [COCO panoptic](https://cocodataset.org/#format-data) segmentation format                                                                                                                 |
| `yolo`           | [Yolo Darknet](https://github.com/AlexeyAB/darknet) object detection format                                                                                                               |
| `instance`       | Grayscale PNGs (16-bit) where the values correspond to instance ids                                                                                                                       |
| `semantic`       | Grayscale PNGs (8-bit) where the values correspond to category ids                                                                                                                        |
| `instance-color` | Colored PNGs where the colors correspond to different instances                                                                                                                           |
| `semantic-color` | <p>Colored PNGs where the colors correspond to different categories, with colors<br>as configured in the <a href="configure-label-editor.md">label editor settings</a> when available</p> |

Example:

```python
# pip install segments-ai
from segments import SegmentsClient, SegmentsDataset
from segments.utils import export_dataset

# Initialize a SegmentsDataset from the release file
client = SegmentsClient('YOUR_API_KEY')
release = client.get_release('jane/flowers', 'v1.0') # Alternatively: release = 'flowers-v1.0.json'
dataset = SegmentsDataset(release, labelset='ground-truth', filter_by=['labeled', 'reviewed'])

# Export to COCO panoptic format
export_dataset(dataset, export_format='coco-panoptic')
```

Alternatively, you can use the initialized `SegmentsDataset` to loop through the samples and labels, and visualize or process them in any way you please:

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
