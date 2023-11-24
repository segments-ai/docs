# Image vector interface

{% hint style="info" %}
When [creating a dataset](https://sdkdocs.segments.ai/en/latest/client.html#create-a-dataset) through the Python SDK, choose `vector` or `image-vector-sequence` as the `task_type` to use this labeling interface.&#x20;
{% endhint %}

## Add a new object

To add a new object:

1. Select an annotation type (see [#annotation-types](image-vector-interface.md#annotation-types "mention"))
2. Label the object by drawing on the image&#x20;

## Select an object

1. Press `Space` or `Escape` or click the ![](<../../.gitbook/assets/image (31).png>) button in the left toolbar to enter view-and-select mode
2. Click on a labeled object to select it. You can also select an object by selecting it in the right sidebar

## Remove an object

Select an object and press `Backspace` to remove it. You can also click the ![](<../../.gitbook/assets/image (9) (1).png>) icon in the sidebar to remove an object.

## Change the category of an object

Select an object and click on its name in the sidebar to select a different category. You can also use hotkey `c` to change the category of the active object.

## Annotation types

### Bounding box

Click the![](<../../.gitbook/assets/image (21).png>)button in the left toolbar to draw a bounding box. Click and drag to draw the box.

### Polygon

Click the![](<../../.gitbook/assets/image (32).png>)button in the left toolbar to draw a polygon. Click on the image to draw polygon points. Double click or click the first point of the polygon to finish it.

After finishing a polygon, you can add a point to it with `Shift + left click`. This will add a point to the edge closest of the cursor. You will see a preview of where the point will be added as soon as you press `Shift`. You can add points to a selected polygon in _view-and-select_ mode, or while still in _draw polygon_ mode after finishing it. \
You can remove a point by `Shift + left click`. A polygon needs at least 3 points.

### Polyline

Click the![](<../../.gitbook/assets/image (30) (2).png>)button in the left toolbar to draw a polyline. Click on the image to draw polyline points. Double click to finish it.

After finishing a polyline, you can add a point to it with `Shift + left click`. This will add a point to the edge closest of the cursor. You will see a preview of where the point will be added as soon as you press `Shift`. You can add points to a selected polyline in _view-and-select_ mode, or while still in _draw polygon_ mode after finishing it.\
You can remove a point by `Shift + left click`. A polyline needs at least 2 points.

### Keypoint

Click the![](<../../.gitbook/assets/image (13).png>)button in the left toolbar to draw a keypoint.
