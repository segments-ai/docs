# Configure the label editor

Once you've created a dataset, you can further configure the labeling interface under **Settings** -> **Labeling** -> **Categories:**

![](<../.gitbook/assets/image (11).png>)

Here you can set the color, name and description for each category. You can also add one or more object-level attributes to a category by expanding its row, or add image-level attributes by clicking the button "Edit image attributes".&#x20;

Attributes come in 4 types: select box, text, number and checkbox. You can optionally set a default value for each attribute or make them mandatory.

### Editing the configuration file directly

If you click on the "Raw" tab, you can see the configuration in JSON format. You can copy-paste this configuration from one dataset to another, or update it programmatically using the [Python SDK](../reference/python-sdk.md#create-a-dataset).

The format is defined as follows:

```javascript
{
    "format_version": "0.1",
    "categories": [
        { // At the minimum, a category should have a name and id
            "name": "person",
            "id": 1
        },
        {
            "name": "car",
            "id": 2,
            "has_instances": true, // Whether the category contains instances (person, car) or not (sky, road)
            "color": [33, 138, 33], // RGB color of the category
            "foo": "bar" // You can add custom key-value pairs. These will be ignored.
        },
        {
            "name": "traffic-light",
            "id": 3,
            "attributes": [ // Optional object-level attributes
                {
                    "name": "color",
                    "input_type": "select",
                    "values": [
                        "green",
                        "yellow",
                        "red"
                    ],
                    "default_value": "red" // optional
                },
                {
                    "name": "description",
                    "input_type": "text",
                    "default_value": "A nice car." // optional
                },
                {
                    "name": "number_of_wheels",
                    "input_type": "number",
                    "min": "1",
                    "max": "20",
                    "step": "1",
                    "default_value": 4 // optional
                },
                {
                    "name": "is_",
                    "input_type": "checkbox",
                    "default_value": false // optional
                }
            ]
        }
    ],
    "image_attributes": [ // Optional image-level attributes
        {
            "name": "scene_type",
            "input_type": "select",
            "values": [
                "highway",
                "urban",
                "countryside"
            ],
            "default_value": "highway" // optional
        },
        {
            "name": "description",
            "input_type": "text",
            "default_value": "A nice sunny highway scene." // optional
        },
        {
            "name": "visibility",
            "input_type": "number",
            "min": "0.0",
            "max": "1.0",
            "step": "0.01",
            "default_value": 0.8 // optional
        },
        {
            "name": "sunny",
            "input_type": "checkbox",
            "default_value": true // optional
        }
    ]
}
```

{% hint style="warning" %}
Note that the inline comments in this example configuration file should be left out, as comments of the form`//…` or `/*…*/` are not allowed in JSON.
{% endhint %}
