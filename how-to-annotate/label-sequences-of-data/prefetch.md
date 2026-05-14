# Prefetch

When using the labeling interface, only the necessary assets (e.g. point cloud files, image files) are fetched matching the current active frame. In many cases, when working on a sample extensively, many frames will be accessed eventually.

To improve the experience and reduce waiting time for fetching and loading assets, the assets can be prefetched proactively. (In multisensor datasets, prefetching happens on a per sensor level.)

Prefetching can be done by clicking the prefetch button in the timeline.

<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

In the settings in the sidebar, the prefetching can be configured to activate automatically on sample load (and on sensor switch in multisensor datasets).

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Prefetched assets are [cached on disk](../../guides/caching-assets.md) so that repeated access to frequently used assets loads faster.
