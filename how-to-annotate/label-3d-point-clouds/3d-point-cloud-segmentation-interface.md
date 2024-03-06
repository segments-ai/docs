# 3D point cloud segmentation interface

{% hint style="info" %}
When [creating a dataset](https://sdkdocs.segments.ai/en/latest/client.html#create-a-dataset) through the Python SDK, choose `pointcloud-segmentation` or `pointcloud-segmentation-sequence` as the `task_type` to use this labeling interface.&#x20;
{% endhint %}

{% hint style="info" %}
Tip: [use your GPU in Chrome](https://segmentsai.notion.site/How-to-use-your-GPU-in-Chrome-2b95e19fb77c456c87f798013769a98a) to make sure the 3D point cloud interface runs smoothly.
{% endhint %}

## Create a new object

1. If another object is currently selected, first confirm the active object.
2. Select some points. Instantly, a new object is created and appears in the objects sidebar.

## Select points

### Select points using the depth brush tool

1. Select the depth brush tool by clicking on the brush icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. When hovering over points, the points in the depth range of the brush will be highlighted, and the points outside the brush will be darkened.
3. Click or click and drag in any view to select the points in the depth range of the brush.

### Select points using the polygon tool

1. Select the polygon tool by clicking on the polygon icon in the toolbar on the left, or by pressing the hotkey (`g` by default).
2. Click in one of the views to place the first polygon point and start drawing the polygon.
3. Click to add additional points (connected by a straight line) or click and drag to add a line that follows your mouse path.
4. To close the polygon, either:
   * Double-click the last point
   * Click on the first point (indicated by a square)
   * Press the hotkey (`Enter` by default)

### Select points using the box tool

1. Select the box tool by clicking on the rectangle icon in the toolbar on the left, or by pressing the hotkey ( `m` by default).
2. Click and drag in one of the views to draw a box. When you release your mouse click, the points in the box will be selected.

## Deselect points

1. Activate one of the selection tools.
2. To deselect points, either:
   * Click on the eraser icon in the left toolbar, and then use the selection tool. The newly selected points will now be removed from the active object.
   * Use the selection tool, and hold the shortcut (`e` by default) to remove points from the active object.

## Remove an object

1. Select the object you want to remove.
2. Press the hotkey (`Backspace` by default) or click the trash icon next to the object in the objects sidebar on the right.

## Select an object

#### Using the "View and select" tool

1. Select the "View and select" tool by clicking on the cursor icon in the toolbar on the left, or use the hotkey (`Esc` by default).
2. Click on a point of the object in any view.

#### Using the objects sidebar

1. Click on the object in the objects sidebar to select it.

## Confirm the active object

Press the hotkey (`Space` by default), or select another object.

## Change the category of a**n object**

#### Using the category dropdown

1. Select the object.
2. Open the category dropdown by clicking on the category name in the objects sidebar on the right, or by pressing the hotkey (`c` by default).
3. Select a category by clicking on the desired category, or by using the arrow keys and pressing `Enter` to confirm.

#### Using the category hotkey

1. Select the object.
2. Press the hotkey of the desired category (`1` - `9`).

## Change the brush size

1. Select the depth brush tool by clicking on the brush icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Drag the brush size slider in the toolbar on the left, or use the hotkey (`Ctrl/cmd + scroll` by default).

## Change the brush depth

1. Select the depth brush tool by clicking on the brush icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Drag the brush depth slider in the toolbar on the left, or use the hotkey (`Ctrl/cmd + Shift + scroll` by default).

## Use the lock mode

When the lock mode is enabled, you cannot select points that are already part of another object.

To toggle the lock mode:

1. Activate one of the selection tools.
2. Click the lock icon in the toolbar on the left, or use the shortcut (`r` by default) to toggle the lock mode.

## Cycle between objects/ select the next object

Press the hotkey (`Tab` by default).

## Use the limiting cuboid

The limiting cuboid can be used to limit the point cloud to an (oriented) bounding box. Only points in the cuboid can be edited.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>The limiting cuboid is shown as a yellow cuboid with red outlines and includes the whole point cloud by default.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption><p>Adjust the limiting cuboid to determine which part of the point cloud will be shown.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption><p>The resulting point cloud view. Only the visible points can be edited.</p></figcaption></figure>

### Limit the point cloud to an oriented bounding box

1. Show the limiting cuboid by clicking on the cuboid icon (![](<../../.gitbook/assets/image (47).png>)) in the toolbar on the right.
2. Adjust the cuboid:
   * Adjust the cuboid dimensions by clicking and dragging a face of the cuboid.
   * Rotate the cuboid by clicking and dragging the red rotation plane attached to the cuboid.
   * Translate the cuboid freely by clicking and dragging the yellow cube in the middle of the cuboid. \
     Hover over the yellow cube in the middle to see the translation axes. Click and drag on an axis to translate the cuboid along the selected axis.
3. Apply the changes by clicking on the cuboid icon again or by selecting any of the segmentation tools in the toolbar on the left.&#x20;

{% hint style="info" %}
In [interface layout presets 1 and 5](3d-interface-settings.md#description-of-the-layout-presets), you can also adjust the limiting cuboid in the side, top, and back views.
{% endhint %}

### Limit the height of the point cloud

1. Show the limiting cuboid by clicking on the cuboid icon (![](<../../.gitbook/assets/image (47).png>)) in the toolbar on the right.
2. Adjust the min/max values in the sidebar on the right.
3. Apply the changes by clicking on the cuboid icon again or by selecting any of the segmentation tools in the toolbar on the left.&#x20;

### Reset the limiting cuboid

1. Show the limiting cuboid by clicking on the cuboid icon (![](<../../.gitbook/assets/image (47).png>)) in the toolbar on the right.
2. Click on the "Reset limiting cuboid" button located at the center-top of the interface.
3. Apply the changes by clicking on the cuboid icon again or by selecting any of the segmentation tools in the toolbar on the left.&#x20;
