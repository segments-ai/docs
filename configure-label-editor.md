# Configuring the label editor

Once you've created a dataset, you can further configure the labeling interface by editing the configuration file under **Settings** -&gt; **Labeling**.

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
                    "input_type": "radio",
                    "values": [
                        "green",
                        "yellow",
                        "red"
                    ]
                },
                {
                    "name": "visibility",
                    "input_type": "radio",
                    "values": [
                        "good",
                        "bad"
                    ]
                }
            ]
        }
    ],
    "image_attributes": [ // Optional image-level attributes
        {
            "name": "scene_type",
            "input_type": "radio",
            "values": [
                "highway",
                "urban",
                "countryside"
            ]
        },
        {
            "name": "weather",
            "input_type": "radio",
            "values": [
                "sunny",
                "cloudy",
                "rainy"
            ]
        }
    ]
}
```

{% hint style="warning" %}
Note that the inline comments in this example configuration file should be left out, as comments of the form`//…` or `/*…*/` are not allowed in JSON.
{% endhint %}

