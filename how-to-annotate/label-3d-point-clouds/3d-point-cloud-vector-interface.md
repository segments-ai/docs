---
cover: ../../.gitbook/assets/Screenshot 2024-03-08 at 13.20.32.png
coverY: 0
---

# 3D point cloud vector interface

{% hint style="info" %}
When [creating a dataset](https://sdkdocs.segments.ai/en/latest/client.html#create-a-dataset) through the Python SDK, choose `pointcloud-vector` or `pointcloud-vector-sequence` as the `task_type` to use this labeling interface
{% endhint %}

{% hint style="info" %}
Tip: [use your GPU in Chrome](https://segmentsai.notion.site/How-to-use-your-GPU-in-Chrome-2b95e19fb77c456c87f798013769a98a) to make sure the 3D point cloud interface runs smoothly.
{% endhint %}

## Create a new vector

You can create three types of vectors: a polygon, polyline, and a keypoint.

### Create a polygon

1. Select the "Create polygon" tool by clicking on the polygon icon in the toolbar on the left, or by pressing the hotkey (`g` by default).
2. Click in the perspective or orthographic view to add a point to the polygon (each click adds a new point).
3. Close the polygon by&#x20;
   1. double clicking (this adds a final point and closes the polygon) or by
   2. clicking on the first polygon point (this closes the polygon without adding a final point) or by
   3. confirming the object (hotkey `space` by default) - this closes the polygon without adding a final point.

When holding `Shift + F`node snapping is activated. This will snap the point you want to add to the nearest handle of an existing vector, within a certain distance threshold.

### Create a polyline

1. Select the "Create polyline" tool by clicking on the line icon in the toolbar on the left, or by pressing the hotkey (`n` by default).
2. Click in the perspective or orthographic view to add a point to the polyline (each click adds a new point).
3. Close the polyline&#x20;
   1. by double clicking (this adds a final point and finishes the polyline) or by
   2. confirming the object (press `space` hotkey by default) - this closes the polyline without adding a final point.

{% hint style="info" %}
It's possible to view the direction of a polyline on orthographic top views. To enable this, open the "Settings" tab, go to the "Helper objects" section and activate "Show polyline arrows".
{% endhint %}



### Create a point

* Select the "Create point" tool by clicking on the point icon in the toolbar on the left, or by pressing the hotkey (`p` by default).
* Click in the viewer to add a point.

## Remove a vector

1. Select the vector you want to remove.
2. Press the hotkey (`Backspace` by default) or click the trash icon next to the object in the objects sidebar on the right.

## Select a vector

### Using the "Select and edit" tool

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Click on the vector in any view.

### Using the objects sidebar

1. Click on the object in the objects sidebar to select it.

## Translate a vector

* **Polygon.** Hover over a polygon (the cursor changes to a "move cursor"). Click, hold and drag to move the polygon.&#x20;
* **Polyline.** Hover over a polyline (do not hover over the middle of a line segment, this adds a preview of a new polyline point - see [#add-a-point-to-a-vector](3d-point-cloud-vector-interface.md#add-a-point-to-a-vector "mention")). The cursor changes to a "move cursor". Click, hold and drag to move the polyline.
* **Point.** Hover over a point (the cursor changes to a "move cursor"). Click, hold and drag to move the point.

## Translate a vector point

Hover over a polygon point, a polyline point or a key point. The cursor changes to a "grab cursor". Click, hold and drag to move this point.

## Add a point to a vector

1. Select a polygon or polyline annotation.
2. Press `Shift` and move the mouse close to a line segment.
3. Click to add this point to the polygon or polyline.
4. Release `Shift` and move the point if necessary.

## Remove a point from a vector

1. Hover over keypoint or a polygon or polyline point.
2. Press `Shift` and click to remove the point.

## Change the category of a vector

### Using the category dropdown

1. Select the vector.
2. Open the category dropdown by clicking on the category name in the objects sidebar on the right, or by pressing the hotkey (`c` by default).
3. Select a category by clicking on the desired category, or by using the arrow keys and pressing `Enter` to confirm.

### Using the category hotkey

1. Select the vector.
2. Press the hotkey of the desired category (`1` - `9`).

## Cycle between vectors / select the next vector

Press the hotkey (`Tab` by default).
