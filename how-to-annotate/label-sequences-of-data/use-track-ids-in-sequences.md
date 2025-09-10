# Use track IDs in sequences

A **track ID** is an identifier assigned to each labeled object in a [sequence](../../background/sequences.md). This track ID can be used to track an object over multiple frames.

## View the track ID of an object

The track ID of an object is displayed:

* in the sidebar on the left of the object category
* at the left of its category name in the timeline

## Add a track ID to an object

When creating an object in a sequence editor, a track ID is automatically created.

The track ID will always increment with 1 starting from the highest track ID.

## Change the track ID of an object (in all frames)

1. Select the object.
2. In the timeline, right click on the track bar to open the contextual menu
3. Select the `Update track id` option
4. Enter the new track ID.
5. Click on merge. The new track ID will replace the old track ID in all frames.

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-28 at 11.43.21.png" alt=""><figcaption><p>Track contextual menu in the timeline</p></figcaption></figure>



## Merge a track into another track

1. Select the object you want to merge into another track.
2. In the timeline, right click on the track bar to open the contextual menu
3. Select the `Update track id` option
4. Enter the ID of the track you want to merge the current track into.
5. Click on merge. The keyframes of both tracks will be combined, and the combined track takes the track ID you just entered.

{% hint style="warning" %}
Merging tracks is only possible when both tracks have no overlapping keyframes.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-28 at 11.44.11.png" alt=""><figcaption><p>Update and merge track id view</p></figcaption></figure>

## Remove a track (= remove an object in all frames)

1. Select the object you want to remove from the sequence.
2. In the timeline, right click on the track bar to open the contextual menu
3. Select the `Remove track` option. The object will then be removed from all frames.

If the track ID of the removed track was the highest track ID, then this track ID will be recovered for newly created objects. If the track ID was not the highest track ID, then the track ID will not be recovered when creating new objects, unless explicitly adjusted by the user (see [#change-the-track-id-of-an-object-in-all-frames](use-track-ids-in-sequences.md#change-the-track-id-of-an-object-in-all-frames "mention"))

## Split a track

Splitting a track will create a new track at the current frame and move all keyframes after the current frame to the new track.

1. Select the object whose track you want to split.
2. Select the frame where you want the new track to start.&#x20;
3. Click the "Split track" button under the track ID in the track editor on the right of the timeline.

{% hint style="warning" %}
Splitting a track is only possible if there are keyframes before the current frame. Otherwise, splitting the track would create an empty track.
{% endhint %}

## Enable same-dimensions track constraint

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

