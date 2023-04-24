# 3D point cloud cuboid interface

{% hint style="info" %}
When [creating a dataset](https://sdkdocs.segments.ai/en/latest/client.html#create-a-dataset) through the Python SDK, choose `pointcloud-cuboid` or `pointcloud-cuboid-sequence` as the `task_type` to use this labeling interface
{% endhint %}

{% hint style="info" %}
Tip: [use your GPU in Chrome](https://segmentsai.notion.site/How-to-use-your-GPU-in-Chrome-2b95e19fb77c456c87f798013769a98a) to make sure the 3D point cloud interface runs smoothly.
{% endhint %}

{% embed url="https://youtu.be/om5w69OErVs" %}
This video shows you how to label cuboids in 3D point cloud sequences on Segments.ai. Specifically, we'll use the [merged point cloud view](merged-point-cloud-view-for-static-objects.md) to easily label static objects, and [batch mode](batch-mode-for-dynamic-objects.md) to label dynamic objects.
{% endembed %}

## Create a new cuboid

#### Create a cuboid with default dimensions

If you've set up the default dimensions for your categories (see [#categories](../../reference/categories-and-task-attributes.md#categories "mention")), you can create a cuboid with default dimensions by double clicking.

1. Select the "Create cuboid" tool by clicking on the box icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Double click in the perspective view or in the top view to create a new cuboid. This cuboid will have the default dimensions of the current category. When you change the category, the dimensions of the cuboid will change as well, given that you have not altered the dimensions of the cuboid yet.

#### Draw a cuboid with custom dimensions

You can quickly draw a cuboid with an arbitrary rotation using our 3-click cuboid drawing method.&#x20;

1. Select the "Create cuboid" tool by clicking on the box icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Click in the perspective view or in the top view to set the back corner of the new cuboid.
3. When you move your mouse, the back side of the cuboid will follow your mouse position. Click to set the second corner of the cuboid.&#x20;
4. Next, you can extend the cuboid by moving your mouse. Click to complete the cuboid. After clicking, the new cuboid is added to the objects sidebar on the right.

## Remove a cuboid

1. Select the cuboid you want to remove.
2. Press the hotkey (`Backspace` by default) or click the trash icon next to the object in the objects sidebar on the right.

## Select a cuboid

#### Using the "Select and edit" tool

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Click on the cuboid in any view.

#### Using the objects sidebar

1. Click on the object in the objects sidebar to select it.

## Change the dimensions of a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to change.
3. Change the cuboid's dimensions by using the hotkeys (`i`, `j`, `k`, `l`, `u`, `o` by default) or by using your mouse:
   * In the perspective view: click and drag a face of the cuboid.
   * In a side view: click and drag one of the edges of the cuboid.

## Translate a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to translate.
3. Translate the cuboid by using the hotkeys (`w`, `a`, `s`, `d`, `Shift + W`, `Shift + S` by default) or by using your mouse:
   * Click and drag the yellow cube in the middle of the cuboid to translate the cuboid freely.
   * Hover over the yellow cube in the middle to see the translation axes. Click and drag on an axis to translate the cuboid along the selected axis.

## Rotate a cuboid

{% hint style="info" %}
By default, only yaw rotation (around the z-axis) is enabled. To enable full 3D rotation, visit the dataset settings, select the "Labeling" tab, tick the "Enable 3D cuboid rotation" checkbox, and press "Save".
{% endhint %}

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to rotate.
3. Click and drag the red rotation plane attached to the cuboid to rotate the cuboid or use the hotkeys:
   * Rotate 1° counterclockwise (yaw): `f` by default
   * Rotate 1° clockwise (yaw): `g` by default
   * Rotate 45° counterclockwise (yaw): `Shift + F` by default
   * Rotate 45° clockwise (yaw): `Shift + G` by default

## Change the heading of a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to change.
3. Change the heading of the cuboid (indicated by a red arrow):
   * In the perspective view: double-click the face where you want the heading to be.
   * In a side view: double-click the edge where you want the heading to be.

## Change the category of a cuboid

{% hint style="info" %}
If the selected cuboid was created with default dimensions, the dimensions of the cuboid will change to the default dimensions of the new category.
{% endhint %}

#### Using the category dropdown

1. Select the cuboid.
2. Open the category dropdown by clicking on the category name in the objects sidebar on the right, or by pressing the hotkey (`c` by default).
3. Select a category by clicking on the desired category, or by using the arrow keys and pressing `Enter` to confirm.

#### Using the category hotkey

1. Select the cuboid.
2. Press the hotkey of the desired category (`1` - `9`).

## Cycle between cuboids / select the next cuboid

Press the hotkey (`Tab` by default).
