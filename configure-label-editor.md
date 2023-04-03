# Configure the label editor

Once you have created a dataset, you can further configure the labeling interface under **Settings** -> **Labeling** -> **Categories:**

![](<.gitbook/assets/image (11).png>)

Here you can set the color, name, and description for each category. You can also add one or more object-level attributes to a category by expanding its row, or add image-level attributes by clicking the button "Edit image attributes".&#x20;

Attributes come in 4 types: select box, text, number, and checkbox. You can optionally set a default value for each attribute or make them mandatory.

In the label editor, the object-level and image-level attributes will be shown in the sidebar on the right. The image-level attributes are always visible, while the object-level attributes are only shown when an object is selected and has a category with object-level attributes.

![](<.gitbook/assets/image (4) (2).png>)

### Editing the configuration file directly

If you click on the "Raw" tab, you can see the configuration in JSON format. You can copy-paste this configuration from one dataset to another, or update it programmatically using the [Python SDK](python-sdk.md#create-a-dataset). The configuration should adhere to the format defined [here](reference/categories-and-task-attributes.md).
