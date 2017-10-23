<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
Reads stored residue subset created by HBNet(StapleInterface) and sums all of the sc-sc and sc-bb hbonds in the network. Adds BuriedUnsatHbondFilter score for a penalty.

```xml
<HBNetScore name="(&string;)" threshold="(0.0 &real;)"
        hbond_threshold="(-0.25 &real;)" confidence="(1.0 &real;)" />
```

-   **threshold**: Score must be less than or equal to this value to pass
-   **hbond_threshold**: Disregard hbonds weaker than this
-   **confidence**: Probability that the pose will be filtered out if it does not pass this Filter

---