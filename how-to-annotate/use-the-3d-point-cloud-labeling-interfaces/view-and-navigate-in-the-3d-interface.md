# View and navigate in the 3D interface

## Move the camera

Hold the hotkey (`Ctrl/cmd` by default) and click and drag, or simply click and drag the right mouse button.

#### Only in the perspective view

* Use the keyboard navigation (by default: `w` to move forward, `a` to move left, `s` to move backward, `d` to move right, `Shift + W` to move up, `Shift + S` to move down).

## Rotate/orbit the camera in the perspective view

Hold the hotkey (`Shift` by default) and click and drag.

## Zoom to an object

1. Select the object.
2. Press the hotkey (`t` by default).

## Pan to a bird's eye view in the perspective view

Press the hotkey (`Ctrl/cmd + b` by default).

## Enable intensity coloring

1. Upload a point cloud with intensity labels.
2. Click/hover over the sun icon in the toolbar on the right and select "Enable intensity coloring".
3. _Optional:_ Choose a gradient by clicking on the gradient and selecting one from the list. You can also reverse the gradient by checking the box under "Reverse".

## Change the size of the points

1. Click/hover over the dot icon in the toolbar on the right.
2. Drag the slider to adjust the point size.

## Change the point budget

If you are labeling a point cloud with a large number of points (> 500K) and you notice lag when navigating around the point cloud, you can choose to change the point budget. The point budget controls the maximum number of points that are displayed. If the point cloud contains more points than the point budget, the point cloud will be randomly subsampled to limit the number of points.&#x20;

1. Click/hover over the dot icon in the toolbar on the right.
2. Enter the maximum amount of points in the point budget input box. If you want to remove the point budget, simply remove the value in the input box.

{% hint style="info" %}
This feature is only available in the 3D point cloud cuboid interface.
{% endhint %}

## Change the key pan speed

1. Click/hover over the tachometer icon in the toolbar on the right.
2. Drag the slider to adjust the key pan speed, i.e. the speed the camera moves when using keyboard navigation.

## Open the synced images window

If you uploaded one or more [camera images](../../reference/sample-types/#camera-image) to your sample, you can view them in a separate window.

* To open the synced images window, click on the image icon (with an arrow) in the right toolbar.
* To zoom in on a synced image, double-click the image.&#x20;
* To move the zoomed-in image, click and drag on the image.&#x20;
* To reset the zoom of an image, double-click the image again.

## Display a camera image behind the point cloud

If you uploaded one or more **calibrated** [camera images](../../reference/sample-types/#camera-image) to your sample, you can display a calibrated camera image behind the point cloud in the main point cloud viewer.

1. Open the synced images window.
2. Hover over the image you want to display in the main viewer. A camera button pops up in the top right of the image.
3. Press the camera button.

## Change a side view

1. Click the dropdown in the top right corner of the side view.
2. Select the new view you want to change to.

{% hint style="info" %}
This feature is only available in the 3D point cloud segmentation interface.
{% endhint %}
