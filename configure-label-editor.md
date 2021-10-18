# Configuring the label editor

Once you've created a dataset, you can further configure the labeling interface by editing the configuration file under **Settings** -> **Labeling**.

You can also copy-paste configuration files from one dataset to another, or update them through the API or SDK.

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
