# Sample formats

A [sample](../../background/main-concepts.md#sample) is a data point you want to label. Samples come in different types, like an image, a 3D point cloud, or a video sequence. When uploading ([`client.add_sample()`](../../python-sdk.md#create-a-sample)) or downloading ([`client.get_sample()`](../../python-sdk.md#get-a-sample)) a sample using the [Python SDK](../../python-sdk.md), the format of the `attributes` field depends on the type of sample. The different formats are described here.

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

```json
{
    "pcd": {
        "url": "https://example.com/pointcloud.bin",
        "type": "kitti"  // optional, "pcd" by default
    },
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
    "default_z": -1 // optional, 0.5 by default
}
```

| Name        | Type                             | Description                                                                                                                                                                                    |
| ----------- | -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `pcd`       | [Point cloud data](./#undefined) | **Required.** Point cloud data.                                                                                                                                                                |
| `name`      | `string`                         | Name of the sample.                                                                                                                                                                            |
| `timestamp` | `string`                         | Timestamp of the sample.                                                                                                                                                                       |
| `ego_pose`  | [Ego pose](./#ego-pose)          | Pose of the sensor that captured the point cloud data.                                                                                                                                         |
| `default_z` | `float`                          | Default z-value of a cuboid. 0.5 by default. Only valid in the point cloud cuboid editor. A cuboid has a height of 1 by default, so the ground plane is located 0.5 under the default z-value. |

### Point cloud data

See [3D point cloud formats](supported-file-formats.md#3d-point-cloud) for the supported file formats.

```json
{
    "url": "https://example.com/pointcloud.bin",
    "type": "kitti"  // optional, "pcd" by default
}
```

| Name   | Type                                                                        | Description                                                                                                                                                                    |
| ------ | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `url`  | `string`                                                                    | **Required.** URL of the point cloud data.                                                                                                                                     |
| `type` | `string`: "pcd" \| "binary-xyzi" \| "kitti" \| "binary-xyzir" \| "nuscenes" | Type of the point cloud data. "pcd" by default. See [#3d-point-cloud](supported-file-formats.md#3d-point-cloud "mention") file formats for the list of supported file formats. |

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

| Name       | Type                                                                                                                                                                     | Description                                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `position` | <p><code>object</code>: {<br>    "x": <code>float</code>,<br>    "y": <code>float</code>,<br>    "z": <code>float</code><br>}</p>                                        | XYZ position of the sensor in world coordinates.                                                                                         |
| `heading`  | <p><code>object</code>: {<br>    "qx": <code>float</code>,<br>    "qy": <code>float</code>,<br>    "qz": <code>float</code>,</p><p>    "qw": <code>float</code><br>}</p> | Orientation of the sensor. Defined as a [rotation quaternion](https://danceswithcode.net/engineeringnotes/quaternions/quaternions.html). |

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

| Name     | Type                                            | Description                                                  |
| -------- | ----------------------------------------------- | ------------------------------------------------------------ |
| `frames` | `array` of [3D point clouds](./#3d-point-cloud) | **Required.** List of 3D point cloud frames in the sequence. |

## Text

```json
{ 
    "text": "Example text sample." 
}
```

| Name   | Type     | Description              |
| ------ | -------- | ------------------------ |
| `text` | `string` | **Required.** Text data. |

{% hint style="info" %}
To upload text samples in bulk, see [file formats](supported-file-formats.md#text).
{% endhint %}
