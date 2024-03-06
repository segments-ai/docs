# 3D interface settings

## Open the 3D interface settings

Click on the "Settings" tab in the sidebar on the right to open the 3D interface settings.

![](<../../.gitbook/assets/image (3).png>)

## View and customize hotkeys

Press the "Hotkeys" button to open the hotkey settings. See [customize-hotkeys.md](../customize-hotkeys.md "mention") for more information on how to customize the hotkeys.

## Interface layout presets

The interface layout presets allow you to change the layout of the point cloud and image viewers. The preset you picked will be remembered within the dataset type.

### Description of the layout presets

1. This layout contains a large main viewer and below it a top view and a synced image viewer (when calibrated images are present). When selecting a cuboid or vector, the top view splits into a side, top, and back view which are placed in a row. _Default for cuboid datasets._
2. This layout contains a large main viewer and below it a top view, back view, and a synced image viewer (when calibrated images are present). In segmentation datasets, the top and back view can be switched to other perspectives.
3. This layout contains a large main viewer and a synced image viewer in the bottom right (when calibrated images are present). _Default for vector and segmentation datasets._
4. This layout contains a large main viewer, a top view in the bottom left, and a synced image viewer in the bottom right (when calibrated images are present).
5. This layout contains a large main viewer and right of it a top view and a synced image viewer (when calibrated images are present). When selecting a cuboid or vector, the top view splits into a side, top, and back view which are placed in a column.

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

### Invert selection point color (segmentation datasets only)

If the default color doesn't contrast enough with the background while selecting points, you can toggle this checkbox to invert the color.

### Gradient coloring

Gradient coloring allows you to view your point cloud more clearly. Gradient coloring can be used to visualize the height of each point, or the intensity value of each point.

#### Enable height coloring

1. Check the "Gradient coloring" checkbox.
2. Choose "Height" in the "Gradient attribute" dropdown.
3. _Optional:_ Check the "Set min/max automatically" checkbox to automatically adjust the height range to the bounds of the current point cloud. Or unselect it and set the minimum and maximum height manually.
4. _Optional:_ Choose a gradient by clicking on the gradient and selecting one from the list. You can also reverse the gradient by checking the box under "Reverse".

#### Enable intensity coloring

1. Upload a point cloud with intensity values. See [supported-file-formats.md](../../reference/sample-types/supported-file-formats.md "mention").
2. Check the "Gradient coloring" checkbox.
3. Choose "Intensity" in the "Gradient attribute" dropdown.
4. _Optional:_ Choose a gradient by clicking on the gradient and selecting one from the list. You can also reverse the gradient by checking the box under "Reverse".

### Change the point budget

{% hint style="warning" %}
This feature is deprecated. It is only available in the 3D point cloud vector interfaces for point clouds that do not use 3D tiling.
{% endhint %}

The point budget controls the maximum number of points that are displayed. If the point cloud contains more points than the point budget, the point cloud will be randomly subsampled to limit the number of points.&#x20;

1. Click/hover over the dot icon in the toolbar on the right.
2. Enter the maximum amount of points in the point budget input box. If you want to remove the point budget, simply remove the value in the input box.

## Camera settings

### Follow active object (cuboid/vector datasets only)

Check the "Follow active object" checkbox to make your camera follow the active cuboid/vector through the sequence.

### Change the key pan speed

Drag the slider to adjust the key pan speed, i.e. the speed the camera moves when using keyboard panning.

### Toggle calibrated camera helpers

Check the "Show calibrated camera helpers" to show a camera helper for each calibrated camera in the scene. When the "Show calibrated camera helpers" is checked, you will see a list of the calibrated cameras in the scene. To disable the camera helper of a calibrated camera, untick the checkbox next to the camera name. The camera name can be provided in the [camera image attributes](../../reference/sample-types/#camera-image). If no camera names are provided, the cameras are labeled as "Camera 1", "Camera 2", etc.

## Panning settings

### Panning modes

Click on a panning mode to change how the camera pans in the 3D perspective view.&#x20;

#### Map panning

The camera pans along the ground plane.&#x20;

_E.g. when you pan up by clicking and dragging, or press `w`, the camera moves forwards._

#### Screen panning

The camera pans along the screen, i.e. along the camera plane.&#x20;

_E.g. when you pan up by clicking and dragging, or press `w`, the camera moves up._&#x20;

## Helper objects settings

### Square grid

Check the "Show square grid" checkbox to show a helper grid that is fixed to world coordinates.

### Concentric circles grid

Check the "Show concentric circles grid" checkbox to show a circular helper grid that is attached to the [ego pose](../../reference/sample-types/#ego-pose).

### Ego-vehicle model

Check the "Show ego-vehicle model" checkbox to show a 3D model of a car that is attached to the [ego pose](../../reference/sample-types/#ego-pose). Note that the orientation of the model might not correspond to the rotation of the ego vehicle.&#x20;

### Show all cuboids in active track

Check the "Show all cuboids in active track" checkbox to show all cuboids across all frames in the sequence of the active track. On a keyframe, the cuboid box is orange, while on other frames, it is grey.

Click on a cuboid to jump to the frame of that cuboid.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

### Show trajectory line of active track

Check the "Show trajectory line in active track" checkbox to show the trajectory line of the active track across all frames in the sequence. The position of the cuboid at a certain frame is visualized as a circle, which is orange when the frame is a keyframe, and grey if it is not.

Click on the circle to jump to the frame where the cuboid is positioned at the circle's position.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

## Cuboid settings

### Opacity

Drag the slider to change the opacity of the cuboids in the view. This will change the opacity for all cuboids in the scene, including the active cuboid.
