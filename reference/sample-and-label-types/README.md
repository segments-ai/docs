# Sample and label types

A **sample** is a data point you want to label. Samples come in different types, like an image, a 3D point cloud, or a video sequence.

When you label a sample and press the save button, you've created a **label** for that sample. Labels also come in different types, with the available options determined by the sample type.

When uploading and downloading samples and labels using the [Python SDK](../../python-sdk.md), you need to know the format of the sample type and label types you're working with. These formats are described here.

| Sample type                                                        | Label type                                                                                                                       | Labeling interface                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| [Image](sample-types.md#image)                                     | [Segmentation labels](label-types.md#segmentation-labels)                                                                        | ``[`segmentation-bitmap`](../../guides/use-the-labeling-interfaces/image-segmentation-interface.md)``                       |
|                                                                    | [Vector labels (bounding box, polygon, polyline, keypoint)](label-types.md#vector-labels-bounding-box-polygon-polyline-keypoint) | ``[`vector`](../../guides/use-the-labeling-interfaces/image-vector-interface.md)``                                          |
| [Image sequence](sample-types.md#image-sequence)                   | [Segmentation labels](label-types.md#segmentation-labels-1)                                                                      | coming soon                                                                                                                 |
|                                                                    | [Vector labels (bounding box, polygon, polyline, keypoint)](label-types.md#vector-labels-bounding-box-polygon-polyline-keypoint) | ``[`image-vector-sequence`](../../guides/use-the-labeling-interfaces/image-vector-interface.md)``                           |
| [3D point cloud](sample-types.md#3d-point-cloud)                   | [Segmentation labels](label-types.md#segmentation-labels-2)                                                                      | ``[`pointcloud-segmentation`](../../guides/use-the-labeling-interfaces/3d-point-cloud-segmentation-interface.md)``          |
|                                                                    | [Cuboid labels](label-types.md#cuboid-labels)                                                                                    | ``[`pointcloud-cuboid`](../../guides/use-the-labeling-interfaces/3d-point-cloud-cuboid-interface.md)``                      |
| [3D point cloud sequence](sample-types.md#3d-point-cloud-sequence) | [Segmentation labels](label-types.md#segmentation-labels-3)                                                                      | ``[`pointcloud-segmentation-sequence`](../../guides/use-the-labeling-interfaces/3d-point-cloud-segmentation-interface.md)`` |
|                                                                    | [Cuboid labels](label-types.md#cuboid-labels-1)                                                                                  | ``[`pointcloud-cuboid-sequence`](../../guides/use-the-labeling-interfaces/3d-point-cloud-cuboid-interface.md)``             |
| [Text](sample-types.md#text)                                       | [Named entity recognition (NER)](label-types.md#named-entity-recognition-and-span-categorization)                                | [`text-named-entities`](../../guides/use-the-labeling-interfaces/text-named-entities-interface.md)``                        |
|                                                                    | [Span categorization](label-types.md#named-entity-recognition-and-span-categorization)                                           | [`text-span-categorization`](../../guides/use-the-labeling-interfaces/text-span-categorization-interface.md)``              |

Extra:

* [Object attributes](label-types.md#object-attributes)
* [Image attributes](label-types.md#image-attributes)
