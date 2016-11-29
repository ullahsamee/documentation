_Autogenerated Tag Syntax Documentation:_

---
Change a single residue to a different type. For instance, mutate Arg31 to an Asp.

```xml
<MutateResidue name="(&string;)" target="(&string;)" new_res="(&string;)"
        mutate_self="(false &bool;)" perserve_atom_coords="(false &bool;)"
        update_polymer_bond_dependent="(&bool;)" preserve_atom_coords="(&bool;)" />
```

-   **target**: The location to mutate. This can be a PDB number (e.g. 31A), a Rosetta index (e.g. 177), or an index in a reference pose or snapshot stored at a point in a protocol before residue numbering changed in some way (e.g. refpose(snapshot1,23)). See the convention on residue indices in the RosettaScripts Conventions documentation for details
-   **new_res**: (REQUIRED) The name of the residue to introduce. This string should correspond to the ResidueType::name() function (eg ASP).
-   **mutate_self**: If true, will mutate the selected residue to itself, regardless of what new_res is set to (although new_res is still required). This is useful to "clean" residues when there are Rosetta residue incompatibilities (such as terminal residues) with movers and filters.
-   **perserve_atom_coords**: If true, then atoms in the new residue that have names matching atoms in the old residue will be placed at the coordinates of the atoms in the old residue, with other atoms rebuilt based on ideal coordinates. If false, then only the mainchain heavyatoms are placed based on the old atom's mainchain heavyatoms; the sidechain is built from ideal coordinates, and sidechain torsion values are then set to the sidechain torsion values from the old residue. False if unspecified.
-   **update_polymer_bond_dependent**: Update the coordinates of atoms that depend on polymer bonds
-   **preserve_atom_coords**: Preserve atomic coords as much as possible

---