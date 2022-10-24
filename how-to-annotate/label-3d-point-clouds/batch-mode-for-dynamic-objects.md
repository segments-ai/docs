# Batch mode (for dynamic objects)

When labeling or reviewing dynamic objects in 3D point cloud sequences, working object by object is usually the most efficient way to obtain precise annotations. However, this means navigating through the different frames in a sequence constantly. To make this process more efficient, we developed batch mode. Batch mode shows you an object in multiple frames at the same time. This way, you can easily choose where to make adjustments to label an object, and easily review an object by simply scrolling through the frames.

{% embed url="https://youtu.be/om5w69OErVs?t=121" %}
This video shows how you can use batch mode to quickly adjust a cuboid.
{% endembed %}

{% hint style="info" %}
Batch mode is only available for [3D tiles datasets](../../background/3d-tiles.md). \
[Contact us](https://segments.ai/contact) to enable 3D tiles for your point clouds!&#x20;
{% endhint %}

## Switch to the batch mode

1. Select the object you want to adjust/review.
2. Press the blue batch button in the bottom left.

## Exit batch mode

To exit batch mode, either:

* Click on the back arrow next to the track name at the top of the page
* Press the hotkey (`Escape` by default).

## Select a frame

Clicking somewhere in a frame to select the frame. If you want to select the previous or next frame, press the back or forward arrow, respectively.

## Zoom in/out

* Double-click a view to zoom in on that view.
* Press the hotkey (`Shift` by default) + double-click a view to zoom out on that view.

## Edit the object

Object editing works exactly in the same way as in the single frame interface, so you can still use your mouse or the hotkeys. See the following pages:

{% content-ref url="3d-point-cloud-cuboid-interface.md" %}
[3d-point-cloud-cuboid-interface.md](3d-point-cloud-cuboid-interface.md)
{% endcontent-ref %}

## Remove the object

1. Select the frame where you want to remove the object.
2. Press the trash icon on the left of the frame.

## Add the object to an empty frame

1. Select the empty frame where you want to add the object.
2. Press the plus icon on the left of the frame.

## Use keyframes

Keyframes work in the same way as in the single frame interface, see [use-keyframe-interpolation.md](../label-sequences-of-data/use-keyframe-interpolation.md "mention"). The only difference is that keyframes are now displayed directly next to the frame.
