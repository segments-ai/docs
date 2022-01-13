# Main concepts

## Datasets, samples, and labels

Segments.ai is built around the concept of **datasets**. A dataset contains a collection of samples.

A **sample** is a data point you want to label, like an image, 3D point cloud, or a [sequence](main-concepts.md#undefined). The different sample types are defined [here](../reference/sample-and-label-types/).&#x20;

When you label a sample and press the save button, you've created a **label** for that sample. Labels also come in different [types](../reference/sample-and-label-types/) (segmentation labels, vector labels, cuboid labels, ...), with the available options determined by the sample type.

When you create a dataset, you have to choose the sample and label type. For example, _images_ with _segmentation labels_, or _3D point clouds_ with _cuboid labels_.

## Label sets

A label is linked to a sample in relation to a **label set**. When you label a sample and press the save button, the label is saved in the default _ground-truth_ label set.

You can optionally create additional label sets to [upload your model predictions](../guides/upload-model-predictions.md).

## Releases

A **release** is a snapshot of a dataset at a specific point in time. Create a new release if you want to [export your data](../export.md).

## Sequences

A **sequence** is a sample comprised of multiple frames. Each frame represents a data point you want to label, such as an image or a 3D point cloud. Using sequences can help increase labeling speed and consistency when working with sequential data.

A sequence has a number of unique features:

* A track ID is assigned to each labeled object in a sequence. This track ID can be used to track an object over multiple frames. Learn how to use track IDs [here](../guides/use-the-labeling-interfaces/use-track-ids-in-sequences.md).
* A sequence is assigned to a single labeler. This can increase the consistency of the labels between the frames in the sequence.
* The image vector labeling interface and 3D point cloud cuboid interface allow you to use keyframe interpolation. This reduces the number of frames you need to label manually, which can decrease the labeling time significantly. Learn how to use keyframe interpolation [here](../guides/use-the-labeling-interfaces/use-keyframe-interpolation.md).

### Keyframes and remove-keyframes

In the context of interpolation, a **keyframe** is a marker that indicates that at that frame, the state of the object is defined by the user. In other frames (that are not keyframes), the state of the object label is calculated automatically through interpolation.&#x20;

A **remove-keyframe** is a visual indication of where an object was removed from the sample. A remove-keyframe means that the object is not present in that frame and all frames before the next normal keyframe.&#x20;

![An example of keyframes (blue diamonds) and a remove-keyframe (grey circle with cross). The yellow color indicates the frames in which the object is present.](<../.gitbook/assets/image (25).png>)

