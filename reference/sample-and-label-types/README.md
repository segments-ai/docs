# Sample and label types

A **sample** is a data point you want to label. Samples come in different types, like an image, a 3D point cloud, or a video sequence.

When you label a sample and press the save button, you've created a **label** for that sample. Labels also come in different types, with the available options determined by the sample type.

When uploading and downloading samples and labels using the [Python SDK](../python-sdk.md), you need to know the format of the sample type and label types you're working with. These formats are described here.

* [Image](sample-types.md#image)
  * [Segmentation labels](label-types.md#segmentation-labels)
  * [Vector labels (bounding box, polygon, polyline, keypoint)](label-types.md#vector-labels-bounding-box-polygon-polyline-keypoint)
* [Image sequence](sample-types.md#image-sequence)
  * Segmentation labels (coming soon)
  * Vector labels (coming soon)
* [3D point cloud](sample-types.md#3d-point-cloud)
  * [Segmentation labels](label-types.md#segmentation-labels-1)
  * [Cuboid labels](label-types.md#cuboid-labels)
* [3D point cloud sequence](sample-types.md#3d-point-cloud-sequence)
  * [Segmentation labels](label-types.md#segmentation-labels-2)
  * [Cuboid labels](label-types.md#cuboid-labels-1)

Extra:

* [Object attributes](label-types.md#object-attributes)
* [Image attributes](label-types.md#image-attributes)
