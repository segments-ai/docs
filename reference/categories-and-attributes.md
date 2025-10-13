# Categories and attributes

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
    "circle_radius": 50, // optional ego circle in 3D vector interfaces
    "warning_rules": [ // optional set of rules that trigger warnings
        { ... },
        { ... },
        { ... }
    ]
}
```

| Name               | Type                                                                   | Description                                                                                                                                                    |
| ------------------ | ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `categories`       | `array` of [categories](categories-and-attributes.md#category)         | **Required.** List of all possible categories for a label in this dataset.                                                                                     |
| `image_attributes` | `array` of [attributes](categories-and-attributes.md#attribute)        | List of image-level attributes.                                                                                                                                |
| `circle_radius`    | `int`                                                                  | The radius of the circle around the ego position in the 3D cuboid and vector interface. Can be used to indicate a region in which objects should be annotated. |
| `warning_rules`    | `array` of  [warning rules](categories-and-attributes.md#warning-rule) | List of rules that should generate warnings running a check on a sample                                                                                        |

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
    "link_attributes": [ // optional link attributes
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

| Name              | Type                                                                                                                              | Description                                                                                                                                                                                                                                                          |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`            | `string`                                                                                                                          | **Required.** Name of the category.                                                                                                                                                                                                                                  |
| `id`              | `int`                                                                                                                             | **Required.** Index of the category.                                                                                                                                                                                                                                 |
| `color`           | `array` of 3 `float` values in \[0, 255]                                                                                          | RGB color of the category.                                                                                                                                                                                                                                           |
| `has_instances`   | `boolean`                                                                                                                         | Whether the category contains instances (person, car) or not (sky, road)                                                                                                                                                                                             |
| `attributes`      | `array` of [attributes](categories-and-attributes.md#object-attribute-format)                                                     | List of object-level attributes.                                                                                                                                                                                                                                     |
| `link_attributes` | `array` of [attributes](categories-and-attributes.md#object-attribute-format)                                                     | List of link attributes when the object is on the "from" side.                                                                                                                                                                                                       |
| `dimensions`      | <p><code>object</code>: {<br>    "x": <code>float</code>,<br>    "y": <code>float</code>,<br>    "z": <code>float</code><br>}</p> | Default XYZ dimensions of a new cuboid. Only valid in the point cloud cuboid editor (see [#create-a-cuboid-with-default-dimensions](../how-to-annotate/label-3d-point-clouds/3d-point-cloud-cuboid-interface.md#create-a-cuboid-with-default-dimensions "mention")). |
| ...               | ...                                                                                                                               | Other key-value pairs can be supplied, but will be ignored.                                                                                                                                                                                                          |

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

### Warning rule

Different warning rules can be configured. Each rule type can be added multiple times for different categories / category groups according to the rule specifications. Currently, the following list of options is allowed

* `intersecting-cuboids`
* `cuboid-dimension-limits`

Each rule has its own set of properties to fully configure it.

#### Intersecting cuboids

An intersecting cuboids rule should either have an `excluded_set_of_categories`  prop or an `excluded_categories` prop, not both.

<table><thead><tr><th width="233">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code></td><td><code>string: intersecting-cuboids</code></td><td><strong>required:</strong> Set this property to <code>intersecting-cuboids</code> when adding a rule to warn for intersecting cuboids.    </td></tr><tr><td><code>excluded_set_of_categories</code></td><td><code>array of numbers</code></td><td>Add categories to this list that are allowed to intersect with each other.<br>Note that intersections between elements of the exact same category will still raise warnings.</td></tr><tr><td><code>excluded_categories</code></td><td><code>array of numbers</code></td><td>Add categories to this list that should not trigger warnings when they intersect with any category (including their own category).</td></tr></tbody></table>

```json

// Activate the rule without exclusions
{
    "name": "intersecting-cuboids",
    "excluded_categories": [],
}

// Activate the rule, but exclude intersections between categories 1 and 3, 1 and 5,
// and between 3 and 5 from raising warnings
{
    "name": "intersecting-cuboids",
    "excluded_set_of_categories": [1, 3, 5],
}

// Activate the rule, but don't raise warnings when category 3 intersects
{
    "name": "intersecting-cuboids",
    "excluded_categories": [3],
}
```

#### Cuboid dimension limits

An intersecting cuboids rule should either have an `excluded_set_of_categories`  prop or an `excluded_categories` prop, not both.

<table><thead><tr><th width="169">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code></td><td><code>string: cuboid-dimension-limits</code></td><td><strong>required:</strong> Set this property to <code>cuboid-dimension-limits</code> when adding a rule to warn for invalid dimensions on cuboids.    </td></tr><tr><td><code>categories</code></td><td><code>array of numbers</code></td><td>Add categories to this list for which this rule should apply.<br>Pass an empty array to apply this rule to all categories.</td></tr><tr><td><code>min</code></td><td><code>object: {</code><br>    <code>"x": float | undefined,</code><br>    <code>"y": float | undefined,</code><br>    <code>"z": float | undefined</code><br><code>}</code></td><td>Set the minimum dimensions allowed for cuboids.<br>It is not required to set all x, y and z values. Only set the values that you want to be warned for.</td></tr><tr><td><code>max</code></td><td><code>object: {</code><br>    <code>"x": float | undefined,</code><br>    <code>"y": float | undefined,</code><br>    <code>"z": float | undefined</code><br><code>}</code></td><td>Set the maximum dimensions allowed for cuboids.<br>It is not required to set all x, y and z values. Only set the values that you want to be warned for.</td></tr></tbody></table>



```json

// Activate the rule and warn for any cuboid with an x value larger than 10
{
    "name": "cuboid-dimension-limits",
    "max" {
        "x": 10
    }
}

// Activate the rule and warn for any cuboid in category 1 or 2
// with an x or y value smaller than or a z value larger than 3
{
    "name": "cuboid-dimension-limits",
    "categories": [1, 2],
    "min": {
        "x": 0.5,
        "y": 0.5
    },
    "max" {
        "x": 3
    }
}
```

{% hint style="warning" %}
Note that the inline comments in the examples should be left out, as comments of the form`//…` or `/*…*/` are not allowed in JSON.
{% endhint %}
