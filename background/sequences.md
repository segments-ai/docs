# Sequences

A **sequence** is a sample comprised of multiple frames. Each frame represents a data point you want to label, such as an image or a 3D point cloud. Using sequences can help increase labeling speed and consistency when working with sequential data.

A sequence has a number of unique features:

* A track ID is assigned to each labeled object in a sequence. This track ID can be used to track an object over multiple frames. Learn how to use track IDs [here](../how-to-annotate/label-sequences-of-data/use-track-ids-in-sequences.md).
* A sequence is assigned to a single labeler. This can increase the consistency of the labels between the frames in the sequence.
* The image vector labeling interface and 3D point cloud cuboid interface allow you to use keyframe interpolation. This reduces the number of frames you need to label manually, which can decrease the labeling time significantly. Learn how to use keyframe interpolation [here](../how-to-annotate/label-sequences-of-data/use-keyframe-interpolation.md).

### Keyframes and remove-keyframes

In the context of interpolation, a **keyframe** is a marker that indicates that at that frame, the state of the object is defined by the user. In other frames (that are not keyframes), the state of the object label is calculated automatically through interpolation.&#x20;

A **remove-keyframe** is a visual indication of where an object was removed from the sample. A remove-keyframe means that the object is not present in that frame and all frames before the next normal keyframe.

![An example of keyframes (blue diamonds) and a remove-keyframe (grey circle with cross). The yellow color indicates the frames in which the object is present.](<../.gitbook/assets/image (25) (1).png>)

## Timeline interface

The timeline is always visible at the bottom of the editor and provides a visual representation of all tracks and their states across the sequence.

### What the timeline shows

The timeline displays tracks as horizontal rows with:

* **Track information** on the left (track ID and category name)
* **Frame columns** showing the track's state across time
* **Visual indicators** for keyframes and object presence

### Visual indicators

| Element            | Appearance                | Meaning                                     |
| ------------------ | ------------------------- | ------------------------------------------- |
| Colored bar        | Continuous horizontal bar | Track is visible in these frames            |
| White diamond (◆)  | Icon on colored bar       | Keyframe (user-defined object state)        |
| White cross (×)    | Icon on blank space       | Remove-keyframe (object explicitly removed) |
| Highlighted column | Vertical highlight        | Active frame (current position)             |

### Timeline views

The timeline adapts to show different information:

**When no track is selected:**

* Switch between viewing all tracks or scene attributes using the View dropdown

**When a track is selected:**

* Shows only that track with its associated track attributes

This dynamic display helps you focus on relevant information while labeling.

### Attributes in the timeline

The timeline can display two types of attributes:

**Scene attributes** - Properties that apply to the entire scene or individual frames:

* Example: Weather conditions, lighting, time of day
* Visible when no track is selected (Scene attributes view)

**Track attributes** - Properties specific to individual tracks:

* Example: Vehicle speed, object confidence score
* Visible when a track is selected

Attributes can be frame-level (changing per frame) or sequence-level (constant across frames).

{% hint style="info" %}
For detailed instructions on using the timeline interface, see Track timeline. For keyframe operations, see Use keyframe interpolation.
{% endhint %}
