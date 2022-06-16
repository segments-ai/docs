# Use track IDs in sequences

A **track ID** is an identifier assigned to each labeled object in a [sequence](../../background/sequences.md). This track ID can be used to track an object over multiple frames.

![](<../../.gitbook/assets/image (24) (1) (1).png>)

### View the track ID of an object

1. Select the object.
2. The track ID of the selected object is now visible in the bottom-right corner, next to the timeline.&#x20;

### Add a track ID to an object

When creating an object in a sequence editor, a track ID is automatically created.

### Change the track ID of an object (in all frames)

1. Select the object.
2. Click the pencil button next to the track ID.
3. Enter the new track ID.
4. Press the checkmark button next to the track ID to set the new track ID. The new track ID will replace the old track ID in all frames.

{% hint style="warning" %}
You cannot change the track ID to a track ID that is already used by another object in the current frame.
{% endhint %}

### Remove a track / remove an object in all frames

1. Select the object.
2. Click the "Remove track" button under the track ID. The object will then be removed from all frames.

### Enable same-dimensions track constraint

The same-dimensions track constraint forces objects to maintain the same dimensions in every frame. When changing the dimensions of an object with a certain track ID in one frame, the dimensions of the object will be updated in all other frames too. This can be useful when you want objects to keep their dimensions, regardless of occlusions or noise.

{% hint style="info" %}
The same-dimensions track constraint is only available for cuboid sequences.
{% endhint %}

You can enable the same-dimensions track constraint as follows:

1. Open the dataset where you want to activate the constraint.
2. Open the "Settings" tab.
3. Click on the "Labeling" section.
4. Tick the "Enable same-dimensions track constraint" checkbox.
5. Save the labeling settings.

