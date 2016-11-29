_Autogenerated Tag Syntax Documentation:_

---
Repeat a filter multiple times and average.

```xml
<ReplicateFilter name="(&string;)" filter_name="(&string;)"
        replicates="(1 &non_negative_integer;)" upper_cut="(0 &real;)"
        lower_cut="(0 &real;)" median="(false &bool;)" threshold="(0 &real;)"
        confidence="(1.0 &real;)" />
```

-   **filter_name**: (REQUIRED) Name of the filter to be applied multiple times.
-   **replicates**: Number of replicates.
-   **upper_cut**: Trim of the highest value bye upper_cut.
-   **lower_cut**: Trim of the lowest value bye lower_cut.
-   **median**: If true, calculate the median instead of the average.
-   **threshold**: Filter returns true of calculated value is less than threshold.
-   **confidence**: Probability that the pose will be filtered out if it does not pass this Filter

---