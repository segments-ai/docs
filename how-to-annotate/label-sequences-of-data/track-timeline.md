# Track timeline

The track timeline is the main interface for managing annotations across frames in a sequence. It's always visible at the bottom of the editor.

## Overview

The timeline displays your annotations as horizontal rows (tracks) across time (frames), with each track showing:

* Track ID and category
* Where the object is present (colored bars)
* Keyframe locations (diamond icons)
* Track attributes (when selected)

## Timeline states

The timeline can be displayed in two states:

**Collapsed view:**

* The timeline appears in a compact form by default
* Shows basic track information and frame columns

**Expanded view:**

* Click the **Details** button to expand the timeline
* Reveals additional information and controls
* Provides more space for viewing tracks and attributes

{% hint style="info" %}
Use the expanded view when working intensively with keyframes or attributes. Use the collapsed view to maximize space for the main viewer.
{% endhint %}

## Timeline views

The timeline adapts its display based on your current selection:

### Tracks view

**Access:** No track selected + View dropdown = "Tracks"

Shows all tracks in your sequence with:

* One row per track
* Track ID and category name on the left
* Colored bars showing track visibility
* Keyframes marked with white diamonds (◆)
* Remove-keyframes marked with white crosses (×)

**Use this view to:**

* Get an overview of all objects in the sequence
* Compare timing between different tracks
* Select a track to work on

### Scene attributes view

**Access:** No track selected + View dropdown = "Scene attributes"

Shows scene-level attributes with:

* One row per scene attribute
* Attribute name on the left
* Editable cells for each frame

**Use this view to:**

* Label environmental conditions (weather, lighting, etc.)
* Add sequence-level metadata (recording location, camera settings, etc.)

### Single track view

**Access:** Select any track in the viewer (automatic)

Shows only the selected track with:

* The track row at the top
* Track attribute rows below (if attributes exist)
* View dropdown is disabled

**Use this view to:**

* Focus on labeling a specific object
* Edit track-specific attributes
* Work with keyframes for that track

{% hint style="info" %}
The timeline automatically switches to single track view when you select an object. Deselect the object (click in empty space) to return to the previous view. The track list is synchronized with the sidebar panel.
{% endhint %}

## Navigate between frames

### Navigation controls

The timeline header provides several ways to move between frames:

**Navigation buttons:**

* `◄`: Previous frame
* `►`: Next frame
* `◄◄`: Jump 5 frames backward
* `►►`: Jump 5 frames forward

**Direct selection:**

* Click on any frame column to jump directly to it

**Keyboard shortcuts:**

* Arrow keys: Move frame-by-frame
* Shift + Arrow keys: Jump multiple frames

**Visual feedback:**

* Active frame: Highlighted vertical column
* Hovered frame: Gray highlight when you hover over a frame

## Create tracks

When you add a new object in the viewer:

1. A track is automatically created with a unique track ID
2. A new row appears in the timeline (Tracks view)
3. A keyframe is created at the current frame
4. The track bar displays the track's visibility range using the same color as the object in the viewer

{% hint style="info" %}
Track IDs increment sequentially, starting from the highest existing track ID.
{% endhint %}

## Manage tracks

Right-click on any track row to open the context menu with these options:

### Update track ID

Change the track's ID across all frames. Useful for:

* Correcting incorrectly assigned IDs
* Aligning with external tracking data

See Use track IDs - Update a track ID for details.

### Merge with track

Combine two tracks into one. Useful for:

* Fixing tracking errors where one object was assigned multiple IDs
* Correcting splits that shouldn't have happened

{% hint style="warning" %}
Merging is only possible when both tracks have no overlapping keyframes.
{% endhint %}

See Use track IDs - Merge tracks for details.

### Remove track

Delete the entire track and all its annotations. This action:

* Removes all keyframes
* Deletes all attribute values
* Can be undone via undo history

{% hint style="info" %}
When a track is removed, the highest track ID becomes available for new objects.
{% endhint %}

### Split track

Divide a track into two separate tracks at the current frame. Useful for:

* Separating objects that were tracked as one
* Handling scenarios where one object becomes two

{% hint style="warning" %}
Splitting is only possible if there are keyframes before the current frame.
{% endhint %}

{% hint style="info" %}
Split track is only available in single-sensor sequences.
{% endhint %}

See Use track IDs - Split a track for details.

## Work with keyframes

### View keyframes

Keyframes appear as **white diamond icons (◆)** on the track bar. Each diamond marks a frame where you've defined the object's state.

Remove-keyframes appear as **white cross icons (×)** on blank spaces, marking frames where you've explicitly removed the object.

### Keyframe operations

The timeline supports several keyframe operations:

**Select keyframes:**

* Click on a keyframe to select it
* The viewer jumps to that frame automatically

**Move keyframes:**

* Drag keyframe diamonds to different frames
* Interpolation recalculates automatically
* Movement is constrained to segments where the object exists (within the colored bar)

**Delete keyframes:**

* Select a keyframe and press `Backspace`
* The keyframe is removed and interpolation adjusts

**Copy and paste keyframes:**

* Copy a keyframe's state and paste it to another frame
* Useful for duplicating complex object states

{% hint style="info" %}
Keyframe movement is constrained to preserve data integrity. You can only move keyframes within the track's visibility range.
{% endhint %}

{% hint style="info" %}
For detailed keyframe operations, see Use keyframe interpolation.
{% endhint %}

## Edit attributes in timeline

The timeline allows direct editing of attribute values without leaving the labeling interface.

### Track attributes

**When to see them:** Select a track

Track attribute rows appear below the track row, showing:

* Attribute name on the left
* One cell per frame (or one cell for sequence-level attributes)
* Cell type matches the attribute type (text, number, dropdown, checkbox, etc.)

**How to edit:**

1. Click on any cell
2. Enter or select the value
3. The value is saved automatically

**Synced across frames:**

* If enabled: Editing one cell updates all frames
* If disabled: Each frame can have a different value

### Scene attributes

**When to see them:** Deselect all tracks + View dropdown = "Scene attributes"

Scene attribute rows appear, showing:

* Attribute name on the left
* One cell per frame (frame-level) or one cell total (sequence-level)

**How to edit:** Same as track attributes — click and edit.

{% hint style="info" %}
For configuring attributes (synced vs not synced, frame-level vs sequence-level), see Configure the label editor.
{% endhint %}

## Timeline layout

### Sticky elements

As you scroll through the timeline:

* **Name column** stays visible on the left, so you always see track/attribute names
* **Navigation header** stays visible at the top, so controls are always accessible

### Scrolling

* **Horizontal scrolling:** View frames beyond the visible area (useful for long sequences)
* **Vertical scrolling:** View tracks beyond the visible area (only in all tracks view)

### Active frame indicator

The active frame is marked with a highlighted vertical column spanning the entire timeline height. This makes it easy to see your current position, especially when scrolling.









