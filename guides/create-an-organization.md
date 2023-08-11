---
description: >-
  Organizations are shared accounts where teams can easily collaborate across
  many datasets.
---

# Create an organization

Each person that uses Segments signs into a personal account. Multiple personal accounts can collaborate on shared datasets by joining the same organization account, which owns the datasets. Administrators can manage memberships and create datasets within an organization.

## Create an organization

To create a new organization, click the plus-icon in the top navigation bar and select “New organization”. Choose a username for your organization in the next screen.

![](<../.gitbook/assets/image (8) (2) (1).png>)![](<../.gitbook/assets/image (25) (2).png>)

When clicking the “Create organization” button, you will be taken to the organization account page.

![](<../.gitbook/assets/image (26).png>)

Each member of an organization can quickly access it via the profile button in the top navigation bar.

![](<../.gitbook/assets/image (13) (1).png>)

## Create a dataset within an organization

{% hint style="info" %}
Only organization administrators can create new datasets within the organization
{% endhint %}

To create a new dataset within an organization, go to the organization account page and click the “New dataset” button. In the popup window, you will see that the organization is selected as the owner of the dataset.

![](<../.gitbook/assets/image (24).png>)

Alternatively you can create a new dataset by clicking the plus-icon in the top navigation bar, selecting “New dataset”, and changing the owner from your personal account to your organization account manually.

## Manage organization members

As an administrator, you can add new members to the organization and assign them a role.

From the organization account page, go to the “Settings” tab and click the “Members” subtab. Type the username of the user you want to add, and click “Add member”.

![](<../.gitbook/assets/image (23).png>)

For each member, you can assign an “Organization role” and a “Default dataset role”.

### Organization role

The organization role determines the role of a user within the organization itself.

There are only two organization roles, _member_ or _administrator_. Their permissions are as follows.

<table><thead><tr><th width="226.48909562299832"> </th><th width="150" data-type="checkbox">Member</th><th data-type="checkbox">Administrator</th></tr></thead><tbody><tr><td>Access the organization account and see other members</td><td>true</td><td>true</td></tr><tr><td>Create new organization datasets</td><td>false</td><td>true</td></tr><tr><td>Manage memberships and settings</td><td>false</td><td>true</td></tr></tbody></table>

### Default dataset role

When creating a new dataset within an organization, all organization members will be added as collaborators to these datasets according to their _default dataset role_. Dataset collaborator roles are described in [add-collaborators-to-a-dataset.md](add-collaborators-to-a-dataset.md "mention").

Choose “None (do not add)” if you don’t want to add a member as a collaborator to new datasets by default.

## Leave an organization

As a member you can leave an organization by going to the _organizations_ tab on your own settings page, and clicking the "Leave organization" button.

![](<../.gitbook/assets/image (20).png>)
