# 3D point cloud cuboid interface

{% hint style="info" %}
When [creating a dataset](../../python-sdk.md#create-a-dataset) through the Python SDK, choose `pointcloud-cuboid` or `pointcloud-cuboid-sequence` as the `task_type` to use this labeling interface.&#x20;
{% endhint %}

## Cuboid editing

### Create a new cuboid

#### Create a cuboid with default dimensions

If you've set up the default dimensions for your categories (see [#categories](../../reference/categories-and-task-attributes.md#categories "mention")), you can create a cuboid with default dimensions in one click.

1. Select the "Create cuboid" tool by clicking on the box icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Click in the perspective view or in the top view to create a new cuboid. This cuboid will have the default dimensions of the current category. When you change the category, the dimensions of the cuboid will change as well, given that you have not altered the dimensions of the cuboid yet.

#### Draw a cuboid with custom dimensions

1. Select the "Create cuboid" tool by clicking on the box icon in the toolbar on the left, or by pressing the hotkey (`b` by default).
2. Click and drag in the perspective view or in the top view to draw a new cuboid. When you release the mouse, the new cuboid is added to the objects sidebar on the right.

### Remove a cuboid

1. Select the cuboid you want to remove.
2. Press the hotkey (`Backspace` by default) or click the trash icon next to the object in the objects sidebar on the right.

### Select a cuboid

#### Using the "Select and edit" tool

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Click on the cuboid in any view.

#### Using the objects sidebar

1. Click on the object in the objects sidebar to select it.

### Change the dimensions of a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to change.
3. Change the cuboid's dimensions:
   * In the perspective view: click and drag a face of the cuboid.
   * In a side view: click and drag one of the edges of the cuboid.

### Translate a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to translate.
3. Click and drag the yellow cube in the middle of the cuboid to translate the cuboid freely.\
   Hover over the yellow cube in the middle to see the translation axe. Click and drag on an axis to translate the cuboid along the selected axis.

### Rotate a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to rotate.
3. Click and drag the red rotation plane in front of the cuboid to rotate the cuboid.

### Change the heading of a cuboid

1. Select the "Select and edit" tool by clicking on the pointer icon in the toolbar on the left, or by pressing the hotkey (`Esc` by default).
2. Select the cuboid you want to change.
3. Change the heading of the cuboid (indicated by a red arrow):
   * In the perspective view: double-click the face where you want the heading to be.
   * In a side view: double-click the edge where you want the heading to be.

### Change the category of a cuboid

{% hint style="info" %}
If the selected cuboid was created with default dimensions, the dimensions of the cuboid will change to the default dimensions of the new category.
{% endhint %}

#### Using the category dropdown

1. Select the cuboid.
2. Open the category dropdown by clicking on the category name in the objects sidebar on the right, or by pressing the hotkey (`c` by default).
3. Select a category by clicking on the desired category, **** or by using the arrow keys and pressing `Enter` to confirm.

#### Using the category hotkey

1. Select the cuboid.
2. Press the hotkey of the desired category (`1` - `9`).

### Cycle between cuboids / select the next cuboid

Press the hotkey (`Tab` by default).

## Viewing

### Move the camera

Hold the hotkey (`Ctrl/cmd` by default) and click and drag.

#### Only in the perspective view

* Use the keyboard navigation (by default: `w` to move forward, `a` to move left, `s` to move backward, and `d` to move right).

### Rotate/orbit the camera in the perspective view

Hold the hotkey (`Shift` by default) and click and drag.

### Zoom to a cuboid

1. Select the cuboid.
2. Press the hotkey (`t` by default).

### Enable intensity coloring

1. Upload a point cloud with intensity labels.
2. Press the sun icon in the toolbar on the right to toggle intensity coloring.

### Pan to a bird's eye view in the perspective view

Press the hotkey (`Ctrl/cmd + b` by default).

### Change the size of the points

1. Click/hover over the dot icon in the toolbar on the right.
2. Drag the slider to adjust the point size.

### Change the key pan speed

1. Click/hover over the tachometer icon in the toolbar on the right.
2. Drag the slider to adjust the key pan speed, i.e. the speed the camera moves when using keyboard navigation.
