# Use track IDs in sequences

## Use track IDs in sequences

A track ID uniquely identifies an object across multiple frames in a sequence. Track IDs are essential for tracking applications where you need to follow the same object over time.

## Understanding track IDs

When you create an object in a sequence:

* A unique track ID is automatically assigned
* The track ID remains constant across all frames where the object exists
* Track IDs increment sequentially, starting from the highest existing ID

Track IDs are visible:

* In the **sidebar** next to the object category
* In the **timeline** at the left of each track row

{% hint style="info" %}
The timeline interface is described in detail in Track timeline.
{% endhint %}

## Update a track ID

Change a track ID across all frames:

1. In the timeline, right-click on the track row
2. Select **Update track ID**
3. Enter the new track ID in the dialog
4. Click **Update**

{% hint style="info" %}
Track IDs must be unique within the sequence. If you enter an existing ID, you'll be prompted to merge the tracks instead.
{% endhint %}

**Use case:** Fix incorrectly assigned track IDs or align with external tracking data.

## Merge tracks

Combine two tracks that represent the same object:

1. Right-click on the source track row in the timeline
2. Select **Merge with track**
3. Choose the target track ID from the dropdown
4. Confirm the merge

All keyframes from the source track are transferred to the target track, and the source track is removed.

{% hint style="warning" %}
**Important constraint:** Merging tracks is only possible when both tracks have no overlapping keyframes.
{% endhint %}

**Use case:** Correct tracking errors where the same object was accidentally assigned multiple track IDs.

## Split a track

Divide a track into two separate tracks at a specific frame:

1. Navigate to the frame where you want to split
2. Right-click on the track row in the timeline
3. Select **Split track**

The track is divided:

* Frames before the split point keep the original track ID
* Frames from the split point onward receive a new track ID

{% hint style="warning" %}
**Limitation:** Splitting a track is only possible if there are keyframes before the current frame.
{% endhint %}

{% hint style="info" %}
The **Split track** action is only available in single-sensor sequences.
{% endhint %}

**Use case:** Separate objects that were incorrectly tracked as one, or handle scenarios where one object becomes two (e.g., a vehicle splitting into two paths).

## Remove a track

Delete an entire track from the sequence:

1. Right-click on the track row in the timeline
2. Select **Remove track**
3. Confirm the deletion

{% hint style="warning" %}
This deletes all keyframes and annotations associated with the track. Use undo if you need to recover it.
{% endhint %}

{% hint style="info" %}
When a track is removed, the highest track ID becomes available for new objects. Lower IDs require manual adjustment if you want to reuse them.
{% endhint %}

## Same-dimensions constraint

For 3D cuboid sequences, you can enforce consistent object dimensions across all frames:

1. Go to **Settings** > **Labeling**
2. Enable the **Same-dimensions track constraint** checkbox

When enabled, all keyframes in a track will maintain the same object dimensions (width, height, depth), allowing only position and rotation changes between frames.

{% hint style="info" %}
**Note:** The same-dimensions track constraint is only available for cuboid sequences.
{% endhint %}

**Use case:** Label objects with known fixed dimensions (e.g., standard shipping containers, vehicles with known specifications).

{% hint style="info" %}
For more details on the timeline context menu and interface, see Track timeline.
{% endhint %}
