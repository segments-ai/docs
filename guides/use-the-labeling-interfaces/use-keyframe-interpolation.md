# Use keyframe interpolation

**Keyframe interpolation** is the process of creating intermediate values between a set of keyframes. The keyframes are specified by you and then the values in the frames between the keyframes are automatically filled in.

In Segments.ai, keyframe interpolation is used for object labels that change over time. For example, in a sequence with a moving car, the bounding box around the car moves in each frame. With keyframe interpolation, you only need to specify the label at certain key times, and the intermediate labels will be created automatically.

{% hint style="info" %}
Keyframe interpolation is enabled for 2D bounding box labels, and for 3D cuboid labels.&#x20;
{% endhint %}

### View the keyframes of an object

In the context of interpolation, a **keyframe** is a marker that indicates that at that frame, the state of the object is defined by the user. In other frames (that are not keyframes), the state of the object label is calculated automatically through interpolation.&#x20;

1. Select the object.
2. The keyframes are now visible in the timeline at the bottom of the editor. A normal keyframe is shown as a blue diamond under the frame it belongs to.

![](<../../.gitbook/assets/image (22).png>)

### Add a keyframe

#### In the current frame

1. Select the object.
2. Make a change to the object in the editor. A keyframe containing the new changes is added automatically.

#### In a different frame

1. Select the object.
2. In the timeline, double-click the space under the frame where you want to add a keyframe. The keyframe captures the state of the object label at that frame. This means the object will not change.

### Move a keyframe

1. Select the object.
2. In the timeline, click and drag the keyframe. When you release your mouse, the changes will be applied and the interpolation will be recalculated.

### Remove a keyframe

1. Select the object.
2. In the timeline, click the keyframe you want to remove.
3. Press the `Backspace` key to remove the keyframe. The interpolation will be recalculated immediately.

### View the remove-keyframes of an object

A remove-keyframe is a visual indication of where an object was removed from the sample. A remove-keyframe means that the object is not present in that frame and all frames before the next normal keyframe.&#x20;

1. Select the object.
2. The delete-keyframes are now visible in the timeline at the bottom of the editor. A delete-keyframe is indicated as a grey circle with a cross.

![](<../../.gitbook/assets/image (23).png>)

### Add a remove-keyframe

1. Select the object.
2. Remove the object from the current frame (see [Use the labeling interfaces](./)). A remove-keyframe is added automatically.

### Move a remove-keyframe

1. Select the object.
2. In the timeline, click and drag the remove-keyframe. When you release your mouse, the changes will be applied.

### Remove a remove-keyframe

1. Select the object.
2. In the timeline, click the remove-keyframe you want to remove.
3. Press the `Backspace` key to remove the remove-keyframe. The interpolation will be recalculated immediately.
