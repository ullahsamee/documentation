_Autogenerated Tag Syntax Documentation:_

---
Collects data on an antibody including CDRs, interfaces of L_H, L_A, H_A, and LH_A (this can be set), and other metrics.

```xml
<AntibodyFeatures name="(&string;)" pack_separated="(true &bool;)"
        pack_together="(false &bool;)" dSASA_cutoff="(100 &real;)"
        compute_packstat="(true &bool;)"
        skip_all_antigen_analysis="(false &bool;)" scorefxn="(&string;)"
        interface="(&ab_interface_string;)" interfaces="(&ab_interface_list;)"
        cdr_definition="(&string;)" input_ab_scheme="(&string;)"
        include_proto_cdr4="(&bool;)" />
```

-   **pack_separated**: repack chains after separation (better evaluation of unbound state).
-   **pack_together**: repack the input before calculating bound state values
-   **dSASA_cutoff**: XRW TO DO currently unused parameter
-   **compute_packstat**: Compute interface packstat
-   **skip_all_antigen_analysis**: Do not report antigen analysis.
-   **scorefxn**: Name of the scoring function
-   **interface**: Definition of the interface
-   **interfaces**: Define multiple interface sections
-   **cdr_definition**: XRW TO DO
-   **input_ab_scheme**: XRW TO DO
-   **include_proto_cdr4**: XRW TO DO

---