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
    ]
}
```

| Name               | Type                                                                               | Description                                                                |
| ------------------ | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `categories`       | `array` of [categories](categories-and-task-attributes.md#categories-format)       | **Required.** List of all possible categories for a label in this dataset. |
| `image_attributes` | `array` of [attributes](categories-and-task-attributes.md#object-attribute-format) | List of image-level attributes.                                            |

### Categories

```json
{
    "name": "car",
    "id": 1,
    "color": [33, 138, 33], // optional
    "has_instances": true, // optional
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

| Name            | Type                                                                                                                              | Description                                                                                          |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `name`          | `string`                                                                                                                          | **Required.** The name of the category.                                                              |
| `id`            | `int`                                                                                                                             | **Required.** The index of the category. <mark style="color:orange;">Should start at index 1!</mark> |
| `color`         | `array` of 3 `float` values in \[0, 255]                                                                                          | RGB color of the category                                                                            |
| `has_instances` | `boolean`                                                                                                                         | Whether the category contains instances (person, car) or not (sky, road)                             |
| `attributes`    | `array` of [attributes](categories-and-task-attributes.md#object-attribute-format)                                                | List of object-level attributes.                                                                     |
| `dimensions`    | <p><code>object</code>: {<br>    "x": <code>float</code>,<br>    "y": <code>float</code>,<br>    "z": <code>float</code><br>}</p> | Default XYZ dimensions of a new cuboid. Only valid in the point cloud cuboid editor.                 |
| ...             | ...                                                                                                                               | Other key-value pairs can be supplied, but will be ignored.                                          |

### Attributes

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
}
```

| Name            | Type                                                   | Description                                                                                              |
| --------------- | ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| `name`          | `string`                                               | **Required.** The name of the attribute.                                                                 |
| `input_type`    | `string`: `select` \| `text` \| `number` \| `checkbox` | **Required**. The type of the attribute.                                                                 |
| `values`        | `array` of `string`s                                   | **Required when** `input_type` **is** `select`**.** List of possible values.                             |
| `min`           | `string`                                               | Valid when `input_type` is `number`. The minimum value the attribute can be.                             |
| `max`           | `string`                                               | Valid when `input_type` is `number`. The maximum value the attribute can be.                             |
| `step`          | `string`                                               | Valid when `input_type` is `number`. The step when incrementing/decrementing the value of the attribute. |
| `default_value` | `string` \| `boolean` depending on `input_type`        | The default value of the attribute.                                                                      |

#### Additional examples

```json
{
    "name": "description",
    "input_type": "text",
    "default_value": "A nice car." // optional
},
```

```json
{
    "name": "number_of_wheels",
    "input_type": "number",
    "min": "1", // optional
    "max": "20", // optional
    "step": "1", // optional
    "default_value": 4 // optional
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
