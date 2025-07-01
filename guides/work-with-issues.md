# Work with issues

## Creating Issues

Both labelers and reviewers can open a new issue on a sample by clicking the <img src="../.gitbook/assets/issues icon.png" alt="bubble icon depicting issues with a number next to it" data-size="line"> icon in the top navigation bar. For example, a labeler might open an issue when unsure how to label something, or a reviewer might open one after finding a mistake in a labeled sample.

When an issue is created, it automatically becomes an "open" issue, indicated by a red number next to to message icon.

An issue must include a description. You can also optionally add screenshots and link an issue to specific context like sensor, frame, object, track, attributes, or a location. Any available fields will be pre-filled based on your current selection (e.g., the current sensor).&#x20;

When visualizing an issue, a user can see all the data linked to it. By clicking on the tag, the user is brought directly to the relevant context (e.g., frame, sensor).

### Managing Issues

Reviewers and admins can "resolve" issues by clicking the checkmark icon. A resolved issue is indicated with a green icon.

Issue authors and admins can edit an issue's description or delete an issue by clicking the ellipsis icon and choosing the action from the dropdown menu.&#x20;

Everyone can add replies to an issue, and only reply authors can delete their own replies. This feature enables back-and-forth communication between labelers and reviewers. Remember that rejected samples always return to the original labeler, while corrected samples go back to the original reviewer.

Reviewers and admins have access to an issues panel, where they can filter issues by "resolved," "unresolved," or "all."

<figure><img src="../.gitbook/assets/Screenshot 2025-06-25 at 13.54.21.png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2025-06-25 at 13.56.28.png" alt=""><figcaption></figcaption></figure>

### Anchoring Issues

{% hint style="warning" %}
This functionality is not yet available in the image segmentation interface
{% endhint %}

For more precision, optional tools are available to anchor an issue to specific elements. An issue can be linked to:

1. A track (and optionally a specific track attribute)
2. A specific location in the point cloud or image
3. The scene itself (and optionally a specific scene attribute)

<figure><img src="../.gitbook/assets/Screenshot 2025-06-25 at 16.57.07.png" alt="" width="563"><figcaption><p>Link an issue to a specific point or pixel</p></figcaption></figure>

