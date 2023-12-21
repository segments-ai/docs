# View and navigate in the 3D interface

{% hint style="info" %}
Tip: [use your GPU in Chrome](https://segmentsai.notion.site/How-to-use-your-GPU-in-Chrome-2b95e19fb77c456c87f798013769a98a) to make sure the 3D point cloud interface runs smoothly.
{% endhint %}

## Pan/move the camera

Hold the hotkey (`Ctrl/cmd` by default) and click and drag, or simply click and drag the right mouse button.

### Key panning (only in the perspective view)

Use hotkeys (`w`, `a`, `s`, `d`, `Shift + W`, `Shift + S` by default) to move the camera.

Change the key pan speed in the [3D interface settings](3d-interface-settings.md#change-the-key-pan-speed).

### Panning modes

By default, **map panning** is enabled, which means the camera pans along the ground plane. E.g. when you pan up by clicking and dragging, or press `w`, the camera moves _forwards_.

When **screen panning** is enabled, the camera moves along the screen (i.e. along the camera plane). E.g. when you pan up by clicking and dragging, or press `w`, the camera moves _up_.&#x20;

You can change the panning mode in the [3D interface settings](3d-interface-settings.md#panning-modes).

## Rotate/orbit the camera in the perspective view

Hold the hotkey (`Shift` by default) and click and drag.

### Change the rotation center point

* The rotation point is initialized at the center of the point cloud.&#x20;
* If you [zoom to an object](view-and-navigate-in-the-3d-interface.md#zoom-to-an-object), the rotation point will move to the center of that object.&#x20;
* You can manually set the rotation point by middle-clicking on any point of the point cloud. The changed rotation point will then be visible for a short time.

## Zoom in/out

#### Mouse wheel

Scroll using the mouse wheel to zoom in/out.

#### Double-click (only in orthographic views)

* Double-click in the viewer to zoom in.
* Press the hotkey (`Shift` by default) + double-click in the viewer to zoom out.

## Zoom to an object

1. Select the object.
2. Press the hotkey (`t` by default).

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

## Open/close camera view

Press the hotkeys `0-9` to open a certain camera view (numbered left to right). Press the same number key or `esc` to close the camera view again.

## Switch the main view to an orthographic top view

Click on the camera icon (![](<../../.gitbook/assets/image (6).png>)) in the toolbar on the right, or press the hotkey (`v` by default).&#x20;

{% hint style="info" %}
This feature is only available in the 3D point cloud cuboid and vector interface.
{% endhint %}

## Change a side view

1. Click the dropdown in the top right corner of the side view.
2. Select the new view you want to change to.

{% hint style="info" %}
This feature is only available in the 3D point cloud segmentation interface.
{% endhint %}

## Ruler mode

1. Click on the ruler icon (![](<../../.gitbook/assets/image (35).png>)) in the toolbar on the right, or press the hotkey (`z` by default).
2. Click on the ground plane to starting point.
3. When you move your cursor to another point on the ground plane the distance measurement will be shown in the bottom right panel of the sidebar. This measurement is in meters if the scale of your point cloud is true to life.
4. Click again to go back to "Select and edit" tool or press `Esc`.
