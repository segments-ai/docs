# Add collaborators to a dataset

Go to **Settings -> Collaborators** to add collaborators to your dataset.

![](<../.gitbook/assets/image (21) (1) (1).png>)

### Permissions

Collaborators can have one of 4 roles: viewer, labeler, reviewer, manager and administrator. Each role has a different set of permissions:

<table><thead><tr><th width="186.50472062299832"> </th><th width="93.91015625" data-type="checkbox">Viewer</th><th width="97.56640625" data-type="checkbox">Labeler</th><th width="108.51953125" data-type="checkbox">Reviewer</th><th width="108.02734375" data-type="checkbox">Manager</th><th width="138.21484375" data-type="checkbox">Administrator</th></tr></thead><tbody><tr><td>View samples</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td></tr><tr><td>Label samples</td><td>false</td><td>true</td><td>true</td><td>true</td><td>true</td></tr><tr><td>Review samples</td><td>false</td><td>false</td><td>true</td><td>true</td><td>true</td></tr><tr><td>Delete and resolve issues</td><td>false</td><td>false</td><td>false</td><td>true</td><td>true</td></tr><tr><td>Add, update, delete collaborators</td><td>false</td><td>false</td><td>false</td><td>true</td><td>true</td></tr><tr><td>Edit sample priority and assigned labeler/reviewer</td><td>false</td><td>false</td><td>false</td><td>true</td><td>true</td></tr><tr><td>Add and delete samples</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td>View, add, delete releases</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td>Manage settings</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr></tbody></table>

Viewers can only open a sample in read-only mode with all editing actions disabled, except the creation of issues. On the dataset level, they can see the "Overview", "Samples" and "Issues" tabs.

Labelers and reviewers can only see the "Overview" tab of a dataset, where they can click the "Start labeling" and "Start reviewing" buttons depending on their role. Note that they cannot browse the samples on the Samples tab.

Managers and administrators can add collaborators to a dataset. Note that a manager cannot add a collaborator with an administrator role.

### Adding collaborators programmatically

You can also [add collaborators to a dataset using the Python SDK](https://sdkdocs.segments.ai/en/latest/client.html#add-a-dataset-collaborator).
