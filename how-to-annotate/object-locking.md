# Object locking

Lock an object to prevent any modification (move, resize, category change, delete). The cursor changes to a lock icon when hovering over a locked object.

* `Shift + R` - toggle lock on the active object
* Or click the lock icon in the right sidebar

<figure><img src="../.gitbook/assets/Screenshot 2026-07-07 at 11.41.08 (1).png" alt="" width="373"><figcaption></figcaption></figure>

Note that

* Locking is **local**, meaning others will not see any locks that you've placed on objects
* Locking is **temporary**, meaning locks are not saved and are reset on reload

Locking can be used for accuracy purposes to avoid unintended modification, or for structured QA processes.

If you want all objects to be locked, you might benefit more from the [read-only](../guides/open-a-sample-in-read-only-mode.md) mode.

