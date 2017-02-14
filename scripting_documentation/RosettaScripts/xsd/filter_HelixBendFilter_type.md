<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
This filter will check each helix turn in target HelixID helix for further-than-optimal Hbond pairs and curvature below (smaller angles) than cutoff.

```xml
<HelixBendFilter name="(&string;)" threshold="(155.0 &real;)"
        HelixID="(1 &positive_integer;)" blueprint="(&string;)"
        confidence="(1.0 &real;)" />
```

-   **threshold**: Minimum bending angle allowed.
-   **HelixID**: Helix number over which to calculate bend and Hbond pair distance according to blueprint numbers
-   **blueprint**: path to blueprint file from which to parse strands
-   **confidence**: Probability that the pose will be filtered out if it does not pass this Filter

---