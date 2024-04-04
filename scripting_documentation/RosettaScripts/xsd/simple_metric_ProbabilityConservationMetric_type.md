<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
A PerResidueRealMetric for calculating the conservation of a position given some predicted probabilities (using the relative Shannon Entropy).

References and author information for the ProbabilityConservationMetric simple metric:

ProbabilityConservationMetric SimpleMetric's author(s):
Moritz Ertelt, University of Leipzig [moritz.ertelt@gmail.com]

```xml
<ProbabilityConservationMetric name="(&string;)" custom_type="(&string;)"
        metric="(&string;)" use_cached_data="(false &bool;)"
        cache_prefix="(&string;)" cache_suffix="(&string;)"
        fail_on_missing_cache="(true &bool;)" />
```

-   **custom_type**: Allows multiple configured SimpleMetrics of a single type to be called in a single RunSimpleMetrics and SimpleMetricFeatures. 
 The custom_type name will be added to the data tag in the scorefile or features database.
-   **metric**: (REQUIRED) A PerResidueProbabilitiesMetric to calculate the conservation of residues.
-   **use_cached_data**: Use any data stored in the datacache that matches the set metrics name (and any prefix/suffix.)  Data is stored during a SimpleMetric's apply function, which is called during RunSimpleMetrics
-   **cache_prefix**: Any prefix used during apply (RunSimpleMetrics), that we will match on if use_cache is true
-   **cache_suffix**: Any suffix used during apply (RunSimpleMetrics), that we will match on if use_cache is true
-   **fail_on_missing_cache**: If use_cached_data is True and cache is not found, should we fail?

---