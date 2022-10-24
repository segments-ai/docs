---
description: >-
  This page describes some tips and tricks to label cuboids in point cloud
  sequences faster.
---

# Tips for labeling cuboid sequences

## General tips

### Label object by object

By labeling object by object, we mean first labeling an object in the whole sequence, before moving on to the next object. This is typically easier and faster than labeling all objects on the first frame, then all objects on the second frame, and so on.

### Use hotkeys for fine adjustments

Your mouse is perfectly suitable for quickly drawing a cuboid or for moving it to roughly the right position. However, for fine adjustments, you’re probably better off using your keyboard. Segments.ai has hotkeys for almost everything, including for [moving a cuboid](3d-point-cloud-cuboid-interface.md#translate-a-cuboid) and for [changing its dimensions](3d-point-cloud-cuboid-interface.md#change-the-dimensions-of-a-cuboid). Better still, you can customize all the hotkeys to your liking:

{% content-ref url="../customize-hotkeys.md" %}
[customize-hotkeys.md](../customize-hotkeys.md)
{% endcontent-ref %}

### Learn about keyframes and remove-keyframes

[Keyframe interpolation](../../background/sequences.md#keyframes-and-remove-keyframes) is enabled by default on point cloud sequences with cuboid annotations. It allows you to label a sequence perfectly by only labeling a few “key” frames, while the rest of the frames are completed automatically. On Segments.ai, there are also remove-keyframes that indicate when an object disappears. More precisely, a remove-keyframe means that the object is not present in that frame and all frames before the next normal keyframe.

You can learn about adding, moving, and removing keyframes on this page:

{% content-ref url="../label-sequences-of-data/use-keyframe-interpolation.md" %}
[use-keyframe-interpolation.md](../label-sequences-of-data/use-keyframe-interpolation.md)
{% endcontent-ref %}

## How to find objects

In order to find objects to label, you can use the main point cloud viewer. You can move through the interface either by using your mouse or the hotkeys (wasd by default). Learn more about navigating on the following page:

{% content-ref url="view-and-navigate-in-the-3d-interface.md" %}
[view-and-navigate-in-the-3d-interface.md](view-and-navigate-in-the-3d-interface.md)
{% endcontent-ref %}

If the point cloud sequence has images associated with it, they can often be helpful for locating objects that might otherwise be hard to spot in the point clouds. You can quickly [toggle the image viewer](view-and-navigate-in-the-3d-interface.md#view-synced-camera-images), or [open it in a new window](view-and-navigate-in-the-3d-interface.md#view-synced-camera-images) if you have two screens. When the images are properly calibrated, you can also [display an image directly behind the point cloud](view-and-navigate-in-the-3d-interface.md#display-a-camera-image-behind-the-point-cloud). That way, you can make sure that you’re labeling the correct object in the point cloud.

## How to label a static object

1. Go to the first frame where the static object is visible
2. [Toggle the merged point cloud](merged-point-cloud-view.md#toggle-the-merged-point-cloud-view) view if it is available
3. [Draw a cuboid](3d-point-cloud-cuboid-interface.md#create-a-new-cuboid) around the object
4. Disable the merged point cloud view
5.  Go through the sequence to find the frame where the object disappears

    Tip: you can use the [batch mode](batch-mode-for-dynamic-objects.md) for navigating through a sequence faster
6. [Remove the cuboid](3d-point-cloud-cuboid-interface.md#remove-a-cuboid) in the frame where the object disappears

## How to label a dynamic object

1. Go to the first frame where the static object is visible
2. [Draw a cuboid](3d-point-cloud-cuboid-interface.md#create-a-new-cuboid) around the object
3. Go through the sequence to find the last frame where the object is visible
4. [Move the cuboid](3d-point-cloud-cuboid-interface.md#translate-a-cuboid) to the correct position
5. [Remove the cuboid](3d-point-cloud-cuboid-interface.md#remove-a-cuboid) in the frame where the object disappears
6. [Open the batch mode](batch-mode-for-dynamic-objects.md#switch-to-the-batch-mode)
7. Adjust the object in the frames where the cuboid’s position is the farthest away from the real object’s position
8. When the sequence is roughly labeled, go through the sequence by using the arrow keys and make fine adjustments using keyboard hotkeys

## How to label a static object that starts moving

Labeling a static object that starts moving is basically the same as labeling a dynamic object. To label the static part, place a keyframe on the first frame where the object is static. Then add a keyframe to the last frame where the object is static ([by double-clicking under the frame](../label-sequences-of-data/use-keyframe-interpolation.md#in-a-different-frame)). This way, you make sure that the object remains static between the keyframes.
