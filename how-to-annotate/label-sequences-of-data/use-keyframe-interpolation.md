# Use keyframe interpolation

**Keyframe interpolation** is the process of creating intermediate values between a set of keyframes. The keyframes are specified by you and then the values in the frames between the keyframes are automatically filled in.

In Segments.ai, keyframe interpolation is used for object labels that change over time. For example, in a sequence with a moving car, the bounding box around the car moves in each frame. With keyframe interpolation, you only need to specify the label at certain key times, and the intermediate labels will be created automatically.

{% hint style="info" %}
Keyframe interpolation is available for 2D bounding box labels, and for 3D cuboid labels.&#x20;
{% endhint %}

{% hint style="warning" %}
#### [Object attributes](../../reference/label-types.md#object-attributes) and interpolation

Editing an object-level attribute will create a new keyframe, and attribute values are copied between keyframes. This means that if you edit an object-level attribute, its value will be copied until the next existing keyframe.

If want to change an attribute of an object with existing keyframes, make sure to change the value on **all** necessary keyframes.
{% endhint %}

## View the keyframes of an object

In the context of interpolation, a **keyframe** is a marker that indicates that at that frame, the state of the object is defined by the user. In other frames (that are not keyframes), the state of the object label is calculated automatically through interpolation.&#x20;

1. Select the object.
2. The keyframes are visible in the timeline at the bottom of the editor. Each track is present or not in the current frame. A present track in a frame is represented by a colored bar.  A keyframe is shown as a white diamond icon on top of a colored bar for the corresponding frame.

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-26 at 11.47.19 (3).png" alt=""><figcaption></figcaption></figure>

## Add a keyframe

1. Select the object.
2. Make a change to the object in the editor. A keyframe containing the new changes is added automatically.

## Move a keyframe

1. Select the object.
2. In the timeline, click and drag the keyframe. When you release your mouse, the changes will be applied and the interpolation will be recalculated.

## Remove a keyframe

1. Select the object and a frame **where it contains a keyframe**.
2. Press the `Backspace` key to remove the keyframe. The interpolation will be recalculated immediately.

{% hint style="info" %}
When there exists only one keyframe, this keyframe cannot be removed.
{% endhint %}



## View the deleted-keyframes of an object

A deleted-keyframe is a visual indication of where an object was explicitly removed from the sample. A deleted-keyframe means that the object is not present in that frame and all frames before the next standard keyframe.

1. Select the object and a frame **where it contains no keyframe**.
2. The deleted-keyframes are visible in the timeline at the bottom of the editor. Each track is present or not in the current frame. A non-present track in a frame is represented by a blank dark space.  A deleted-keyframe is shown as a white cross icon on top of a blank space.



<figure><img src="../../.gitbook/assets/Screenshot 2025-08-26 at 11.56.24 (2).png" alt=""><figcaption></figcaption></figure>



## Add a deleted-keyframe

1. Select the object.
2. Remove the object from the current frame (see [Use the labeling interfaces](broken-reference)). A deleted-keyframe is added automatically.

## Move a deleted-keyframe

1. Select the object.
2. In the timeline, click and drag the deleted-keyframe. When you release your mouse, the changes will be applied.

## Remove a deleted-keyframe

1. Select the object.
2. In the timeline, click the deleted-keyframe you want to remove.
3. Press the `Backspace` key to remove the deleted-keyframe. The interpolation will be recalculated immediately.

## Label occluded objects

Sometimes an object might be occluded, in which case you might want the object to not be present in certain frames and reappear in other frames. There are several ways to obtain this.

One procedure is to ...

1. Label a cuboid
2. Adjust the cuboid on the first frame where it _reappears_. This will create a keyframe.
3. Remove the cuboid on the first frame where it _starts being occluded_. The removal will carry through to the next keyframe which is the first frame where it reappears.

Another procedure is to ...

1. Label a cuboid
2. Remove the cuboid in the first frame where it _starts being occluded_.
3. Label a _new_ cuboid in the first frame where it _reappears_
4. Change the track ID of the _new_ cuboid into the track ID of the initial cuboid. This will merge both cuboids together on a single track.



<figure><img src="../../.gitbook/assets/Screenshot 2025-08-28 at 11.36.43.png" alt=""><figcaption></figcaption></figure>
