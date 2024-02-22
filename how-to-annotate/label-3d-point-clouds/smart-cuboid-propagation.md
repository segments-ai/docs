# Smart cuboid propagation

Smart cuboid propagation automatically propagates a cuboid frame by frame. This can help you save time when annotating dynamic objects that do not move linearly. For linear movement, simply use [keyframe interpolation](../label-sequences-of-data/use-keyframe-interpolation.md).

## Automatically propagate a cuboid

1. Select the cuboid you want to propagate.
2. Open the [batch mode](batch-mode-for-dynamic-objects.md) by clicking on the batch mode icon (<img src="../../.gitbook/assets/image (7) (2).png" alt="" data-size="line">) in the right toolbar.
3. Label the cuboid in the first frame(s) where the object is visible. Label the object in two consecutive frames to improve the smart propagation results.
4. Select the last labeled frame.
5. Press the "step forward" button (![](<../../.gitbook/assets/image (1) (1).png>)) to propagate the cuboid forward one frame, or press the "forward"  button (![](<../../.gitbook/assets/image (10).png>)) to propagate the cuboid forward until the end of the sequence.
6. If you see the propagation going wrong, you can press the stop button (![](<../../.gitbook/assets/image (7).png>)) to stop the propagation. You can then correct the label and continue the propagation again.

{% hint style="warning" %}
**Limitations**

* Objects need to contain enough points (\~ hundreds of points) to be propagated reliably.
* Objects that move erratically might not be tracked accurately. Specifically, their heading might move erratically as well.
* You cannot switch browser tabs while smart cuboid propagation is propagating the object
{% endhint %}
