# Main concepts

## Datasets, samples, and labels

Segments.ai is built around the concept of **datasets**. A dataset contains a collection of samples.

A **sample** is a data point you want to label, like an image, 3D point cloud, or video. The different sample types are defined [here](../reference/sample-and-label-types/).&#x20;

When you label a sample and press the save button, you've created a **label** for that sample. Labels also come in different [types](../reference/sample-and-label-types/) (segmentation labels, vector labels, cuboid labels, ...), with the available options determined by the sample type.

When you create a dataset, you have to choose the sample and label type. For example, _images_ with _segmentation labels_, or _3D point clouds_ with _cuboid labels_.

## Label sets

A label is linked to a sample in relation to a **label set**. When you label a sample and press the save button, the label is saved in the default _ground-truth_ label set.

You can optionally create additional label sets to [upload your model predictions](../guides/upload-model-predictions.md).

## Releases

A **release** is a snapshot of a dataset at a specific point in time. Create a new release if you want to [export your data](../guides/export.md).
