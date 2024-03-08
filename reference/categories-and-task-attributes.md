# Categories and task attributes

When [editing the category and task attribute configuration directly](https://docs.segments.ai/guides/configure-label-editor), you need to adhere to the following format:

## Configuration format

```json
{
    "format_version": "0.1",
    "categories": [
        { ... },
        { ... },
        { ... }
    ],
    "image_attributes": [ // optional image-level attributes
        { ... },
        { ... },
        { ... }
    ],
    "circle_radius": 50 // optional ego circle in 3D vector interfaces
}
```

| Name               | Type                                                                 | Description                                                                                                                                                    |
| ------------------ | -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `categories`       | `array` of [categories](categories-and-task-attributes.md#category)  | **Required.** List of all possible categories for a label in this dataset.                                                                                     |
| `image_attributes` | `array` of [attributes](categories-and-task-attributes.md#attribute) | List of image-level attributes.                                                                                                                                |
| `circle_radius`    | `int`                                                                | The radius of the circle around the ego position in the 3D cuboid and vector interface. Can be used to indicate a region in which objects should be annotated. |

{% hint style="warning" %}
The `categories` array should contain at least one category.
{% endhint %}

### Category

```json
{
    "name": "car",
    "id": 1,
    "color": [33, 138, 33], // optional
    "has_instances": true, // optional
    "lock_dimensions": true, // optional, false by default
    "lock_rotation": true, // optional, false by default
    "lock_position": true, // optional, false by default
    "attributes": [ // optional object-level attributes
        { ... },
        { ... },
        { ... }
    ],
    "dimensions": {  // optional, only valid in the point cloud cuboid editor
        "x": 0.6564944386482239,
        "y": 1.3789583444595337,
        "z": 1.6037739515304565
    },
    "foo": "bar" // optional custom key-value pairs. These will be ignored.
}
```

| Name            | Type                                                                                                                              | Description                                                                                                                                                                                                                                                          |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`          | `string`                                                                                                                          | **Required.** Name of the category.                                                                                                                                                                                                                                  |
| `id`            | `int`                                                                                                                             | **Required.** Index of the category.                                                                                                                                                                                                                                 |
| `color`         | `array` of 3 `float` values in \[0, 255]                                                                                          | RGB color of the category.                                                                                                                                                                                                                                           |
| `has_instances` | `boolean`                                                                                                                         | Whether the category contains instances (person, car) or not (sky, road)                                                                                                                                                                                             |
| `attributes`    | `array` of [attributes](categories-and-task-attributes.md#object-attribute-format)                                                | List of object-level attributes.                                                                                                                                                                                                                                     |
| `dimensions`    | <p><code>object</code>: {<br>    "x": <code>float</code>,<br>    "y": <code>float</code>,<br>    "z": <code>float</code><br>}</p> | Default XYZ dimensions of a new cuboid. Only valid in the point cloud cuboid editor (see [#create-a-cuboid-with-default-dimensions](../how-to-annotate/label-3d-point-clouds/3d-point-cloud-cuboid-interface.md#create-a-cuboid-with-default-dimensions "mention")). |
| ...             | ...                                                                                                                               | Other key-value pairs can be supplied, but will be ignored.                                                                                                                                                                                                          |

### Attribute

```json5
{
    "name": "color",
    "input_type": "select",
    "values": [
        "green",
        "yellow",
        "red"
    ],
    "default_value": "red" // optional
    "is_mandatory": true // optional
    "is_track_level: true // for sequence interfaces, optional
}
```

| Name             | Type                                                   | Description                                                                                                                                                                     |
| ---------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`           | `string`                                               | **Required.** Name of the attribute.                                                                                                                                            |
| `input_type`     | `string`: `select` \| `text` \| `number` \| `checkbox` | **Required.** Type of the attribute.                                                                                                                                            |
| `values`         | `array` of `string`s                                   | **Required when** `input_type` **is** `select`**.** List of possible values.                                                                                                    |
| `min`            | `string`                                               | Valid when `input_type` is `number`. Minimum value the attribute can be.                                                                                                        |
| `max`            | `string`                                               | Valid when `input_type` is `number`. Maximum value the attribute can be.                                                                                                        |
| `step`           | `string`                                               | Valid when `input_type` is `number`. Step when incrementing/decrementing the value of the attribute.                                                                            |
| `default_value`  | `string` \| `boolean` depending on `input_type`        | Default value of the attribute.                                                                                                                                                 |
| `is_mandatory`   | `boolean`                                              | Valid when `input_type` is `select`, `text` or `number`. Whether the attribute is mandatory. Mandatory attributes raise a warning when not filled in.                           |
| `is_track_level` | `boolean`                                              | Valid in sequence datasets. Whether an attribute should remain constant across all frames for an object with a certain track ID. If false, the attribute can change each frame. |

#### Additional examples

```json
{
    "name": "description",
    "input_type": "text",
    "default_value": "A nice car.", // optional
    "is_mandatory": true // optional
},
```

```json
{
    "name": "number_of_wheels",
    "input_type": "number",
    "min": "1", // optional
    "max": "20", // optional
    "step": "1", // optional
    "default_value": 4, // optional
    "is_mandatory": true // optional
},
```

```json
{
    "name": "is_electric",
    "input_type": "checkbox",
    "default_value": false // optional
}
```

{% hint style="warning" %}
Note that the inline comments in the examples should be left out, as comments of the form`//…` or `/*…*/` are not allowed in JSON.
{% endhint %}
