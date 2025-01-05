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

<table><thead><tr><th width="258.3333333333333">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code></td><td><code>string</code></td><td><strong>Required.</strong> Name of the attribute.</td></tr><tr><td><code>input_type</code></td><td><code>string</code>: <code>select</code> | <code>text</code> | <code>number</code> | <code>checkbox</code></td><td><strong>Required.</strong> Type of the attribute.</td></tr><tr><td><code>values</code></td><td><code>array</code> of <code>string</code>s</td><td><strong>Required when</strong> <code>input_type</code> <strong>is</strong> <code>select</code><strong>.</strong> List of possible values.</td></tr><tr><td><code>min</code></td><td><code>string</code></td><td>Valid when <code>input_type</code> is <code>number</code>. Minimum value the attribute can be.</td></tr><tr><td><code>max</code></td><td><code>string</code></td><td>Valid when <code>input_type</code> is <code>number</code>. Maximum value the attribute can be.</td></tr><tr><td><code>step</code></td><td><code>string</code></td><td>Valid when <code>input_type</code> is <code>number</code>. Step when incrementing/decrementing the value of the attribute.</td></tr><tr><td><code>default_value</code></td><td><code>string</code> | <code>boolean</code> depending on <code>input_type</code></td><td>Default value of the attribute.</td></tr><tr><td><code>is_mandatory</code></td><td><code>boolean</code></td><td>Valid when <code>input_type</code> is <code>select</code>, <code>text</code> or <code>number</code>. Whether the attribute is mandatory. Mandatory attributes raise a warning when not filled in.</td></tr><tr><td><code>is_track_level</code></td><td><code>boolean</code></td><td>Valid in sequence datasets. Whether an attribute should remain constant across all frames for an object with a certain track ID. If false, the attribute can change on each frame.</td></tr><tr><td><code>synced_across_sensors</code></td><td><code>boolean</code></td><td>Valid in multi-sensor datasets. Whether an attribute should remain constant across all sensors for an object with a certain track ID. If false, the attribute can change on each sensor.</td></tr><tr><td><code>sensors</code></td><td><code>string</code>: <code>2D</code> |<code>3D</code>| <code>all</code></td><td>Valid in multi-sensor datasets. Whether an attribute applies to 2D sensors, 3D sensors, or all sensors.</td></tr></tbody></table>

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
