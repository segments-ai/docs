# 3D Tiles

3D point clouds are collections of points in 3D space. Depending on the type of sensor used, the number of points in one scan can vary greatly. As 3D sensors have evolved, the resolution of 3D scans has generally increased. Furthermore, robots and autonomous vehicles typically have multiple 3D sensors. The outputs of these sensors can then be combined into one large point cloud scan.&#x20;

High-resolution scans with hundreds of thousands of points, or even millions of points, make it easy to detect objects, but come at a cost of increased file size and compute requirements. This can become a problem when trying to label the point clouds in a browser. Due to the large file size of the point clouds, loading the point cloud files can take a long time, especially when the file is being loaded by a workforce in a region far from your data center. Displaying hundreds of thousands of points in the browser can also be taxing for the GPU, and if there are too many points, the labeling interface can become unresponsive.

To solve these issues, we've introduced an option to split your point clouds into 3D tiles. When viewing the point cloud, the application only loads the tiles which should be visible, and only loads the tiles that are close in high resolution. Thus, the point cloud can load faster, and the GPU can comfortably render all points. This approach is similar to the way Google Earth works; when you are zoomed out, the application only loads a low-resolution image of a whole area. When you zoom in, smaller high-resolution tiles are loaded automatically.

## Why use 3D tiles?

* Upload and label point clouds with **no limits on the point cloud size**
* Enable a [merged point cloud view](../how-to-annotate/use-the-3d-point-cloud-labeling-interfaces/merged-point-cloud-view.md) when labeling sequences of point clouds
* Enable the [batch mode](../how-to-annotate/use-the-3d-point-cloud-labeling-interfaces/batch-mode-for-dynamic-objects.md) for labeling dynamic objects in point cloud sequences

## How to enable 3D tiles

This feature is currently available behind a feature flag. [Contact us](https://segments.ai/contact) if you'd like to enable 3D tiles for your point clouds.

{% hint style="info" %}
3D tiles are currently only available for 3D vector labeling tasks (cuboid, polygon/polyline, and keypoint annotation). \
\
[Contact us](https://segments.ai/contact) if you're interested in 3D tiles for point cloud segmentation.
{% endhint %}

