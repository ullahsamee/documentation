_Autogenerated Tag Syntax Documentation:_

---
This mover takes a template pdb and cuts the active pose accroding to start and end position relative to the template pose

```xml
<CutOutDomain name="(&string;)" start_res="(1 &non_negative_integer;)"
        end_res="(1 &non_negative_integer;)" source_pdb="(&string;)"
        suffix="(&string;)" delta_n_ter="(0 &non_negative_integer;)"
        delta_c_ter="(0 &non_negative_integer;)" />
```

-   **start_res**: begin residue on the template pdb
-   **end_res**: end residue on the template pdb
-   **source_pdb**: (REQUIRED) name of the pdb to be cut
-   **suffix**: suffix of the outputted structure
-   **delta_n_ter**: do not delete n N-terminal residues
-   **delta_c_ter**: do not delete n C-terminal residues

---