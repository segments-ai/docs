# Configure the label editor

Once you have created a dataset, you can further configure the labeling interface under **Settings** -> **Labeling** -> **Categories:**

![](<.gitbook/assets/image (11).png>)

Here you can set the color, name, and description for each category.&#x20;

## Working with attributes

### Object attributes

You can add one or more object-level attributes or _object attributes_ to a category by expanding its row.

Attributes come in 4 types:&#x20;

* Select box
* Multi-select box
* Checkbox
* Text
* Number

You can optionally configure following settings for each object attribute:

* **Default value**: default value of the attribute.
* **Mandatory**: whether the attribute is mandatory. Mandatory attributes raise a warning when not filled in.
* **Synced across frames ("Sequence-level")**: Only in sequence datasets. Whether an attribute should remain constant across all frames for an object with a certain track ID. If false, the attribute can change on each frame.
* **Synced across sensors ("Across sensors")**: Only in multi-sensor datasets. Whether an attribute should remain constant across all sensors for an object with a certain track ID. If false, the attribute can change on each sensor.
* **Sensors**: Only in multi-sensor datasets. Whether an attribute applies to 2D sensors, 3D sensors, or all sensors.

### Scene attributes

You can add scene attributes by clicking the "Edit image attributes" button. Scene attributes are not linked to a specific object, but rather to a frame or the scene as a whole.

### Link attributes

Todo

### In the labeling interface

When labeling, the object and scene attributes will be shown in the sidebar on the right. Scene attributes are always visible, while object attributes are only shown when an object is selected which has a category with object attributes.

![](<.gitbook/assets/image (4) (2).png>)

### Editing the configuration file directly

If you click on the "Raw" tab, you can see the configuration in JSON format. You can copy-paste this configuration from one dataset to another, or update it programmatically using the [Python SDK](https://sdkdocs.segments.ai/en/latest/client.html). The configuration should adhere to the format defined [here](reference/categories-and-task-attributes.md).
