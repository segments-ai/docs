# Configuring the label editor

Once you've created a dataset, you can further configure the labeling interface by editing the configuration file under **Settings** -&gt; **Labeling**.

You can also easily copy-paste this configuration file from one dataset to another.

```javascript
{
    "format_version": "0.1",
    "categories": [
        { // At the minimum, a category should have a name and category_id
            "name": "person",
            "category_id": 1
        },
        {
            "name": "car",
            "category_id": 2,
            "has_instances": true, // Whether category contains instances (person, car) or not (sky, road)
            "color": [33, 138, 33], // RGB color of the category
            "foo": "bar" // You can add custom key-value pairs that will be ignored
        },
        {
            "name": "traffic-light",
            "category_id": 3,
            "attributes": [ // Optional object-level attributes
                {
                    "name": "color",
                    "input_type": "radio",
                    "values": [
                        "green",
                        "yellow",
                        "red",
                    ]
                }
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

