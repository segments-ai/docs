# Sample types

When downloading or uploading samples using the [Python SDK](../python-sdk.md), the format of the`attributes` field depends on the type of sample. The different formats are described here.

## Image

Format of the `attributes` field in [`client.get_sample()`](../python-sdk.md#get-a-sample):&#x20;

```json
{
    "image": {
        "url": "https://example.com/image.jpg" // Can be jpg or png
    }
}
```

## Image sequence

Format of the `attributes` field in [`client.get_sample()`](../python-sdk.md#get-a-sample):&#x20;

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

Format of the `attributes` field in [`client.get_sample()`](../python-sdk.md#get-a-sample):&#x20;

```json
{
    "pcd": {
        "url": "https://example.com/pointcloud.pcd"
    }
}
```

## 3D point cloud sequence

Format of the `attributes` field in [`client.get_sample()`](../python-sdk.md#get-a-sample):&#x20;

```json
{ 
  "frames": [
    {
      "pcd": {
        "url": "https://example.com/frame_00001.pcd"
      },
      "name": "frame_00001" // optional
    },
    {
      "pcd": {
        "url": "https://example.com/frame_00002.pcd"
      },
      "name": "frame_00002"
    },
    {
      "pcd": {
        "url": "https://example.com/frame_00003.pcd"
      },
      "name": "frame_00003"
    }
  ]
} 
```
