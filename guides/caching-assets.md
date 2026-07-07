# Caching assets

A dedicated cache is used to store sample point cloud files and images to disk. This allows recently visited samples to load more quickly by loading cached assets from disk rather than downloading them new.&#x20;

For samples in sequence datasets, assets can be proactively [prefetched](../how-to-annotate/label-sequences-of-data/prefetch.md).

Assets accessed in the past 7 days are retained and the maximum size is capped at 10 GB.

If needed, the cache can be refreshed or cleared from the settings sidebar.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-07 at 10.56.06.png" alt=""><figcaption></figcaption></figure>
