# View and navigate in the 3D interface

{% hint style="info" %}
Tip: [use your GPU in Chrome](https://sixth-smell-48e.notion.site/How-to-use-your-GPU-in-Chrome-2b95e19fb77c456c87f798013769a98a) to make sure the 3D point cloud interface runs smoothly.
{% endhint %}

## Move/pan the camera

Hold the hotkey (`Ctrl/cmd` by default) and click and drag, or simply click and drag the right mouse button.

#### Only in the perspective view

* Use the keyboard navigation (by default: `w` to move forward, `a` to move left, `s` to move backward, `d` to move right, `Shift + W` to move up, `Shift + S` to move down).

## Rotate/orbit the camera in the perspective view

Hold the hotkey (`Shift` by default) and click and drag.

## Zoom in/out

To zoom in or out, scroll using the mouse wheel.

## Zoom to an object

1. Select the object.
2. Press the hotkey (`t` by default).

## Toggle map panning in the perspective view

When you pan the camera, the camera moves along the ground plane by default. If you disable map panning, the camera instead pans along the camera plane (i.e. moving the mouse up moves the point cloud up as well).

To toggle map panning, click on the map icon in the toolbar on the right.

## Set the rotation point

* The rotation point is initialized at the center of the point cloud.&#x20;
* If you [zoom to an object](view-and-navigate-in-the-3d-interface.md#zoom-to-an-object), the rotation point will move to the center of that object.&#x20;
* You can manually set the rotation point by middle-clicking on any point of the point cloud. The changed rotation point will then be visible for a short time.

## Hide objects

### Hide/show a single object

1. Hover over the object you want to hide/show in the objects sidebar.
2. Press the eye icon.

### Hide/show all unselected instances

Press the hotkey (`h` by default).

## Pan to a bird's eye view in the perspective view

Press the hotkey (`Ctrl/cmd + b` by default).

## Pan to initial camera view

Press the hotkey (`Ctrl/cmd + i` by default).

## Switch to an orthographic top view for the main view

Click on the camera icon in the toolbar on the right, or press the hotkey (`v` by default).&#x20;

{% hint style="info" %}
This feature is only available in the 3D point cloud cuboid and vector interface.
{% endhint %}

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

## Change a side view

1. Click the dropdown in the top right corner of the side view.
2. Select the new view you want to change to.

{% hint style="info" %}
This feature is only available in the 3D point cloud segmentation interface.
{% endhint %}
