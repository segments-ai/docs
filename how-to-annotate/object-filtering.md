# Object filtering

Across all task types you can use the filter box in the sidebar to isolate specific annotations based on their _category_ and/or _attributes_ (e.g., showing only _stationary vehicles_). It also allows for batch hide/show all filtered annotations simultaneously with a single click to instantly clear background clutter.

The filter is located in the right sidebar, under **Objects** or **Tracks** section (for sequence datasets).

<figure><img src="../.gitbook/assets/Screenshot 2026-07-07 at 10.01.50.png" alt="" width="375"><figcaption></figcaption></figure>

The active filter state is automatically appended to the browser's URL (e.g., `?object-filter=[{"type":"category","value":"human.pedestrian.adult"},{"type":"visibility","value":"visible"}]`). This enables you to copy and share the URL so teammates or QA reviewers land on the exact same filtered view.
