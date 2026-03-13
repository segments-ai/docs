# Open a sample in read-only mode

## Overview

A sample can be opened in read-only mode which restricts the actions of the user in the interface.

## How it works

The read-only mode disables the following actions in the interface:

* All annotation hotkeys (draw, edit, copy/paste...)
* Any action implying a modification
  * Creating or modifying objects and keyframes
  * All destructive actions (delete, merge, split tracks)
* Saving a sample<br>

The user can still:&#x20;

* View and browse the annotations
* Use navigation, camera controls, display toggle and selection hotkeys
* View and create issues
* Modify its visualization settings in the right sidebar

## How to use the read-only mode

There are two ways to trigger the read-only mode:

* Assign the Viewer role from the dataset Collaborators settings page (More information about roles settings [here](https://docs.segments.ai/guides/add-collaborators-to-a-dataset)). Opening a sample with this user role will enforce the read-only mode.
* Manually open a sample in read-only mode from the `Samples` tab, by clicking on the eye icon on one of listed samples at mouse hover.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-12 at 10.47.54.png" alt=""><figcaption></figcaption></figure>

Note that while using the read-only mode manually, the web page URL is appended with the query parameter `readOnly=true` . It can be useful to share a link using the read-only mode. However, if you refresh the page, the read-only mode is not used by default (except when in the Viewer role, as described above).

Viewers cannot edit annotations, use labeling shortcuts, or modify any dataset settings.

