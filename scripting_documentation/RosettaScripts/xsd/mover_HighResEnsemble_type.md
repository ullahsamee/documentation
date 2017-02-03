<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
Independent high resolution optimization of each protein-ligand interface in ensemble.

```xml
<HighResEnsemble name="(&string;)" scorefxn="(&string;)" chains="(&string;)"
        movemap_builder="(&string;)" final_move="(&string;)"
        final_score="(&string;)" resfile="(&string;)"
        cycles="(&non_negative_integer;)" rosetta="(false &bool;)"
        repack_every_Nth="(&non_negative_integer;)" />
```

-   **scorefxn**: (REQUIRED) Score function to be used during docking
-   **chains**: (REQUIRED) Ligand chains, specified as the PDB chain IDs
-   **movemap_builder**: (REQUIRED) Name of a previously defined MoveMapBuilder for Docking phase.
-   **final_move**: (REQUIRED) Name of a previously defined MoveMapBuilder for Minimization phase.
-   **final_score**: (REQUIRED) Score function to be used during minimizing
-   **resfile**: Name (path to) the resfile.
-   **cycles**: Number of cycles to run.
-   **rosetta**: Use Rosetta scores as stand-in for experimental affinity (testing purposes)
-   **repack_every_Nth**: Perform side chain repacking every Nth cycle.

---