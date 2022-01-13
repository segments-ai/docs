# Label types

When downloading or uploading labels using the [Python SDK](../../python-sdk.md), the format of the`attributes` field depends on the type of label. The different formats are described here.

## Image

### Segmentation labels

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```javascript
{
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, // this is an object id. Should be > 0.
      "category_id": 1 // this is a category id
    },
    {
      "id": 2, 
      "category_id": 1
    },
    {
      "id": 3, 
      "category_id": 4
    }
  ],
  "segmentation_bitmap": {
    "url": "https://segmentsai-staging.s3.eu-west-2.amazonaws.com/assets/davy/ddf55e99-1a6f-42d2-83e9-8657de3259a1.png"
  }
}
```

{% hint style="info" %}
The`segmentation_bitmap_url`refers to a 32-bit RGBA png image which contains the segmentation masks. The alpha channel is set to 255, and the remaining 24-bit values in the RGB channels correspond to the object ids in the `annotations` list. Because of the large dynamic range, these png images may appear black in an image viewer.

**When downloading a label**, you can use the utility function `utils.load_label_bitmap_from_url(url)` in the Python SDK to load the label bitmap as a numpy array containing object ids.

**When uploading a label**, the easiest way to transform a segmentation bitmap into this format and upload it is by using the util function`bitmap2file`:

```python
from segments.utils import bitmap2file

# segmentation_bitmap is a numpy array of type np.uint32, with values corresponding to instance_ids
file = bitmap2file(segmentation_bitmap)
asset = client.upload_asset(file, "label.png")
segmentation_bitmap_url = asset["url"]
```

For a full example of uploading model-generated labels to Segments.ai, please refer to [this blogpost](https://segments.ai/blog/speed-up-image-segmentation-with-model-assisted-labeling).
{% endhint %}

### Vector labels (bounding box, polygon, polyline, keypoint)

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```javascript
{
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, // the object id
      "category_id": 1, // the category id
      "type": "bbox", // refers to the annotation type (bounding box)
      "points": [
        [12.34, 56.78], // x0, y0 (upper left corner of bbox)
        [90.12, 34.56]  // x1, y1 (lower right corner of bbox)
      ]
    },
    {
      "id": 2,
      "category_id": 2,
      "type": "polygon", // refers to the annotation type (polygon)
      "points": [
        [12.34, 56.78], // x0, y0 (starting point of the polygon)
        [90.12, 34.56], // x1, y1
        [78.91, 23.45], // x2, y2
        [67.89, 98.76], // x3, y3
        [54.32, 10.01]  // x4, y4
      ]
    },
    {
      "id": 3, 
      "category_id": 3,
      "type": "polyline", // refers to the annotation type (polyline)
      "points": [
        [12.34, 56.78], // x0, y0 (starting point of the polyline)
        [90.12, 34.56], // x1, y1
        [78.91, 23.45], // x2, y2
        [67.89, 98.76], // x3, y3
        [54.32, 10.01]  // x4, y4
      ]
    },
    {
      "id": 4,
      "category_id": 4,
      "type": "point", // refers to the annotation type (keypoint)
      "points": [
        [12.34, 56.78] // x, y (coordinates of keypoint)
      ]
    },
  ],
}
```

## Image sequence

### Segmentation labels

Coming soon.

### Vector labels (bounding box, polygon, polyline, keypoint)

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```jsonp
{
  "format_version": "0.2",
  "frames": [
    { ... },
    { ... },
    { ... }
  ]
}
```

Where each frames object has the following format:

```jsonp
{
  "format_version": "0.1",
  "timestamp": "00001", // this field is only included if the sample has a timestamp
  "annotations": [
    {
      "id": 1, // the object id
      "category_id": 1, // the category id
      "track_id": 6, // this id is used to links objects across frame
      "is_keyframe": true, // whether this frame is a keyframe
      "type": "bbox", // refers to the annotation type (bounding box)
      "points": [
        [12.34, 56.78], // x0, y0 (upper left corner of bbox)
        [90.12, 34.56]  // x1, y1 (lower right corner of bbox)
      ]
    },
    {
      "id": 2,
      "category_id": 2,
      "track_id": 5, // this id is used to links objects across frame
      "is_keyframe": true, // whether this frame is a keyframe
      "type": "polygon", // refers to the annotation type (polygon)
      "points": [
        [12.34, 56.78], // x0, y0 (starting point of the polygon)
        [90.12, 34.56], // x1, y1
        [78.91, 23.45], // x2, y2
        [67.89, 98.76], // x3, y3
        [54.32, 10.01]  // x4, y4
      ]
    },
    {
      "id": 3, 
      "category_id": 3,
      "track_id": 4, // this id is used to links objects across frame
      "is_keyframe": true, // whether this frame is a keyframe
      "type": "polyline", // refers to the annotation type (polyline)
      "points": [
        [12.34, 56.78], // x0, y0 (starting point of the polyline)
        [90.12, 34.56], // x1, y1
        [78.91, 23.45], // x2, y2
        [67.89, 98.76], // x3, y3
        [54.32, 10.01]  // x4, y4
      ]
    },
    {
      "id": 4,
      "category_id": 4,
      "track_id": 3, // this id is used to links objects across frame
      "is_keyframe": true, // whether this frame is a keyframe
      "type": "point", // refers to the annotation type (keypoint)
      "points": [
        [12.34, 56.78] // x, y (coordinates of keypoint)
      ]
    },
  ],
}
```

## 3D point cloud

### Segmentation labels

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```json
{
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, // the object id
      "category_id": 1 // the category id
    },
    {
      "id": 2, 
      "category_id": 1
    },
    {
      "id": 3, 
      "category_id": 4
    }
  ],
  "point_annotations": [0, 0, 0, 3, 2, 2, 2, 1, 3...], // refers to object ids
}
```

### Cuboid labels

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```jsonp
{
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, // the object id
      "category_id": 1, // the category id
      "type": "cuboid", // refers to the annotation type (cuboid)
      "position": {
        "x": 0.0,
        "y": 0.2,
        "z": 0.5
      },
      "dimensions": {
        "x": 1.2,
        "y": 1,
        "z": 1
      },
      "yaw": 1.63
    }
  ]
}
```

## 3D point cloud sequence

### Segmentation labels

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```jsonp
{
  "format_version": "0.2",
  "frames": [
    { ... },
    { ... },
    { ... }
  ]
}
```

Where each frames object has the following format:

```jsonp
{
  "format_version": "0.2",
  "annotations": [
    {
      "id": 1, // the object id
      "category_id": 1, // the category id
      "track_id": 3 // this id is used to link objects across frames
    },
    {
      "id": 2, 
      "category_id": 1,
      "track_id": 4
    },
    {
      "id": 3, 
      "category_id": 4,
      "track_id": 5
    },
  ],
  "point_annotations": [0, 0, 0, 3, 2, 2, 2, 1, 3...], // refers to object ids
}
```

### Cuboid labels

Format of the `attributes` field in [`client.get_label()`](../../python-sdk.md#get-a-label):

```jsonp
{
  "format_version": "0.2",
  "frames": [
    { ... },
    { ... },
    { ... }
  ]
}
```

Where each frames object has the following format:

```jsonp
{
  "format_version": "0.2",
  "timestamp": "00001", // this field is only included if the sample has a timestamp
  "annotations": [
    {
      "id": 1, // the object id
      "category_id": 1, // the category id
      "type": "cuboid", // refers to the annotation type (cuboid)
      "position": {
        "x": 0.0,
        "y": 0.2,
        "z": 0.5
      },
      "dimensions": {
        "x": 1.2,
        "y": 1,
        "z": 1
      },
      "yaw": 1.63,
      "is_keyframe": true, // whether this frame is a keyframe
      "track_id": 6, // this id is used to links objects across frames
    },
    {
      "id": 2,
      "category_id": 2,
      "type": "cuboid",
      "position": {
        "x": 0.0,
        "y": 0.2,
        "z": 0.5
      },
      "dimensions": {
        "x": 1.2,
        "y": 1,
        "z": 1
      },
      "yaw": 1.63,
      "is_keyframe": false,
      "track_id": 7
    }
  ]
},
```

## Object attributes

Objects in the annotations list can optionally also contain an attributes field to store object-level attributes. Make sure to properly [configure the label editor](../../configure-label-editor.md) if you're using object-level attributes.

```javascript
{
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, 
      "category_id": 1,
      "attributes": { // object-level attributes
        "is_crowd": "1",
        "color": "red"
      }
    },
    {
      "id": 2, 
      "category_id": 1,
      "attributes": {
        "is_crowd": "0",
        "color": "blue"
      }
    },
    {
      "id": 3, 
      "category_id": 4,
      "attributes": {
        "is_crowd": "1",
        "color": "yellow"
      }
    }
  ],
  ...
}
```

## Image attributes

You can also define image-level attributes. These can be useful in image classification tasks. Make sure to properly [configure the label editor](../../configure-label-editor.md) if you're using image-level attributes.

```javascript
{
  "format_version": "0.1",
  "annotations": [...],
  "image_attributes": { // sample-level attributes
    "scene_type": "crossroads",
    "weather": "sunny"
  }
}
```
