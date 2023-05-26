# Merged point cloud view (for static objects)

When labeling a static object in 3D point cloud sequences, a single frame might not show the object in full detail. It can thus be difficult to assess the full dimensions of an object.

To solve this issue, you can toggle a merged point cloud view.

{% embed url="https://youtu.be/om5w69OErVs?t=17" %}
This video shows how you can use the merged point cloud view to draw a perfect cuboid around a static object.
{% endembed %}

## Toggle the merged point cloud view

Click on the merged point cloud icon (![](<../../.gitbook/assets/image (1) (1).png>)) in the right toolbar to toggle the merged point cloud view on/off.

{% hint style="warning" %}
The merged point cloud view is only available for 3D vector labeling (cuboids, polygons, polylines, keypoints).&#x20;

[Contact us](https://segments.ai/contact) if you are interested in the merged point cloud for 3D segmentation.
{% endhint %}

{% hint style="info" %}
Tip: add an `is_static` track-level attribute to the categories that can be static (see [configure-label-editor.md](../../configure-label-editor.md "mention")). When this attribute is checked, you can edit the position/dimensions/rotation of a cuboid in one frame, and these changes will be applied to all other frames automatically.
{% endhint %}

{% hint style="info" %}
Tip: [use your GPU in Chrome](https://segmentsai.notion.site/How-to-use-your-GPU-in-Chrome-2b95e19fb77c456c87f798013769a98a) to make sure the 3D point cloud interface runs smoothly.
{% endhint %}
