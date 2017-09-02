# HolesFilter
*Back to [[Filters|Filters-RosettaScripts]] page.*
## Holes

Uses Will Sheffler's packing code (holes) to evaluate voids/holes in packing

You can pass a residue selector to only compute the holes score for that given selection:
The holes calculation is performed on the Pose as whole (ignoring the ResidueSelector), but when the time comes to report the score, only the atoms in the residue selector are summed.  The Holes score is a sum of individual atoms/residues anyway (technically "PoseBalls"), so by only reporting a specific selection, we should be able to get location-specific data. 

```
<Holes name="(&string)" threshold=“(&real)" residue_selector="(&string)" normalize_per_atom="(&bool)" normalize_per_residue="(&bool)" exclude_bb_atoms="(&bool)"  />
```

**Example**

```
#compute holes are h-bond networks; correlates better than using the total holes score
<RESIDUE_SELECTORS>
  <ResiduePDBInfoHasLabel name="hbnet_residues" property="HBNet" />
  <Neighborhood name="around_hbnet" selector="hbnet_residues" distance="5.0" />
  <And name="core_around_hbnet" selectors="hbnet_core,around_hbnet"/>
</RESIDUE_SELECTORS>
<FILTERS>
  # holes score only around networks
  <Holes name="network_holes" threshold="1.8" residue_selector="core_around_hbnet" normalize_per_atom="true" exclude_bb_atoms="true" confidence="0"/>
  # holes score of the full pose
  <Holes name="full_holes" threshold="1.8" confidence="0"/>
</FILTERS>
<PROTOCOLS>
  <Add filter="network_holes" />
  <Add filter="full_holes" />
</PROTOCOLS>
```
## Options
-   threshold: return false if above this number
-   residue_selector: pass your residue selector of choice and holes will only calculate holes score for residues in residue_selector; holes calculation is performed on the Pose as whole (ignoring the ResidueSelector), but when the time comes to report the score, only the atoms in the residue selector are summed.  default=""
-   exclude_bb_atoms: don't include backbone (bb) atoms in residue selection case: default=false
-   normalize_per_residue: for residue selector case, normalize per residue; not recommended; default=false
-   normalize_per_atom: for residue selector case, normalize per atom; default is false but this option defaults to true if residue_selector is passed and if normalize_per_atom and normalize_per_residue are not explicitly defined by the user.

## See Also:

* [[Protein-protein docking|docking-protocol]]
* [[InterfaceHolesFilter]]
* [[ShapeComplementarityFilter]]
* [[SSShapeComplementarityFilter]]
* [[ResInInterfaceFilter]]
* [[SpecificResiduesNearInterfaceFilter]]
* [[ExposedHydrophobicsFilter]]