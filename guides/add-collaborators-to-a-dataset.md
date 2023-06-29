# Add collaborators to a dataset

Go to **Settings -> Collaborators** to add collaborators to your dataset.

![](<../.gitbook/assets/image (21) (1) (1).png>)

### Permissions

Collaborators can have one of 4 roles: labeler, reviewer, manager and administrator. Each role has a different set of permissions:

<table><thead><tr><th width="254.48909562299832"> </th><th width="111" data-type="checkbox">Labeler</th><th width="115" data-type="checkbox">Reviewer</th><th width="125" data-type="checkbox">Manager</th><th data-type="checkbox">Administrator</th></tr></thead><tbody><tr><td>Label samples</td><td>true</td><td>true</td><td>true</td><td>true</td></tr><tr><td>Review samples</td><td>false</td><td>true</td><td>true</td><td>true</td></tr><tr><td>Manage samples (view, upload, delete) and issues</td><td>false</td><td>false</td><td>true</td><td>true</td></tr><tr><td>Manage releases (view, create, delete)</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td>Manage settings</td><td>false</td><td>false</td><td>false</td><td>true</td></tr></tbody></table>

Labelers and reviewers can only see the "Overview" tab of a dataset, where they can click the "Start labeling" and "Start reviewing" buttons depending on their role. Note that they cannot browse the samples on the Samples tab.

### Adding collaborators programmatically

You can also [add collaborators to a dataset using the Python SDK](../python-sdk.md#add-a-collaborator-to-a-dataset).
