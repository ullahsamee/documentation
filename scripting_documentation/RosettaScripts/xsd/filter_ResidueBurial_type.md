_Autogenerated Tag Syntax Documentation:_

---
How many residues are within an interaction distance of target_residue across the interface.

```xml
<ResidueBurial name="(&string;)" pdb_num="(XRW TO DO &string;)"
        distance="(8.0 &real;)" neighbors="(1 &non_negative_integer;)"
        residue_fraction_buried="(0.001 &real;)" task_operations="(&string;)"
        confidence="(1.0 &real;)" />
```

-   **pdb_num**: PDB identifier of residue of interest
-   **distance**: Distance cutoff
-   **neighbors**: When used with neighbors=1 this degenerates to just checking whether or not a residue is at the interface.
-   **residue_fraction_buried**: what fraction of the total residues defined as designable by the taskfactory should actually be buried in order to return false. The default (0.0001) effectively means that 1 suffices. Set to 1.0 if you want all residues to be buried.
-   **task_operations**: XRW TO DO
-   **confidence**: Probability that the pose will be filtered out if it does not pass this Filter

---