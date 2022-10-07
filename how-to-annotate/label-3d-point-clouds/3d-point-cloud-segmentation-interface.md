# 3D point cloud segmentation interface

{% hint style="info" %}
When [creating a dataset](../../python-sdk.md#create-a-dataset) through the Python SDK, choose `pointcloud-segmentation` or `pointcloud-segmentation-sequence` as the `task_type` to use this labeling interface.&#x20;
{% endhint %}

## Create a new object

1. If another object is currently selected, first confirm the active object.
2. Select some points. Instantly, a new object is created and appears in the objects sidebar.

## Select points

### Select points using the brush tool

1. Select the brush tool by clicking on the brush icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Click or click and drag in any view to select points.

### Select points using the polygon tool

1. Select the polygon tool by clicking on the polygon icon in the toolbar on the left, or by pressing the hotkey (`g` by default).
2. Click in one of the views to place the first polygon point and start drawing the polygon.
3. Click to add additional points (connected by a straight line) or click and drag to add a line that follows your mouse path.
4. To close the polygon, either:
   * Doubleclick the last point
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
3. Select a category by clicking on the desired category, **** or by using the arrow keys and pressing `Enter` to confirm.

#### Using the category hotkey

1. Select the object.
2. Press the hotkey of the desired category (`1` - `9`).

## Change the brush size

1. Select the brush tool by clicking on the brush icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Drag the brush size slider in the toolbar on the left, or use the hotkey (`Ctrl + scroll` by default).

## Use the lock mode

When the lock mode is enabled, you cannot select points that are already part of another object.

To toggle the lock mode:

1. Activate one of the selection tools.
2. Click the lock icon in the toolbar on the left, or use the shortcut (`r` by default) to toggle the lock mode.

## Cycle between objects/ select the next object

Press the hotkey (`Tab` by default).
