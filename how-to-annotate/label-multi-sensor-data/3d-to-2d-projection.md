# 3D to 2D Projection

For multi-sensor labeling, utilizing the ‘Project cuboids to camera sensors’ feature will automatically project 2D bounding boxes on the camera sensor frames from the 3D cuboids in the lidar point cloud. The projected 2D bounding boxes will maintain the object’s track ID throughout all sensors. This will help speed up the labeling for the 2D camera frames.

<figure><img src="../../.gitbook/assets/3d_to_2d_projection.gif" alt=""><figcaption><p> </p></figcaption></figure>

{% hint style="info" %}
The sensors list has been moved to a dropdown in the top part of the right sidebar.
{% endhint %}

Open the sensors dropdown to access ‘Project cuboids to camera sensors’.

<figure><img src="../../.gitbook/assets/Screenshot 2025-11-18 at 16.52.15.png" alt="" width="375"><figcaption></figcaption></figure>

### **Overwrite existing tracks**

* If this option is checked, it will use the 3D cuboids to overwrite existing 2D bounding box objects.
* If you made adjustments to the 2D bounding boxes and want to project additional objects from 3D to 2D, make sure this option is unchecked.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-27 at 12.48.06 PM.png" alt="" width="296"><figcaption></figcaption></figure>

