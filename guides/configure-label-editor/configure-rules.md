---
description: >-
  In the dataset settings, rules can be configured to help spot potential issues
  early by raising warnings. Currently, the rules that can be added are only
  applicable to cuboids.
---

# Configure rules

{% hint style="info" %}
[More info about how to use the warning system while labeling / reviewing](../../how-to-annotate/use-the-warning-system.md)
{% endhint %}

## Configuration

Go to your dataset settings into the labeling tab. Scroll down the page to the warnings section (just after the categories section).

Here you can enable the intersecting cuboids rule and / or the cuboid dimension rules.

<figure><img src="../../.gitbook/assets/warnigs-config-empty.jpg" alt=""><figcaption></figcaption></figure>

### Intersecting cuboids

<figure><img src="../../.gitbook/assets/warnigs-config-intersecting-1.jpg" alt=""><figcaption></figcaption></figure>

Excluded groups are groups of categories that should not raise a warning when they intersect with each other. A common example is a person on a bicycle.

Excluded categories are a set of categories that the rule should not be applied to at all. Add categories here that should be ignored during the check for intersecting cuboids.

Here's an example of a configuration.

<figure><img src="../../.gitbook/assets/warnigs-config-intersecting-2.jpg" alt=""><figcaption></figcaption></figure>

### Cuboid dimensions

Configure rules that can warn users when cuboids exceed certain limits. Only fields that are filled in are checked.

This can be applied on a global scale by adding a rule without setting any categories on it.

<figure><img src="../../.gitbook/assets/warnigs-config-cuboid-2.jpg" alt=""><figcaption></figcaption></figure>

You can also configure more granular limits for groups of categories.

<figure><img src="../../.gitbook/assets/warnigs-config-cuboid-1.jpg" alt=""><figcaption></figcaption></figure>





