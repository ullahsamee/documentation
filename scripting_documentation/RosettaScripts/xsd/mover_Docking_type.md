_Autogenerated Tag Syntax Documentation:_

---
XRW TO DO

```xml
<Docking name="(&string;)" score_low="(score_docking_low &string;)"
        score_high="(&string;)" fullatom="(0 &bool;)"
        conserve_foldtree="(0 &bool;)" local_refine="(0 &bool;)"
        view="(0 &bool;)" design="(0 &bool;)" symmetry="(0 &bool;)"
        ignore_default_docking_task="(0 &bool;)" task_operations="(&string;)"
        jumps="(1 &int_cslist;)" optimize_fold_tree="(1 &bool;)" />
```

-   **score_low**: Low-resolution scorefunction
-   **score_high**: High-resolution scorefunction
-   **fullatom**: Run the high-resolution phase of the protocol
-   **conserve_foldtree**: Keep the foldtree the same through the whole protocol
-   **local_refine**: Do local refinement
-   **view**: XRW TODO
-   **design**: XRW TODO
-   **symmetry**: Account for symmetry and associated information
-   **ignore_default_docking_task**: Ignore default docking task, instead using whatever is provided
-   **task_operations**: XRW TO DO
-   **jumps**: list of jumps for docking
-   **optimize_fold_tree**: Obtain an optimal foldtree given the desired docking jumps

---