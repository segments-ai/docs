# 3D interface settings

## Open the 3D interface settings

Click on the "Settings" tab in the sidebar on the right to open the 3D interface settings.

![](<../../.gitbook/assets/image (3).png>)

## View and customize hotkeys

Press the "Hotkeys" button to open the hotkey settings. See [customize-hotkeys.md](../customize-hotkeys.md "mention") for more information on how to customize the hotkeys.

## Object coloring mode

The object coloring toggle allows you to change how different objects in the sample are displayed.&#x20;

Click on a mode to change the object coloring mode.

#### **By instance**

Each object is displayed in a different color.

_E.g. two cars each get a different color._

#### By category

Each category has a color defined in the dataset settings (see [categories-and-task-attributes.md](../../reference/categories-and-task-attributes.md "mention")). Every object of the same category is displayed in that category color.

_E.g. two cars are displayed in the same category color (defined in the dataset settings)._&#x20;

## Point cloud display settings

### Change the size of the points

Drag the slider to adjust the point size.

### Toggle point cloud overlay on images

If you have uploaded one or more calibrated images along your point cloud, you can check the checkbox to choose whether the point cloud should be overlaid on the image in the image viewers.

See [upload-view-and-overlay-images.md](upload-view-and-overlay-images.md "mention") for more information on images in the 3D interfaces.

### Gradient coloring

Gradient coloring allows you to view your point cloud more clearly. Gradient coloring can be used to visualize the height of each point, or the intensity value of each point.

#### Enable height coloring

1. Check the "Gradient coloring" checkbox.
2. Choose "Height" in the "Gradient attribute" dropdown.
3. _Optional:_ Choose a gradient by clicking on the gradient and selecting one from the list. You can also reverse the gradient by checking the box under "Reverse".
4. _Optional:_ Set the minimum and maximum height between which the gradient is used. Press the reset button to set the range to include all the z-values of the current point cloud.

#### Enable intensity coloring

1. Upload a point cloud with intensity values. See [supported-file-formats.md](../../reference/sample-types/supported-file-formats.md "mention").
2. Check the "Gradient coloring" checkbox.
3. Choose "Height" in the "Gradient attribute" dropdown.
4. _Optional:_ Choose a gradient by clicking on the gradient and selecting one from the list. You can also reverse the gradient by checking the box under "Reverse".

### Change the point budget

{% hint style="warning" %}
This feature is deprecated. It is only available in the 3D point cloud vector interfaces for point clouds do not use 3D tiling.
{% endhint %}

The point budget controls the maximum number of points that are displayed. If the point cloud contains more points than the point budget, the point cloud will be randomly subsampled to limit the number of points.&#x20;

1. Click/hover over the dot icon in the toolbar on the right.
2. Enter the maximum amount of points in the point budget input box. If you want to remove the point budget, simply remove the value in the input box.

## Grid settings

### Square grid

Check the "Show square grid" checkbox to show a helper grid that is fixed to world coordinates.

### Concentric Circles grid

Check the "Show concentric circles grid" checkbox to show a circular helper grid that is attached to the [ego pose](../../reference/sample-types/#ego-pose).

## Panning settings

### Panning modes

Click on a panning mode to change how the camera pans in the 3D perspective view.&#x20;

#### Map panning

The camera pans along the ground plane.&#x20;

_E.g. when you pan up by clicking and dragging, or press `w`, the camera moves forwards._

#### Screen panning

The camera pans along the screen, i.e. along the camera plane.&#x20;

_E.g. when you pan up by clicking and dragging, or press `w`, the camera moves up._&#x20;

### Change the key pan speed

Drag the slider to adjust the key pan speed, i.e. the speed the camera moves when using keyboard panning.
