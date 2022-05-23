# Sequences

A **sequence** is a sample comprised of multiple frames. Each frame represents a data point you want to label, such as an image or a 3D point cloud. Using sequences can help increase labeling speed and consistency when working with sequential data.

A sequence has a number of unique features:

* A track ID is assigned to each labeled object in a sequence. This track ID can be used to track an object over multiple frames. Learn how to use track IDs [here](../guides/use-the-labeling-interfaces/use-track-ids-in-sequences.md).
* A sequence is assigned to a single labeler. This can increase the consistency of the labels between the frames in the sequence.
* The image vector labeling interface and 3D point cloud cuboid interface allow you to use keyframe interpolation. This reduces the number of frames you need to label manually, which can decrease the labeling time significantly. Learn how to use keyframe interpolation [here](../guides/use-the-labeling-interfaces/use-keyframe-interpolation.md).

### Keyframes and remove-keyframes

In the context of interpolation, a **keyframe** is a marker that indicates that at that frame, the state of the object is defined by the user. In other frames (that are not keyframes), the state of the object label is calculated automatically through interpolation.&#x20;

A **remove-keyframe** is a visual indication of where an object was removed from the sample. A remove-keyframe means that the object is not present in that frame and all frames before the next normal keyframe.

![An example of keyframes (blue diamonds) and a remove-keyframe (grey circle with cross). The yellow color indicates the frames in which the object is present.](<../.gitbook/assets/image (25).png>)

