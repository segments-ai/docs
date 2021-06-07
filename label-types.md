# Label types

When downloading or uploading labels using the API or Python SDK, the format of the`attributes` field depends on the type of label. The different formats are described here.

## Segmentation masks

```javascript
"attributes": {
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, // this is an object id
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
The`segmentation_bitmap`url refers to a 32-bit RGBA png image which contains the segmentation masks. The alpha channel is set to 255, and the remaining 24-bit values in the RGB channels correspond to the object ids in the `annotations` list. Because of the large dynamic range, these png images may appear black in an image viewer.
{% endhint %}

## Bounding boxes

```javascript
"attributes": {
  "format_version": "0.1",
  "annotations": [
    {
      "id": 1, // this is an object id
      "category_id": 1, // this is a category id
      "type": "bbox", // this refers to the label type (bounding box)
      "points": [
        [12.34, 56.78], // x0, y0 (upper left corner of bbox)
        [90.12, 34.56]  // x1, y1 (lower right corner of bbox)
      ]
    },
    {
      "id": 2, 
      "category_id": 1,
      "type": "bbox",
      "points": [
        [12.34, 56.78],
        [90.12, 34.56]
      ]
    },
    {
      "id": 3, 
      "category_id": 4,
      "type": "bbox",
      "points": [
        [12.34, 56.78],
        [90.12, 34.56]
      ]
    }
  ],
}
```

## Object attributes

Objects in the annotations list can optionally also contain an attributes field to store object-level attributes. Make sure to properly [configure the label editor](configure-label-editor.md) if you're using object-level attributes.

```javascript
"attributes": {
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

You can also define image-level attributes. These can be useful in image classification tasks. Make sure to properly [configure the label editor](configure-label-editor.md) if you're using image-level attributes.

```javascript
"attributes": {
  "format_version": "0.1",
  "annotations": [...],
  "image_attributes": { // sample-level attributes
    "scene_type": "crossroads",
    "weather": "sunny"
  }
}
```

