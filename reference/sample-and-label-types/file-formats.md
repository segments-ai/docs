# File formats

## Image

Following image file formats are supported: jpeg, png, bmp.

## 3D point cloud

### PCD (Point Cloud Data)

[Version 0.7](https://pointclouds.org/documentation/tutorials/pcd\_file\_format.html) of the PCD format is supported. PCD files can either be ASCII-encoded or binary files. The PCD files should contain at least x, y, and z coordinate fields. Optionally, you can supply an _intensity_ or an RGB field. These fields are used for setting the color of the points. Intensity coloring can be enabled or disabled in the viewer.

Any other fields will be ignored.

<table><thead><tr><th>Field name</th><th data-type="number">Size (#bytes)</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>4</td><td>float</td><td>true</td></tr><tr><td>y</td><td>4</td><td>float</td><td>true</td></tr><tr><td>z</td><td>4</td><td>float</td><td>true</td></tr><tr><td>intensity</td><td>4</td><td>float</td><td>false</td></tr><tr><td>rgb</td><td>4</td><td>float</td><td>false</td></tr></tbody></table>

### Binary xyzi(r) (KITTI/nuScenes)

We also support the binary point cloud formats used by the [KITTI](http://www.cvlibs.net/datasets/kitti/index.php) and [nuScenes](https://www.nuscenes.org) datasets. These formats do not contain a header and have a fixed number of fields.

<table><thead><tr><th>Field name</th><th data-type="number">Size (#bytes)</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>4</td><td>float</td><td>true</td></tr><tr><td>y</td><td>4</td><td>float</td><td>true</td></tr><tr><td>z</td><td>4</td><td>float</td><td>true</td></tr><tr><td>intensity</td><td>4</td><td>float</td><td>true</td></tr><tr><td>ring index</td><td>4</td><td>float</td><td>false</td></tr></tbody></table>
