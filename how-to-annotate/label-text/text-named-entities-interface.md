# Text named entities interface

{% hint style="info" %}
When [creating a dataset](../../python-sdk.md#create-a-dataset) through the Python SDK, choose `text-named-entities as` the `task_type` to use this labeling interface.
{% endhint %}

## Label text with the mouse

* **Select a category** by clicking on it.
* **Add a label** by selecting characters or words. You can also label a single word by clicking on it.
* **Remove a label** by clicking on it.

## Label text with the keyboard

* **Selecting a category:**
  * Use the numbers `1-9` to select a category.
* **Adding a label:**
  * By default no text is selected - **press the `right arrow` once** **to start using the keyboard** for labeling. Use the `left arrow` to move the selection by one word to the left and the `right arrow` to move the selection by one word to the right.
  * Press `space` to add a label.
  * Use `shift + right arrow` to add a character to the end of the selection and `shift + left arrow` to remove a character from the end of the selection.
  * Use `shift + cmd/ctrl + right arrow` to add a word to the end of the selection and `shift + cmd/ctrl + left arrow` to remove a word from the end of the selection.
* **Removing a label:**
  * Move the selection to a word in a label and press `backspace` to remove the label.
