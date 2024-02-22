# Image segmentation interface

{% hint style="info" %}
When [creating a dataset](https://sdkdocs.segments.ai/en/latest/client.html#create-a-dataset) through the Python SDK, choose `segmentation-bitmap` as the `task_type` to use this labeling interface.&#x20;
{% endhint %}

{% hint style="info" %}
The image segmentation interface is a bitmap interface: the resulting label is an image containing object segmentation masks. If you need vector labels containing polygon, polyline, bounding box or keypoint coordinates, use the [image vector interface](image-vector-interface.md) instead.
{% endhint %}

{% embed url="https://www.youtube.com/watch?v=Y1JOCxXQLMg" %}

## Add a new object

To add a new object:

1. Select a drawing tool (see [#drawing-tools](image-segmentation-interface.md#drawing-tools "mention"))
2. Label the object by drawing on the image&#x20;
3. Press `Space` to confirm the object once you finished labeling

## Select an object

1. Press `Space` or `Escape` or click the ![](<../../.gitbook/assets/image (31).png>) button in the left toolbar to enter view-and-select mode
2. Click on a labeled object to select it. You can also select an object by selecting it in the right sidebar

## Remove an object

Select an object and press `Backspace` to remove it. You can also click the ![](<../../.gitbook/assets/image (9) (1).png>) icon in the sidebar to remove an object.

## Change the category of an object

Select an object and click on its name in the sidebar to select a different category. You can also use hotkey `c` to change the category of the active object.

## Drawing tools

{% hint style="info" %}
You can switch seamlessly between drawing tools while labeling
{% endhint %}

### Brush

1. Click the ![](<../../.gitbook/assets/image (1) (2).png>)button in the left toolbar or press `b` to select the brush tool
2. Change the brush size by adjusting the slider in the top left of the screen, or by scrolling your mouse wheel
3. Click and drag on the image to draw

### Polygon

1. Click the ![](<../../.gitbook/assets/image (4).png>)button in the left toolbar or press `p` to select the polygon tool
2. Click on the image to draw polygon points. You can also click and drag to draw free-form lines
3. Double click or click the first point of the polygon to finish it. The region within the polygon will now be annotated

### Superpixels

1. Click the![](<../../.gitbook/assets/image (8).png>)button in the left toolbar or press s to select the superpixel tool
2. Change the superpixel granularity by adjusting the slider in the top left of the screen, or by scrolling your mouse wheel
3. Click on a superpixel to select the corresponding region, or drag across multiple superpixels to select more than one at a time
4. Click a superpixel again to unselect the region

More info in [this blog post](https://segments.ai/blog/superpixels).

### Autosegment

1. Click the![](<../../.gitbook/assets/image (25).png>)button in the left toolbar or press `a` to select the autosegment tool
2. Draw a box around an object in the image through click and drag
3. The object within the box will be automatically segmented

More info in [this blog post](https://segments.ai/blog/autosegment).

### Hover-and-click

* Click the![](<../../.gitbook/assets/image (1) (1) (1) (1).png>)button in the left toolbar or press `d` to select the hover-and-click tool
* Hover with your mouse over the image to see mask suggestions appear
* Click to select a suggested mask

More info in [this blog post](https://segments.ai/blog/faster-labeling-with-meta-segment-anything-model).

## Erase and lock mode

* The object within the box will be automatically segmented

### Erase mode

When labeling in brush, polygon or autosegment mode, an eraser button ![](<../../.gitbook/assets/image (33).png>) will appear in the left toolbar. Click it or hold hotkey `e` to enable the erase mode.

### Lock mode

Click the![](<../../.gitbook/assets/image (2) (2).png>)button in the left toolbar or press hotkey `r` to toggle the lock mode. When lock mode is enabled, existing objects will not be affected when drawing over them.

## Ruler mode

1. Click the ![](<../../.gitbook/assets/image (35).png>)button in the right toolbar or press hotkey `z` to toggle the ruler mode
2. Click in the interface to set the first point
3. Move your cursor to another point and it will display the measurement in pixels
4. Click again to go back to select-and-view mode or press `esc`

