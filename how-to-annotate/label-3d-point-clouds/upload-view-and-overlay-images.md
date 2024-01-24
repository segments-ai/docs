# Upload, view, and overlay images

See the [view-and-navigate-in-the-3d-interface.md](view-and-navigate-in-the-3d-interface.md "mention") page for basic 3D navigation principles.

## Upload images along with point clouds

Segments.ai allows you to upload images along with point clouds. Additionally, you can also specify the camera calibration parameters, which allows you to view the 3D point cloud and objects on the image. See [#camera-image](../../reference/sample-types/#camera-image "mention") for information on how to add camera images and calibration parameters to a sample.

## Open/close the image viewer

When you open a sample with images, you can see the thumbnails of the images at the bottom of the main labeling window.

#### Open the image viewer

* Click on the thumbnail of the image
* Or press the number key (`1` - `9`) corresponding to the image. The images are numbered from left to right.

{% hint style="info" %}
The 3D overlay (of objects and the point cloud) is only visible if the camera parameters of the image are specified.
{% endhint %}

#### Close the image viewer

* Click on the thumbnail of the image again
* Or press `Esc`
* Or press the number key (`1` - `9`) corresponding to the image again

## Zoom/pan in the image viewer

### Zoom in/out

To zoom in or out, scroll using the mouse wheel, or double-click in the viewer.

### Pan

Hold the hotkey (`Ctrl/cmd` by default) and click and drag.

{% embed url="https://segments.ai/blog/assets/images/improved-image-viewer/zoom-pan-trim-compr.mp4" %}

## Toggle the point cloud overlay

To toggle the point cloud overlay on and off, press the hotkey (`Ctrl/cmd + q` by default) or toggle it in the [3D interface settings](3d-interface-settings.md#toggle-point-cloud-overlay-on-images). Disabling the point cloud overlay allows you to see the camera image in more detail, while enabling it allows you to see if the camera and lidar are well calibrated.

{% embed url="https://segments.ai/blog/assets/images/improved-image-viewer/pc-overlay-trim-compr.mp4" %}

## Use the **synchronized** image viewer

When one or more **calibrated** images are available, a synchronized image viewer appears in the bottom right of the screen. When hovering in the perspective or top view this viewer automatically zooms to the location of the pointer in the closest camera image.

{% embed url="https://segments.ai/blog/assets/images/improved-image-viewer/following-pointer-trim-compr.mp4" %}

## View the active cuboid camera images in the synchronized viewer

When a cuboid is selected, the synchronized image viewer shows the active cuboid in every camera image where it appears.

To switch between the camera images, press the arrow buttons on the left/right of the synchronized image viewer, or press a rectangle at the bottom of the synchronized image viewer.

You can also zoom/pan in the synchronized image viewer in the same way as in the image viewer (see [above](upload-view-and-overlay-images.md#zoom-pan-in-the-image-viewer)).



<figure><img src="../../.gitbook/assets/Screenshot 2024-01-24 at 22.32.38.png" alt=""><figcaption></figcaption></figure>

## View the image grid in a new tab

When adding images to a sample, you have to specify a row and column for each image. This information is used to display a grid of your images. You can view this grid in a separate browser tab (which you could move to a second screen).

* To open the image grid in a new tab, press the "Open grid" rectangle next to the camera images at the bottom of the main viewer.\
  ![](../../.gitbook/assets/image.png)

You can interact with the images in the grid as follows:

* To zoom in/out on an image, scroll using the mousewheel or double-click on the image.&#x20;
* To pan an image, click and drag on the image.
* To open the image viewer in the main labeling window, click the camera icon in the top right corner of the image.&#x20;

<figure><img src="../../.gitbook/assets/image (7) (3).png" alt=""><figcaption></figcaption></figure>

