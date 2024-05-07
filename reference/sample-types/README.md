# Sample formats

A [sample](../../background/main-concepts.md#sample) is a data point you want to label. Samples come in different types, like an image, a 3D point cloud, or a video sequence. When uploading ([`client.add_sample()`](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample)) or downloading ([`client.get_sample()`](https://sdkdocs.segments.ai/en/latest/client.html#get-a-sample)) a sample using the [Python SDK](https://sdkdocs.segments.ai/en/latest/client.html), the format of the `attributes` field depends on the type of sample. The different formats are described here.

{% hint style="info" %}
The section [import-data](../../how-to-integrate/import-data/ "mention") shows how you can obtain URLs for your assets.
{% endhint %}

## Image

Supported image formats:  jpeg, png, bmp.

```json
{
    "image": {
        "url": "https://example.com/image.jpg"
    }
}
```

{% hint style="warning" %}
If the image file is on your local computer, you should first upload it to our asset storage service (using [`upload_asset()`](https://sdkdocs.segments.ai/en/latest/client.html#upload-an-asset-to-segments-s3-bucket)) or to another cloud storage service.
{% endhint %}

## Image sequence

Supported image formats:  jpeg, png, bmp.

```json
{ 
  "frames": [
    {
      "image": {
        "url": "https://example.com/frame_00001.jpg"
      },
      "name": "frame_00001" // optional
    },
    {
      "image": {
        "url": "https://example.com/frame_00002.jpg"
      },
      "name": "frame_00002"
    },
    {
      "image": {
        "url": "https://example.com/frame_00003.jpg"
      },
      "name": "frame_00003"
    }
  ]
} 
```

## 3D point cloud

{% hint style="info" %}
On Segments.ai, the up direction is defined along the z-axis, i.e. the vector (0, 0, 1) points up. If you upload point clouds with a different up direction, you might have trouble navigating the point cloud.
{% endhint %}

```json
{
    "pcd": {
        "url": "https://example.com/pointcloud.pcd",
        "type": "pcd"
    },
    "images": [
        { ... },
        { ... },
        { ... }
    ], // optional
    "name": "frame_00001", // optional
    "timestamp": "00001", // optional
    "ego_pose": {
        "position": {
            "x": -2.7161461413869947,
            "y": 116.25822288149078,
            "z": 1.8348751887989483
        },
        "heading": {
            "qx": -0.02111296123795955,
            "qy": -0.006495469416730261,
            "qz": -0.008024565904865688,
            "qw": 0.9997181192298087
        }
    },
    "default_z": -1, // optional, 0 by default
    "bounds": { // optional
        "min_z": -1,
        "max_z": 3
    }
}
```

<table><thead><tr><th>Name</th><th width="250.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>pcd</code></td><td><a href="./#undefined">Point cloud data</a></td><td><strong>Required.</strong> Point cloud data.</td></tr><tr><td><code>images</code></td><td><code>array</code> of <a href="./#camera-image">camera images</a></td><td>Reference camera images.</td></tr><tr><td><code>name</code></td><td><code>string</code></td><td>Name of the sample.</td></tr><tr><td><code>timestamp</code></td><td><code>int</code> or <code>string</code></td><td>Timestamp of the sample. Object kinematics will only be calculated if the timestamp is an integer representing the time in nanoseconds.</td></tr><tr><td><code>ego_pose</code></td><td><a href="./#ego-pose">Ego pose</a></td><td>Pose of the sensor that captured the point cloud data.</td></tr><tr><td><code>default_z</code></td><td><code>float</code></td><td>Default z-value of the ground plane. 0 by default. Only valid in the point cloud cuboid editor. New cuboids will be drawn on top of the ground plane, i.e. the default z-position of a new cuboid is 0.5 (since the default height of a new cuboid is 1).</td></tr><tr><td><code>bounds</code></td><td><code>dict</code></td><td>Point cloud bounds: a <code>dict</code> with values <code>min_z</code> and <code>max_z</code> (<code>float</code>). These values are used as the default min/max values for height coloring when provided.</td></tr></tbody></table>

### Point cloud data

See [3D point cloud formats](supported-file-formats.md#3d-point-cloud) for the supported file formats.

```json
{
    "url": "https://example.com/pointcloud.bin",
    "type": "kitti"
}
```

<table><thead><tr><th>Name</th><th width="253.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>url</code></td><td><code>string</code></td><td><strong>Required.</strong> URL of the point cloud data.</td></tr><tr><td><code>type</code></td><td><code>string</code>: "pcd" | "binary-xyzi" | "kitti" | "binary-xyzir" | "nuscenes" | "ply"</td><td><strong>Required.</strong> Type of the point cloud data. See <a data-mention href="supported-file-formats.md#3d-point-cloud">#3d-point-cloud</a> file formats for the list of supported file formats.</td></tr></tbody></table>

{% hint style="warning" %}
If the point cloud file is on your local computer, you should first upload it to our asset storage service (using [`upload_asset()`](https://sdkdocs.segments.ai/en/latest/client.html#upload-an-asset-to-segments-s3-bucket)) or to another cloud storage service.
{% endhint %}

### Camera image

A calibrated or uncalibrated reference image corresponding to a point cloud. The reference images can be opened in a new tab from within the labeling interface. You can determine the layout of the images by setting the `row` and `col` attributes on each image. If you also supply the calibration parameters (and distortion parameters if necessary), the main point cloud view can be set to the image to obtain a fused view.

```json
{
    "name": "Camera example 1", // optional
    "url": "https://example.com/image.jpg",
    "row": 0,
    "col": 0,
    "intrinsics": { // optional
        "intrinsic_matrix": [
            [1266.417203046554, 0, 816.2670197447984],
            [0, 1266.417203046554, 491.50706579294757],
            [0, 0, 1]
        ]
    },
    "extrinsics": { // optional
        "translation": {
            "x": -0.012463384576629082,
            "y": 0.76486688894964,
            "z": -0.3109103442096661
        },
        "rotation": {
            "qx": 0.713640516187247,
            "qy": -0.001134052598226082,
            "qz": 0.0036449450274057696,
            "qw": 0.7005017073187271
        }
    },
    "distortion": { // optional
        "model": "fisheye",
        "coefficients": {
            "k1": -0.0539124,
            "k2": -0.0101993,
            "k3": -0.00202017,
            "k4": 0.00120938
        }
    },
    "camera_convention": "OpenCV", // optional
    "rotation": 1.5708 // optional
}
```

<table><thead><tr><th>Name</th><th width="255">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code></td><td><code>string</code></td><td>Name of the camera image.</td></tr><tr><td><code>url</code></td><td><code>string</code></td><td><strong>Required.</strong> URL of the camera image.</td></tr><tr><td><code>row</code></td><td><code>int</code></td><td><strong>Required.</strong> Row of this image in the images viewer.</td></tr><tr><td><code>col</code></td><td><code>int</code></td><td><strong>Required.</strong> Column of this image in the images viewer.</td></tr><tr><td><code>intrinsics</code></td><td><a href="./#camera-intrinsics">Camera intrinsics</a></td><td>Intrinsic parameters of the camera.</td></tr><tr><td><code>extrinsics</code></td><td><a href="./#camera-extrinsics">Camera extrinsics</a></td><td>Extrinsic parameters of the camera relative to the <a href="./#ego-pose">ego pose</a>.</td></tr><tr><td><code>distortion</code></td><td><a href="./#distortion">Distortion</a></td><td>Distortion parameters of the camera.</td></tr><tr><td><code>camera_convention</code></td><td><code>string</code>: "OpenGL" | "OpenCV"</td><td>Convention of the camera coordinates. We use the OpenGL/Blender coordinate convention for cameras. +X is right, +Y is up, and +Z is pointing back and away from the camera. -Z is the look-at direction. Other codebases may use the OpenCV convention, where the Y and Z axes are flipped but the +X axis remains the same. See diagram 1.</td></tr><tr><td><code>rotation</code></td><td><code>float</code></td><td>The rotation that needs to be applied when displaying the image. Valid options are 0, <span class="math">\frac{\pi}{4} </span>, <span class="math">\frac{\pi}{2}</span>, and <span class="math">\frac{3 \pi}{4}</span>. Useful for when a camera is mounted upside-down.</td></tr></tbody></table>

{% hint style="warning" %}
If the image file is on your local computer, you should first upload it to our asset storage service (using [`upload_asset()`](https://sdkdocs.segments.ai/en/latest/client.html#upload-an-asset-to-segments-s3-bucket)) or to another cloud storage service.
{% endhint %}

#### Camera intrinsics

```json
{
    "intrinsic_matrix": [
        [1266.417203046554, 0, 816.2670197447984],
        [0, 1266.417203046554, 491.50706579294757],
        [0, 0, 1]
    ]
}
```

<table><thead><tr><th>Name</th><th width="254">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>intrinsic_matrix</code></td><td>2D <code>array</code> of <code>float</code>s representing 3x3 matrix <span class="math">K</span>in row-major order​</td><td><p><strong>Required.</strong> Intrinsic matrix <span class="math">K</span> used in the pinhole camera model.<br><span class="math">K = \begin{bmatrix} f_x &#x26; 0 &#x26; o_x\\ 0 &#x26; f_y &#x26; o_y \\ 0 &#x26; 0 &#x26; 1 \end{bmatrix}</span></p><p>​<span class="math">f_x</span> and <span class="math">f_y</span>​ are the focal lengths in pixels. We assume square pixels, so <span class="math">f_x = f_y</span>​. <span class="math">o_x</span> and <span class="math">o_y</span> are the offsets (in pixels) of the principal point from the top-left corner of the image frame.</p></td></tr></tbody></table>

#### Camera extrinsics

```json
{
    "translation": {
        "x": -0.012463384576629082,
        "y": 0.76486688894964,
        "z": -0.3109103442096661
    },
    "rotation": {
        "qx": 0.713640516187247,
        "qy": -0.001134052598226082,
        "qz": 0.0036449450274057696,
        "qw": 0.7005017073187271
    }
}
```

<table><thead><tr><th>Name</th><th width="244">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>translation</code></td><td><code>object</code>: {<br>    "x": <code>float</code>,<br>    "y": <code>float</code>,<br>    "z": <code>float</code><br>}</td><td><strong>Required.</strong> Translation of the camera in lidar coordinates, i.e., relative to the <a href="./#ego-pose">ego pose</a>.</td></tr><tr><td><code>rotation</code></td><td><p><code>object</code>: {<br>    "qx": <code>float</code>,<br>    "qy": <code>float</code>,<br>    "qz": <code>float</code>,</p><p>    "qw": <code>float</code><br>}</p></td><td><strong>Required.</strong> Rotation of the camera in lidar coordinates, i.e., relative to the <a href="./#ego-pose">ego pose</a> (or equivalently: a transformation from camera frame to ego frame). Defined as a <a href="https://danceswithcode.net/engineeringnotes/quaternions/quaternions.html">rotation quaternion</a>. By default, we use the OpenGL/Blender coordinate convention for cameras. +X is right, +Y is up, and +Z is pointing back and away from the camera. -Z is the look-at direction. Other codebases may use the OpenCV convention, where the Y and Z axes are flipped but the +X axis remains the same. See diagram 1. You can specify the camera convention in <a data-mention href="./#camera-image">#camera-image</a>.</td></tr></tbody></table>

<figure><img src="../../.gitbook/assets/camera-axes (1).png" alt=""><figcaption><p>Diagram 1: camera convention for calibrated camera images on Segments.ai.</p></figcaption></figure>

#### Distortion

```json
// Fisheye
{ 
    "model": "fisheye",
    "coefficients": {
        "k1": -0.0539124,
        "k2": -0.0101993,
        "k3": -0.00202017,
        "k4": 0.00120938
}
// Brown-Conrady
{ 
    "model": "brown-conrady",
    "coefficients": {
        "k1": -0.2916058942,
        "k2": 0.0763231072,
        "k3": 0.0,
        "p1": 0.0014829263,
        "p2": -0.0019540316
    }
}
```

<table><thead><tr><th>Name</th><th width="251.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>model</code></td><td><code>string</code>: "fisheye" | "brown-conrady"</td><td><strong>Required.</strong> Type of the distortion model: <a href="https://en.wikipedia.org/wiki/Fisheye_lens">fisheye</a> or <a href="https://en.wikipedia.org/wiki/Distortion_(optics)">Brown-Conrady</a>.</td></tr><tr><td><code>coefficients</code> </td><td><p>Fisheye:<br><code>object</code>: {</p><p>    "k1": <code>float</code>,</p><p>    "k2": <code>float</code>,</p><p>    "k3": <code>float</code>,</p><p>    "k4": <code>float</code>,</p><p>}</p><p><br>Brown-Conrady:<br><code>object</code>: {</p><p>    "k1": <code>float</code>,</p><p>    "k2": <code>float</code>,</p><p>    "k3": <code>float</code>,</p><p>    "p1": <code>float</code>,</p><p>    "p2": <code>float</code></p><p>}</p></td><td><strong>Required.</strong> Coefficients of the distortion model: <code>k1</code>, <code>k2</code>, <code>k3</code>, <code>k4</code> for fisheye (see the <a href="https://docs.opencv.org/4.x/db/d58/group__calib3d__fisheye.html">OpenCV fisheye model</a>) and <code>k1</code>, <code>k2</code>, <code>k3</code>, <code>p1</code>, <code>p2</code> for Brown-Conrady (see the <a href="https://docs.opencv.org/4.x/d9/d0c/group__calib3d.html">OpenCV distortion model</a>, note that <span class="math">k_4</span> and <span class="math">k_5</span> are not used).</td></tr></tbody></table>

### Ego pose

The pose of the sensor used to capture the 3D point cloud data. This can be helpful if you want to obtain cuboids in world coordinates, or when your sensor is moving. In the latter situation, supplying an ego pose with each frame will ensure that static objects do not move when switching between frames.

```json
{
    "position": {
        "x": -2.7161461413869947,
        "y": 116.25822288149078,
        "z": 1.8348751887989483
    },
    "heading": {
        "qx": -0.02111296123795955,
        "qy": -0.006495469416730261,
        "qz": -0.008024565904865688,
        "qw": 0.9997181192298087
    }
},
```

<table><thead><tr><th>Name</th><th width="254.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>position</code></td><td><code>object</code>: {<br>    "x": <code>float</code>,<br>    "y": <code>float</code>,<br>    "z": <code>float</code><br>}</td><td><strong>Required.</strong> XYZ position of the sensor in world coordinates.</td></tr><tr><td><code>heading</code></td><td><p><code>object</code>: {<br>    "qx": <code>float</code>,<br>    "qy": <code>float</code>,<br>    "qz": <code>float</code>,</p><p>    "qw": <code>float</code><br>}</p></td><td><strong>Required.</strong> Orientation of the sensor. Defined as a <a href="https://danceswithcode.net/engineeringnotes/quaternions/quaternions.html">rotation quaternion</a>.</td></tr></tbody></table>

{% hint style="warning" %}
Segments.ai uses 32-bit floats for the point positions. Keep in mind that 32-bit floats have limited precision. In fact, only 24 bits can be used to represent the number itself (the significand, excluding the sign bit), or about 7.22 decimal digits. If you want to keep two decimal places, this only leaves 5.22 decimal digits, so the numbers shouldn't be larger than 10^5.22 = 165958.

To avoid rounding problems, it is best practice to subtract the ego position of the first frame from all other ego positions. This way, the first ego position is set to (0, 0, 0) and the subsequent ego positions are relative to (0, 0, 0) . In your export script, you can add the ego position of the first frame back to the object positions.
{% endhint %}

## 3D point cloud sequence

```json
{ 
  "frames": [
    { ... },
    { ... },
    { ... }
  ]
} 
```

<table><thead><tr><th>Name</th><th width="250.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>frames</code></td><td><code>array</code> of <a href="./#3d-point-cloud">3D point clouds</a></td><td><strong>Required.</strong> List of 3D point cloud frames in the sequence.</td></tr></tbody></table>

## Multi-sensor sequence

```json
{
  "sensors": [
    {
      "name": "Lidar", 
      "task_type": "pointcloud-cuboid-sequence",
      "attributes": { ... }
    },
    {
      "name": "Camera 1", 
      "task_type": "image-vector-sequence",
      "attributes": { ... } 
    },
    ...
  ]
}
```

<table><thead><tr><th>Name</th><th width="256.3333333333333">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>sensors</code></td><td><code>array</code> of <a href="./#sensor">sensors</a></td><td><strong>Required.</strong> List of the sensors that can be labeled.</td></tr></tbody></table>

#### Sensor

<table><thead><tr><th>Name</th><th width="253.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code></td><td><code>string</code></td><td><strong>Required.</strong> The name of the sensor.</td></tr><tr><td><code>task_type</code></td><td><code>string</code></td><td><strong>Required.</strong> The <a href="../sample-and-label-types.md">task type</a> of the sensor. Currently, <code>pointcloud-cuboid-sequence</code> and <code>image-vector-sequence</code> are supported.</td></tr><tr><td><code>attributes</code></td><td><code>object</code></td><td><strong>Required.</strong> The sample attributes for the sensor. Currently, <a href="./#3d-point-cloud-sequence">3D point cloud sequence</a> and <a href="./#image-sequence">image sequence</a> are supported.</td></tr></tbody></table>

## Text

```json
{ 
    "text": "Example text sample." 
}
```

<table><thead><tr><th>Name</th><th width="251.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>text</code></td><td><code>string</code></td><td><strong>Required.</strong> Text data.</td></tr></tbody></table>

{% hint style="info" %}
To upload text samples in bulk, see [file formats](supported-file-formats.md#text).
{% endhint %}
