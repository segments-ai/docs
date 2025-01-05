# Labeling metrics

To get accurate labeling metrics, we recommend using the "Start labeling" and "Start reviewing" buttons for labeling. This will automatically assign each team member a sample from the label/review queue according to the rules described [here](label-queue-mechanics.md). It also ensures that samples that got rejected by the reviewer go back to the original labeler and then back to that same reviewer after correction, creating a tight feedback loop.

Using the Start labeling/reviewing workflow also ensures that timings are properly categorized as either _label time_ or _review time_. If you make any changes to a sample by directly opening it from the Samples tab and pressing the Save button, this gets categorized as _edit time_.

On the Insights tab of a dataset we show a number of labeling metrics, both on a per-user level (# labeled, total label time, average label time, # reviewed, total review time, average review time, # edited, total edit time, average edit time) and on a per-sample level (label time, review time, edit time, # rejected, # frames, # annotations).

On the Insights tab of an _organization_, you can see the per-user metrics aggregated across all datasets in that organization.

You can download these aggregated metrics as a csv/json/excel file directly from the webapp or programmatically through the API or Python SDK (reach out to us for more information).

## Advanced: workunits

Behind the scenes, the metrics are calculated from _workunits_.&#x20;

A workunit represents a piece of labeling work done by a dataset collaborator on a certain sample. It is initiated when a sample is loaded in the interface, and is saved when a label is created or saved. This is generally in any of the following three events:

1. A labeler submits a sample via the 'start labeling' workflow
2. A reviewer accepts or rejects a sample via the 'start reviewing' workflow
3. A manager edits and saves a sample after opening it in the samples tab

A workunit contains the following fields:

* `uuid`: unique id of the workunit.
* `created_at`: creation time of the workunit. I.e., the time when the user saved or submitted the sample.
* `created_by`: the user who created the workunit.
* `work_type`: one of:
  * **label** (sample opened in Start labeling workflow)
  * **review** (sample opened in Start Reviewing workflow)
  * **normal** (sample opened directly through the samples tab)
* `time`: the amount of time in milliseconds since the sample loaded, or since the previous time the save button was pressed, whichever is shorter. Note that this does not include inactive time, see below. A more appropriate name for this field would be `active_time`, but it's `time` because of legacy reasons. The metrics on the Insights tab are calculated using this value.
* `inactive_time`: the amount of inactive time during this workunit. Inactive time is defined as the sum of all time intervals between two mouse clicks or keyboard presses that are larger than the inactivity threshold (5 minutes).
* `next_label_status`: the new label status of the label, i.e. after the save/accept/reject/skip button is pressed.

If you want to run your own custom metrics calculations, you can [fetch the list of workunits of a dataset via the Python SDK](https://sdkdocs.segments.ai/en/latest/client.html#list-workunits).
