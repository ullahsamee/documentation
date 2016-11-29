_Autogenerated Tag Syntax Documentation:_

---
Close loops using loophash library

```xml
<LoopHashLoopClosureMover name="(&string;)" loop_insert="(&string;)"
        loop_insert_rclrc="(&string;)" blueprint="(&string;)"
        loophash_db_path="(&string;)"
        loophash_ex_limit="(4 &non_negative_integer;)"
        quick_and_dirty="(true &bool;)" symmetry_definition="(&string;)"
        repeat_structure="(&integer;)" lh_filter_string="(&string;)"
        max_linear_chainbreak="(0.07 &real;)"
        num_trajectory="(1 &non_negative_integer;)"
        save_top="(1 &non_negative_integer;)" />
```

-   **loop_insert**: Instruction string in Between Chains format: e.g. "A6B7CDE" to insert a loop of size 6 between chain A and B and another of 7 between B and C loop_insert, loop_insert_rclrc, and blueprint are mutually exclusive options
-   **loop_insert_rclrc**: Instruction string in Residue:Chain:Length format: e.g. 25:A:6,50:B:7 for a loop of size 6 residues after 25 (and before 26, implicit) and another of size 7 residues between 50 and 51. loop_insert, loop_insert_rclrc, and blueprint are mutually exclusive options
-   **blueprint**: loop_insert, loop_insert_rclrc, and blueprint are mutually exclusive options
-   **loophash_db_path**: (REQUIRED) path to the loophash library
-   **loophash_ex_limit**: loop extension limit
-   **quick_and_dirty**: remodel quick and dirty?
-   **symmetry_definition**: The structure is symmetric. Specify symmetry definition. symmetry_definition and repeat_strucutre are mutually exclusive
-   **repeat_structure**: Number of times the structure should be repeated. symmetry_definition and repeat_strucutre are mutually exclusive
-   **lh_filter_string**: XSD XRW: TO DO
-   **max_linear_chainbreak**: XSD XRW: TO DO
-   **num_trajectory**: number of trajectories
-   **save_top**: keep top n scores

---