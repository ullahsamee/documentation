<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
Calculates the McCoy, Chandana, Colman Electrostatic complementarity using APBS.

```xml
<ElectrostaticComplementarityMetric name="(&string;)" custom_type="(&string;)"
        ignore_radius="(20 &real;)" interface_trim_radius="(1.5 &real;)"
        partially_solvated="(1 &bool;)" jump="(1 &integer;)"
        report_all_ec="(0 &bool;)" residue_selector1="(&string;)"
        residue_selector2="(&string;)" />
```

-   **custom_type**: Allows multiple configured SimpleMetrics of a single type to be called in a single RunSimpleMetrics and SimpleMetricFeatures. 
 The custom_type name will be added to the data tag in the scorefile or features database.
-   **ignore_radius**: How far away from the interface should atoms be ignored. -1 to keep everything. (15 Shows variation of about 0.001. 10 ~ 0.01)
-   **interface_trim_radius**: Value for the SC filter. How far from the sasa surface should the molecular dots be trimmed? The original paper used 0 here.
-   **partially_solvated**: If false, then fully solvated. When partially solvated, the other side of the pose is present but has 0 charge. If fully solvated, the other side of the pose is not present and solvent fills its place.
-   **jump**: Which jump over which to calculate the interface.
-   **report_all_ec**: Do you want to see the sub correlations? (The normally reported values are the averages of interface 1 and 2)
-   **residue_selector1**: Explicitly set which residues are on each side of the interface using residue_selectors.
-   **residue_selector2**: Explicitly set which residues are on each side of the interface using residue_selectors.

---