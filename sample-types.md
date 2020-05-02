# Sample types

## Image

A single image .

{% code title="Sample type: IMAGE" %}
```javascript
{
    "image_url": "https://example.com/image.png"
}
```
{% endcode %}

| Field | Description |
| :--- | :--- |
| image\_url | A link to a valid image file. |

### Task types

#### Segmentation \(bitmap\)

A segmentation task where labels are represented as pixels. Includes semantic, instance and panoptic segmentation.

{% code title="Task type: SEGMENTATION\_BITMAP" %}
```bash
{
    "segmentation_bitmap_url": "https://example.com/bitmap.png"
    "objects": [
        {
            "instance_id": 1,
            "category_id": 2,
        },
        {
            "instance_id": 2,
            "category_id": 3,
        },
    ]
}
```
{% endcode %}





