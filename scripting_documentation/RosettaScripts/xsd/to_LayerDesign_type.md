<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
Note: The LayerDesign TaskOperation will likely be deprecated at some point in the future in favour of the LayerSelector ResidueSelector. It is strongly recommended that users start to switch over to the LayerSelector ResidueSelector, which permits greater flexibility in selecting residues. Design residues with selected amino acids depending on the enviroment--accessible surface area. The layer of each residue is assigned to one of the three basic layers--core, boundary or surface-- depending on the accessible surface area of mainchain + CB, or depending on the number of neighbours in a cone extending along the CA-CB vector --if the use_sidechain_neighbors option is used.

```xml
<LayerDesign name="(&string;)" use_original_non_designed_layer="(true &bool;)"
        layer="(core_boundary_surface_Nterm_Cterm &string;)"
        repack_non_design="(true &bool;)" ignore_pikaa_natro="(false &bool;)"
        use_sidechain_neighbors="(&bool;)" sc_neighbor_dist_midpoint="(&real;)"
        sc_neighbor_denominator="(&real;)"
        sc_neighbor_angle_shift_factor="(&real;)"
        sc_neighbor_angle_exponent="(&real;)"
        sc_neighbor_dist_exponent="(&real;)" pore_radius="(&real;)"
        core="(&real;)" surface="(&real;)" core_E="(&real;)" core_L="(&real;)"
        core_H="(&real;)" surface_E="(&real;)" surface_L="(&real;)"
        surface_H="(&real;)" make_rasmol_script="(&bool;)"
        blueprint="(&string;)" use_symmetry="(true &bool;)"
        verbose="(false &bool;)" restrict_restypes="(true &bool;)"
        make_pymol_script="(false &bool;)" >
    <core >
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
    </core>
    <boundary >
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
    </boundary>
    <surface >
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
    </surface>
    <Nterm >
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
    </Nterm>
    <Cterm >
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
    </Cterm>
    <CombinedTasks name="(&string;)" >
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <TaskOperation Tag ... />
    </CombinedTasks>
    <TaskLayer >
        <TaskOperation Tag ... />
        <all copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Helix copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixCapping copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <HelixStart copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Loop copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
        <Strand copy_layer="(&string;)" aa="(&string;)" ncaa="(&string;)"
                append="(&string;)" ncaa_append="(&string;)" exclude="(&string;)"
                ncaa_exclude="(&string;)"
                operation="(&layer_design_operation_behavior;)"
                specification="(&layer_design_specification_behavior;)" />
    </TaskLayer>
</LayerDesign>
```

-   **use_original_non_designed_layer**: Restrict to repacking the non design layers
-   **layer**: Layer to be designed, other ex. core_surface means only design core and surface layer, other refers to the additional layers defined with packertasks
-   **repack_non_design**: If true, side chains will be repacked, left untouched if otherwise.
-   **ignore_pikaa_natro**: If true, and if a resfile is read before applying this TaskOperation, ignore any residues that have been set in the resfile with the PIKAA, NATRO, or NATAA commands.
-   **use_sidechain_neighbors**: If true, assign a residue's layers based on counting the number CA atoms from other residues within a cone in front of the residue's ca-cb vector. Because this option is no longer SASA based, the layer assignments will always be identical regardless of the protein sequence; i.e. layers could be assigned based on a polyalanine backbone and it would make no difference. This option changes the defaults for core and surface to neighbors less than 2 --surface-- and neighbors greater than 5.2 --core. HOWEVER, these defaults will be overwritten if core and surface are manually specified in declaring the taskoperation! So make sure you do not specify new core and surface settings appropriate for SASA when you are actually counting neighboring residues.
-   **sc_neighbor_dist_midpoint**: These values fine-tune the behavior of the sidechain neighbors residue-counting logic. Typically, a user need not change these from default values. For details on these, see the LayerSelector ResidueSelector's documentation.
-   **sc_neighbor_denominator**: These values fine-tune the behavior of the sidechain neighbors residue-counting logic. Typically, a user need not change these from default values. For details on these, see the LayerSelector ResidueSelector's documentation.
-   **sc_neighbor_angle_shift_factor**: These values fine-tune the behavior of the sidechain neighbors residue-counting logic. Typically, a user need not change these from default values. For details on these, see the LayerSelector ResidueSelector's documentation.
-   **sc_neighbor_angle_exponent**: These values fine-tune the behavior of the sidechain neighbors residue-counting logic. Typically, a user need not change these from default values. For details on these, see the LayerSelector ResidueSelector's documentation.
-   **sc_neighbor_dist_exponent**: These values fine-tune the behavior of the sidechain neighbors residue-counting logic. Typically, a user need not change these from default values. For details on these, see the LayerSelector ResidueSelector's documentation.
-   **pore_radius**: pore radius for calculating accessible surface area
-   **core**: residues of which asa is less than core are defined as core
-   **surface**: residues of which asa is greater than surface are defined as surface
-   **core_E**: XRW TO DO
-   **core_L**: XRW TO DO
-   **core_H**: XRW TO DO
-   **surface_E**: XRW TO DO
-   **surface_L**: XRW TO DO
-   **surface_H**: XRW TO DO
-   **make_rasmol_script**: if true, write a rasmol script coloring the residues by the three basic layers, core, boundary and surface.
-   **blueprint**: XRW TO DO
-   **use_symmetry**: More recently, the use_symmetry option has been added to permit LayerDesign to be symmetry-aware. If use_symmetry is set to true --the default, layers are defined for symmetric poses using the full, symmetric pose.
-   **verbose**: print to tracer
-   **restrict_restypes**: XRW TO DO
-   **make_pymol_script**: if true, write a pymol script coloring the residues by the three basic layer and the aditional taskoperation defined layers..


Subtag **core**:   XRW TO DO



Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **boundary**:   XRW TO DO



Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **surface**:   XRW TO DO



Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Nterm**:   XRW TO DO



Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Cterm**:   XRW TO DO



Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **CombinedTasks**:   XRW TO DO



Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

"TaskOperation Tag": Any of the [[RosettaScripts TaskOperation|TaskOperations-RosettaScripts]] tags

Subtag **TaskLayer**:   XRW TO DO



"TaskOperation Tag": Any of the [[RosettaScripts TaskOperation|TaskOperations-RosettaScripts]] tags

Subtag **all**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Helix**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixCapping**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **HelixStart**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Loop**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

Subtag **Strand**:   XRW TO DO

-   **copy_layer**: XRW TO DO
-   **aa**: XRW TO DO
-   **ncaa**: XRW TO DO
-   **append**: XRW TO DO
-   **ncaa_append**: XRW TO DO
-   **exclude**: XRW TO DO
-   **ncaa_exclude**: XRW TO DO
-   **operation**: XRW TO DO
-   **specification**: XRW TO DO

---