# Main concepts

## Dataset

Segments.ai is built around the concept of **datasets**. A dataset contains a collection of samples.

When you create a dataset, you have to choose the sample and label type. For example, _images_ with _segmentation labels_, or _3D point clouds_ with _cuboid labels_.

## Sample

A **sample** is a data point you want to label, like an image, 3D point cloud, or a [sequence](sequences.md). The different sample types are defined in [sample-types](../reference/sample-types/ "mention").

## Label

When you label a sample and press the save button, you've created a **label** for that sample. Labels also come in different types (segmentation labels, vector labels, cuboid labels, ...), with the available options determined by the sample type. The different label types are specified in [label-types.md](../reference/label-types.md "mention").

## Label set

A **label** is linked to a sample in relation to a **label set**. When you label a sample and press the save button, the label is saved in the default _ground-truth_ label set.

You can optionally create additional label sets to [upload your model predictions](../how-to-integrate/upload-model-predictions.md).

## Release

A **release** is a snapshot of a dataset at a specific point in time. Create a new release if you want to [export your data](../how-to-integrate/export/).
