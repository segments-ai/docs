# File formats

## Image

Following image file formats are supported: jpeg, png, bmp.

## 3D point cloud

### PCD (Point Cloud Data)

[Version 0.7](https://pointclouds.org/documentation/tutorials/pcd\_file\_format.html) of the PCD format is supported. PCD files can either be ASCII-encoded or binary files. The PCD files should contain at least x, y, and z coordinate fields. Optionally, you can supply an _intensity_ or an RGB field. These fields are used for setting the color of the points. Intensity coloring can be enabled or disabled in the viewer.

Any other fields will be ignored.

<table><thead><tr><th>Field name</th><th data-type="number">Size (#bytes)</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>4</td><td>float</td><td>true</td></tr><tr><td>y</td><td>4</td><td>float</td><td>true</td></tr><tr><td>z</td><td>4</td><td>float</td><td>true</td></tr><tr><td>intensity</td><td>4</td><td>float</td><td>false</td></tr><tr><td>rgb</td><td>4</td><td>float</td><td>false</td></tr></tbody></table>

### Binary xyzi(r) (KITTI/nuScenes)

We also support the binary point cloud formats used by the [KITTI](http://www.cvlibs.net/datasets/kitti/index.php) and [nuScenes](https://www.nuscenes.org/) datasets. These formats do not contain a header and have a fixed number of fields. When uploading a sample with point clouds in one of these formats, use `binary-xyzi` (alias `kitti`) or `binary-xyzir` (alias `nuscenes`) for the type field.

<table><thead><tr><th>Field name</th><th data-type="number">Size (#bytes)</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>x</td><td>4</td><td>float</td><td>true</td></tr><tr><td>y</td><td>4</td><td>float</td><td>true</td></tr><tr><td>z</td><td>4</td><td>float</td><td>true</td></tr><tr><td>intensity</td><td>4</td><td>float</td><td>true</td></tr><tr><td>ring index</td><td>4</td><td>float</td><td>false</td></tr></tbody></table>

## Text

When uploading text samples in bulk through the web platform, following file formats are supported:

#### txt

{% code title="data.txt" %}
```
First text sample.
Second text sample.
```
{% endcode %}

#### json

{% code title="data.json" %}
```json
[
    { "text": "First text sample." },
    { "text": "Second text sample."},
]
```
{% endcode %}

#### jsonl

{% code title="data.jsonl" %}
```json
{ "text": "First text sample." }
{ "text": "Second text sample." }
```
{% endcode %}

#### csv

{% code title="data.csv" %}
```
text
First text sample.
Second text sample.
```
{% endcode %}