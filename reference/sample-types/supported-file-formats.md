# Supported file formats

## Image

Following image file formats are supported: jpeg, png, bmp.

## 3D point cloud

### PCD (Point Cloud Data)

[Version 0.7](https://pointclouds.org/documentation/tutorials/pcd\_file\_format.html) of the PCD format is supported. PCD files can either be ASCII-encoded or binary files. The PCD files should contain at least x, y, and z coordinate fields. Optionally, you can supply an _intensity_ or an RGB field. These fields are used for setting the color of the points. Intensity coloring can be enabled or disabled in the viewer.

Any other fields will be ignored.

<table><thead><tr><th>Field name</th><th width="150" data-type="number">Size (#bytes)</th><th width="150">Type</th><th width="150" data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>4</td><td>float</td><td>true</td></tr><tr><td>y</td><td>4</td><td>float</td><td>true</td></tr><tr><td>z</td><td>4</td><td>float</td><td>true</td></tr><tr><td>intensity</td><td>4</td><td>float</td><td>false</td></tr><tr><td>rgb</td><td>4</td><td>float</td><td>false</td></tr></tbody></table>

{% hint style="warning" %}
Please make sure that you supply the values as 32-bit (=4 byte) floats.

Keep in mind that 32-bit floats have limited precision. In fact, only 24 bits can be used to represent the number itself (the significand, excluding the sign bit), or about 7.22 decimal digits. If you want to keep two decimal places, this only leaves 5.22 decimal digits, so the numbers shouldn't be larger than 10^5.22 = 165958.

To avoid rounding problems, it is best practice to subtract the ego position of the first frame from all other ego positions. This way, the first ego position is set to (0, 0, 0) and the subsequent ego positions are relative to (0, 0, 0) . In your export script, you can add the ego position of the first frame back to the object positions.
{% endhint %}

### Binary xyzi(r) (KITTI/nuScenes)

Segments.ai supports the binary point cloud formats used by the [KITTI](http://www.cvlibs.net/datasets/kitti/index.php) and [nuScenes](https://www.nuscenes.org/) datasets. These formats do not contain a header and have a fixed number of fields. When uploading a sample with point clouds in one of these formats, use `binary-xyzi` (alias `kitti`) or `binary-xyzir` (alias `nuscenes`) for the type field.

<table><thead><tr><th>Field name</th><th width="150" data-type="number">Size (#bytes)</th><th width="150">Type</th><th width="150" data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>4</td><td>float</td><td>true</td></tr><tr><td>y</td><td>4</td><td>float</td><td>true</td></tr><tr><td>z</td><td>4</td><td>float</td><td>true</td></tr><tr><td>intensity</td><td>4</td><td>float</td><td>true</td></tr><tr><td>ring index</td><td>4</td><td>float</td><td>false</td></tr></tbody></table>

### PLY (Stanford Triangle Format)&#x20;

The PLY file format can be used for point clouds by encoding the points as vertices. The PLY header should thus contain a vertex _element_ containing x, y, and z _properties_ and optionally also color or intensity properties. Both binary and ASCII PLY files are supported.

{% hint style="danger" %}
PLY Gaussian Splats are not supported
{% endhint %}

<table><thead><tr><th>Property name</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>float32</td><td>true</td></tr><tr><td>y</td><td>float32</td><td>true</td></tr><tr><td>z</td><td>float32</td><td>true</td></tr><tr><td>red</td><td>uchar [0, 255]</td><td>false</td></tr><tr><td>green</td><td>uchar [0, 255]</td><td>false</td></tr><tr><td>blue</td><td>uchar [0, 255]</td><td>false</td></tr><tr><td>intensity</td><td>float32</td><td>false</td></tr></tbody></table>

### LAS

{% hint style="warning" %}
* LAS support is limited to 3D cuboid and 3D vector task types. It is not supported for 3D point cloud segmentation.
* Unlike other file formats, the uploaded files can only be viewed after the [tiling process](../../background/3d-tiles.md) is completed.
* The LAS file format is currently only recommended for huge point clouds (e.g. merged maps) that cannot be tiled otherwise.
{% endhint %}

[Version 1.4](https://www.asprs.org/wp-content/uploads/2019/03/LAS\_1\_4\_r14.pdf) of the LAS file format is supported. Only uncompressed LAS files are currently supported.

Point clouds can optionally include RGB fields, or an intensity field. If both are defined, the intensity will be discarded.

* For point clouds with RGB colors, make sure to set the point format field to 2.
* For point clouds with intensity values, make sure to set the point format field to 0.

Keep in mind to set the LAS scale/resolution small enough (e.g. 1e-6) to avoid discretization errors.

<table><thead><tr><th>Property name</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>X</td><td>float32</td><td>true</td></tr><tr><td>Y</td><td>float32</td><td>true</td></tr><tr><td>Z</td><td>float32</td><td>true</td></tr><tr><td>Red</td><td>uint8 [0-255]</td><td>false</td></tr><tr><td>Green</td><td>uint8 [0-255]</td><td>false</td></tr><tr><td>Blue</td><td>uint8 [0-255]</td><td>false</td></tr><tr><td>Intensity</td><td>uint8 [0-255]</td><td>false</td></tr></tbody></table>

## Gaussian Splat

### .splat

Gaussian splats can only be uploaded as .splat files at the moment. PLY splat files are not supported. If you want to convert your splat file from PLY to .splat, you can either use [SuperSplat](https://playcanvas.com/supersplat/editor), an online splat editor, or the open-source [point-cloud-tool](https://github.com/SpectacularAI/point-cloud-tools) library.
