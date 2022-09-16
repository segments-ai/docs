# Exporting the release file to different formats

## Exporting the release file to different formats

You can export the release file to different formats with the Python SDK. Use the `export_dataset`util function for this, setting the `export_format` parameter to one of the following:

| Value            | Description                                                                                                                                                                                     |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `coco-instance`  | [COCO instance](https://cocodataset.org/#format-data) segmentation format                                                                                                                       |
| `coco-panoptic`  | [COCO panoptic](https://cocodataset.org/#format-data) segmentation format                                                                                                                       |
| `yolo`           | [Yolo Darknet](https://github.com/AlexeyAB/darknet) object detection format                                                                                                                     |
| `instance`       | Grayscale PNGs (16-bit) where the values correspond to instance ids                                                                                                                             |
| `semantic`       | Grayscale PNGs (8-bit) where the values correspond to category ids                                                                                                                              |
| `instance-color` | Colored PNGs where the colors correspond to different instances                                                                                                                                 |
| `semantic-color` | <p>Colored PNGs where the colors correspond to different categories, with colors<br>as configured in the <a href="../../configure-label-editor.md">label editor settings</a> when available</p> |
| `polygon`        | For exporting segmentation bitmap labels to polygons                                                                                                                                            |

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
