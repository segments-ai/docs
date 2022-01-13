# Add collaborators to a dataset

Go to **Settings -> Collaborators** to add collaborators to your dataset.

![](<../.gitbook/assets/image (21) (1).png>)

### Permissions

Collaborators can have 3 roles: labeler, reviewer and administrator. Each role has different permissions:

<table><thead><tr><th></th><th data-type="checkbox">Labeler</th><th data-type="checkbox">Reviewer</th><th data-type="checkbox">Administrator</th></tr></thead><tbody><tr><td>Label samples</td><td>true</td><td>true</td><td>true</td></tr><tr><td>Review samples</td><td>false</td><td>true</td><td>true</td></tr><tr><td>Manage samples (view, upload, delete)</td><td>false</td><td>false</td><td>true</td></tr><tr><td>Manage releases (view, create, delete)</td><td>false</td><td>false</td><td>true</td></tr><tr><td>Manage settings</td><td>false</td><td>false</td><td>true</td></tr></tbody></table>

Labelers and reviewers can only see the "Overview" tab of a dataset, where they can click the "Start labeling" and "Start reviewing" buttons depending on their role. Note that they cannot browse the samples on the Samples tab.

### Adding collaborators programmatically

You can also [add collaborators to a dataset using the Python SDK](../python-sdk.md#add-a-collaborator-to-a-dataset).
