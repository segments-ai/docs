# Use keyframe interpolation and extrapolation

Keyframe interpolation is the process of creating intermediate values between a set of keyframes. In Segments.ai, this technique applies to object labels that change across video frames, such as a moving car's bounding box. Users set labels at key moments, and the system automatically generates intermediate values.

{% hint style="info" %}
Keyframe interpolation is available for 2D bounding box labels and 3D cuboid labels. Keyframe extrapolation is available for 3D cuboid labels only.
{% endhint %}

## Understanding keyframes

A **keyframe** marks a frame where you've explicitly defined an object's state (position, size, rotation, etc.). Between keyframes, the system automatically interpolates the object's properties.

A **remove-keyframe** marks a frame where you've explicitly removed an object. It indicates the object is absent from that point until the next regular keyframe.

{% hint style="info" %}
Keyframes are managed through the timeline interface at the bottom of the editor. See Track timeline for details on the timeline interface.
{% endhint %}

## Extrapolate after the last keyframe

For 3D cuboid labels, keyframe extrapolation predicts an object's position after its last keyframe. It continues the motion defined by the last two keyframes at a constant speed and direction. This can help you label moving objects as you advance through a sequence.

Extrapolation is disabled by default. To enable it:

1. Open the dataset's **Settings** → **Labeling**.
2. Select **Enable keyframe extrapolation**.
3. Confirm the change and save the settings.

A track needs at least two keyframes with a defined position. With only one keyframe, its position stays constant. Extrapolation changes only the cuboid's center position; rotation, dimensions, and attributes retain their last values.

Review the predicted positions and adjust the cuboid when needed to create another keyframe. Add a [remove-keyframe](#add-a-deleted-keyframe) where the object disappears to stop extrapolation from that frame onward.

When **Use timestamps for interpolation and extrapolation** is enabled, motion is calculated using frame timestamps. Otherwise, it uses frame indices.

{% hint style="warning" %}
Enabling or disabling extrapolation can affect existing labels after their last keyframe. Review affected sequences after changing this setting. When disabled, cuboids stay at their last keyframe position.
{% endhint %}

## Object attributes and interpolation

{% hint style="warning" %}
Object-level attribute edits create new keyframes, with values copying between them. To modify attributes on objects with existing keyframes, you must update the value across **all necessary keyframes**.
{% endhint %}

## View the keyframes of an object

The **timeline** is always visible at the bottom of the editor and displays tracks across frames.

### Timeline views

The timeline content changes based on your selection and the active view:

**No track selected:**

* Use the **View dropdown** in the timeline header to switch between:
  * **Tracks view**: Displays all tracks with their visibility across frames
  * **Scene attributes view**: Displays scene-level attributes

**Track selected:**

* The timeline automatically shows the selected track with its track attributes below

### Keyframe indicators

Select a track in the viewer to see its keyframes in the timeline:

* **White diamond icons (◆)**: Mark frames with keyframes
* **White cross icons (×)**: Mark remove-keyframes
* **Colored bar**: Shows where the track is visible

{% hint style="info" %}
When you select a track in the viewer, the timeline automatically switches to show only that track with its attributes. The View dropdown is disabled while a track is selected.
{% endhint %}

## Add a keyframe

Keyframes are created automatically when you modify an object:

1. Select a track in the viewer
2. Navigate to a frame using the timeline navigation buttons or arrow keys
3. Modify the object (move, resize, rotate, change shape)
4. A keyframe is automatically created at that frame

{% hint style="info" %}
You don't need to manually create keyframes — they're added whenever you make changes to an object.
{% endhint %}

## Move a keyframe

Drag keyframes to different frames in the timeline:

1. Select a track in the viewer (timeline switches to show that track)
2. In the timeline, click and hold on a keyframe diamond (◆)
3. Drag it to the desired frame
4. Release to confirm — interpolation is automatically recalculated

{% hint style="info" %}
Keyframes can only be moved within the track's visibility range (where the colored bar appears).
{% endhint %}

## Remove a keyframe

Delete a keyframe to simplify your annotation:

1. Select a track in the viewer
2. Navigate to a frame with a keyframe
3. Press `Backspace`

The keyframe is removed and interpolation is recalculated based on the remaining keyframes.

{% hint style="warning" %}
A track must have at least one keyframe. When there exists only one keyframe, this keyframe cannot be removed.
{% endhint %}

## View the deleted-keyframes of an object

Remove-keyframes appear as white cross icons (×) on blank spaces in the timeline. They indicate frames where you've explicitly removed the object.

## Add a deleted-keyframe

Create a remove-keyframe to mark where an object disappears:

1. Select a track in the viewer
2. Navigate to the frame where the object should disappear
3. Press `Backspace`

The object is removed from that frame onward until the next keyframe.

## Move a deleted-keyframe

Drag remove-keyframes just like regular keyframes:

1. Select a track in the viewer
2. In the timeline, click and hold on a remove-keyframe cross (×)
3. Drag it to the desired frame
4. Release to confirm

## Remove a deleted-keyframe

Delete a remove-keyframe to restore object visibility:

1. Select a track in the viewer
2. Navigate to a frame with a remove-keyframe
3. Press `Backspace`

The object becomes visible again from that frame onward.

## Label occluded objects

Two approaches exist for objects that disappear and reappear:

1. **Adjust on reappearance:** Adjust the object on its reappearance frame (creating a keyframe), then remove it where occlusion begins.
2. **Remove and merge:** Remove the object where occlusion starts, label a new object where it reappears, then merge them by matching their track IDs. See Use track IDs - Merge tracks for details.

{% hint style="info" %}
For more information on managing tracks and navigating the timeline, see Track timeline.
{% endhint %}
