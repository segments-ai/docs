---
description: >-
  With the search bar, you can search for samples by their name, metadata
  attributes, and label content.
---

# Search functionality

![Search for images by label content](.gitbook/assets/image.png)

## Search syntax

To search by sample name, just type the full or partial name of a sample.

To search by metadata attribute, use the `key:value` syntax.

To search by number of objects of a category in a labelset, use the `labelset.category:=value` syntax, or  `labelset.total_count:=value` to search by total number of objects.

For string values, use the `:` operator. For numeric values, use the operators `:=`,`:>`, `:>=`, `:<` and `:<=` to search for values that are equal to, greater than, greater than or equal to, less than, and less than or equal to another value.

Queries can be combined by separating them with a space. They will be ANDed together.

## Examples

| Examples |
| :--- |
| **image\_grayscale** matches samples with the word "image\_grayscale" in their name. |
| **city:london** matches samples with a metadata attribute "city" set to "london". |
| **vehicle\_id:&gt;3** matches samples with a metadata attribute "vehicle\_id" set to a value larger than 3. |
| **ground-truth.car:&gt;=5** matches samples where the "ground-truth" label contains 5 or more "car" objects. |
| **my-predictions.car:&lt;5** matches samples where the "my-predictions" label contains less than 5 "car" objects. |
| **my-predictions.total\_count:&lt;=20** matches samples where the "my-predictions" label contains 20 or fewer objects in total. |
| **city:london ground-truth.car:&gt;0 my-predictions.car:=0** matches samples where metadata attribute "city" is set to "london" AND the "ground-truth" label contains more than 0 "car" objects AND the "my-predictions" label contains 0 "car" objects. |



