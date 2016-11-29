_Autogenerated Tag Syntax Documentation:_

---
The GeneralizedKIC mover allows a user to define a chain of atoms whose conformation is to be sampled or altered subject to the constraint that it remain closed, or that it be closed if it starts out open.  The mover has myriad options for controlling sampling and selection of a solution, and can invoke other movers to apply to each closed solution that it finds.  It has been written to be fully general, and can operate on chains of atoms that pass through backbones, side-chains, ligands, etc.  No assumptions about alpha-amino acid backbones are hard-coded, so GeneralizedKIC should be fully compatible with any non-canonical entity.

```xml
<GeneralizedKIC name="(&string;)" low_memory_mode="(&bool;)"
        correct_polymer_dependent_atoms="(&bool;)"
        dont_fail_if_no_solution_found="(&bool;)"
        selector="(&genkic_selector_name;)" selector_scorefunction="(&string;)"
        selector_kbt="(&real;)" stop_if_no_solution="(0 &non_negative_integer;)"
        closure_attempts="(&non_negative_integer;)"
        stop_when_n_solutions_found="(&non_negative_integer;)"
        pre_selection_mover="(&string;)" contingent_filter="(&string;)" >
    <AddResidue res_index="(&non_negative_integer;)" />
    <AddTailResidue res_index="(&non_negative_integer;)" />
    <SetPivots res1="(&non_negative_integer;)" atom1="(&string;)"
            res2="(&non_negative_integer;)" atom2="(&string;)"
            res3="(&non_negative_integer;)" atom3="(&string;)" />
    <SampleCisPeptideBond cis_prob="(0.1 &real;)" >
        <AddResidue index="(&non_negative_integer;)" />
    </SampleCisPeptideBond>
    <CloseBond res1="(&non_negative_integer;)" atom1="(&string;)"
            res2="(&non_negative_integer;)" atom2="(&string;)" bondlength="(&real;)"
            angle1="(&real;)" angle2="(&real;)"
            randomize_flanking_torsions="(&bool;)"
            prioratom_res="(&non_negative_integer;)" prioratom="(&string;)"
            followingatom_res="(&non_negative_integer;)" followingatom="(&string;)"
            torsion="(&real;)" />
    <AddPerturber effect="(&genkic_perturber_name;)"
            bin_params_file="(ABBA &string;)"
            iterations="(1 &non_negative_integer;)"
            must_switch_bins="(false &bool;)" bin="(&string;)"
            custom_rama_table="(&string;)" >
        <AddResidue index="(&non_negative_integer;)" />
        <AddAtoms res1="(&non_negative_integer;)" atom1="(&string;)"
                res2="(&non_negative_integer;)" atom2="(&string;)"
                res3="(&non_negative_integer;)" atom3="(&string;)"
                res4="(&non_negative_integer;)" atom4="(&string;)" />
        <AddValue value="(&real;)" />
    </AddPerturber>
    <AddFilter type="(&genkic_filter_name;)" residue="(&non_negative_integer;)"
            bin_params_file="(ABBA &string;)" bin="(&string;)"
            rama_cutoff_energy="(0.3 &real;)" >
        <AddFilterParameterReal name="(&string;)" value="(&real;)" />
        <AddFilterParameterInteger name="(&string;)" value="(&non_negative_integer;)" />
        <AddFilterParameterBoolean name="(&string;)" value="(&bool;)" />
        <AddFilterParameterString name="(&string;)" value="(&string;)" />
    </AddFilter>
    <AddAtomPairDistanceFilter res1="(&non_negative_integer;)" atom1="(&string;)"
            res2="(&non_negative_integer;)" atom2="(&string;)" distance="(&real;)"
            greater_than="(&bool;)" />
</GeneralizedKIC>
```

-   **low_memory_mode**: The low_memory_mode option can be used to limit the amount of information about each solution found that is stored, in order to reduce memory consumption. In this mode, only loop degree-of-freedom values are stored prior to selection. The drawback, however, is it can be risk to use low-memory mode with a preselection mover. Any changes to the pose made by the preselection mover will not be stored, so the preselection mover will have to be re-applied to the selected pose after selection. This costs additional time. In addition, if the preselection mover has any stochastic component to its behaviour, then the second application may not produce identical results to the first. This means that what might have been the lowest-energy pose when the preselection mover was first applied could now be a relatively high-energy pose, for example. For this reason, be judicious in the use of low-memory mode. The preferred course is to stop GenKIC when N solutions have been found to limit memory usage.
-   **correct_polymer_dependent_atoms**: If set to true, atoms whose positions are dependent on polymer bonds, such as amino acid "H" and "O" atoms, will have their positions set to ideal coordinates after closure.  False by default.
-   **dont_fail_if_no_solution_found**: By default, the GeneralizedKIC mover returns failure status if it fails to find a closed solution that passes filters.  Certain usage cases require that it does not fail.  If this option is set to true, it prevents GeneralizedKIC from returning a failure status, even if it finds no solution (in which case the input pose, which may have an open chain of atoms, is returned as the output pose).  This is necessary, for example, when GeneralizedKIC is used in conjunction with a ContingentFilter.
-   **selector**: (REQUIRED) The GeneralizedKICselector to use to pick a solution.  Solutions may be picked randomly ("random_selector"), by energy ("lowest_energy_selector"), or by other criteria.  See the Rosetta help wiki for more information on GeneralizedKICselectors, and for the full range of options.
-   **selector_scorefunction**: XSD XRW TO DO
-   **selector_kbt**: If the GeneralizedKICselector is set to "boltzmann_energy_selector", this is the Boltzmann temperature used when selecting a solution randomly, weighted by the Boltzmann probability of that solution.
-   **stop_if_no_solution**: If this option is used and set to a positive integer N, GeneralizedKIC stops looking for closure solutions if no solution was found in the first N attempts.
-   **closure_attempts**: The maximum number of times to try to find a solution.  Set this to zero to keep trying indefinitely (in which case the "stop_when_n_solutions_found" option should be used to prevent the mover from iterating forever).
-   **stop_when_n_solutions_found**: If this option is used and set to a positive integer N, GeneralizedKIC will stop looking for closure solutions as soon as at least N solutions have been found that pass filters.  Note that a GeneralizedKICselector must be specified even if this option is set to 1, because a single attempt can yield up to 16 solutions.
-   **pre_selection_mover**: As an optional alternative to restricting oneself to backbone-only score terms, GeneralizedKIC permits the user to specify a pre-selection mover defined prior to the GeneralizedKIC block. This permits side-chain moves, such as repacking or side-chain minimization, prior to scoring with the full energy function. Note that this mover will be applied to all candidate solutions passing filters, which makes this option potentially very computationally expensive!
If a pre-selection mover is specified, the mover may alter geometry outside of the loop to be closed, or may alter the FoldTree, in which case these alterations will carry through to the final pose returned by GeneralizedKIC. TaskOperations and MoveMaps may be used appropriately in the definition of the mover in question to restrict its effects to the loop on which GeneralizedKIC is operating if the user does not wish to alter geometry outside of this loop. If one wishes to apply more than one pre-selection mover (for example, a PackRotamersMover followed by a sidechain-only MinMover, to repack and minimize side-chains), they may be combined in a ParsedProtocol mover.
As a final note, a mover may return failure status, or may encapsulate filters that return failure status, in which case the solution to which the mover has been applied will be discarded.
-   **contingent_filter**: A ContingentFilter can also be used to record whether the mover failed. The ContingentFilter is a specialized filter that has its value set by a mover. GeneralizedKIC can set the value of a ContingentFilter, specified using the contingent_filter flag, to true or false depending on whether the closure was successful or unsuccessful. Subsequent application of the filter, possibly at a later point, can then abort trajectories involving unsuccessful loop closure.  Note that this is a largely deprecated feature that has been retained since a few users have found it useful in some cases; for most usage cases, one can simply rely on the fact that the mover returns failure status if no closed solution is found.  It will likely be necessary to use the "dont_fail_if_no_solution_found" option if a ContingentFilter is used.


Subtag **AddResidue**:   "AddResidue" sub-tags are used to specify the residues that make up the chain of atoms to be closed, in order of connectivity.

-   **res_index**: (REQUIRED) The "res_index" option within an "AddResidue" sub-tag specifies the index, in Rosetta numbering, of the residue being added to the chain of residues to be closed.

Subtag **AddTailResidue**:   Loops to be closed might have other chains of residues attached to them.  By default, GeneralizedKIC fails to respect covalent bonds to any but the end residues in the chain to be closed, and can tear these bonds apart as residues move.  Users can optionally specify a list of "tail" residues that are covalently attached to, and move with, the chain of residues to be closed.  For example, one might have a series of glycans attached to a serine residue in a protein loop that's being closed with GenKIC.  If these residues are specified as tail residues, then they will remain attached to the serine residue even as the loop that contains the serine residue moves.

-   **res_index**: (REQUIRED) The "res_index" option within an "AddTailResidue" sub-tag specifies the index, in Rosetta numbering, of the residue being added to the chain of residues constituting a "tail" that is intended to move with the chain to be closed.

Subtag **SetPivots**:   Pivots are atoms in the chain of atoms to be closed that are flanked by bonds whose dihedral values will be solved for analytically by the closure algorithm in order to close the loop. Currently, due to hard-coded assumptions in the kinematic closure numerical library, the first pivot must be the second atom in the chain to be closed, and the last pivot must be the second-to-last atom in the chain to be closed.

-   **res1**: (REQUIRED) The first pivot residue (by Rosetta index). Currently, due to hard-coded assumptions in the kinematic closure numerical library, the first pivot must be the second atom in the chain to be closed.
-   **atom1**: (REQUIRED) The first pivot atom (by atom name). Currently, due to hard-coded assumptions in the kinematic closure numerical library, the first pivot must be the second atom in the chain to be closed.
-   **res2**: (REQUIRED) The middle pivot residue (by Rosetta index).
-   **atom2**: (REQUIRED) The middle pivot atom (by atom name).
-   **res3**: (REQUIRED) The last pivot residue (by Rosetta index). Currently, due to hard-coded assumptions in the kinematic closure numerical library, the last pivot must be the second-to-last atom in the chain to be closed.
-   **atom3**: (REQUIRED) The last pivot atom (by atom name). Currently, due to hard-coded assumptions in the kinematic closure numerical library, the last pivot must be the second-to-last atom in the chain to be closed.

Subtag **SampleCisPeptideBond**:   A "SampleCisPeptideBond" sub-tag is a shorthand for adding a sample_cis_peptide_bond GeneralizedKICperturber.  It tells the GeneralizedKIC mover to sample a cis-peptide bond at a particular residue some subset of the time.

-   **cis_prob**: The probability of sampling a cis-peptide bond at a given position, where 1.0 means that cis is sampled 100% of the time, and 0.0 means that trans is sampled 100% of the time.


Subtag **AddResidue**:   "AddResidue" sub-sub-tags are used within a "SampleCisPeptideBond" sub-tag to list all of the residues at which cis-peptide bonds should be sampled.

-   **index**: (REQUIRED) The index, in Rosetta numbering, of a residue whose omega value should sample 0.

Subtag **CloseBond**:   A "CloseBond" sub-tag is a shorthand for set_bondangle and set_bondlength GeneralizedKICperturbers, as well as an optional pair of randomize_dihedral perturbers for the flanking dihedral angles, and an optional set_torsion perturber.  It is intended to be used to set the ideal geometry for an open bond in a loop that GeneralizedKIC should close.

-   **res1**: (REQUIRED) The residue (Rosetta numbering) containing the first atom in the bond to be closed.
-   **atom1**: (REQUIRED) The first atom (given as an atom name string) in the bond to be closed.
-   **res2**: (REQUIRED) The residue (Rosetta numbering) containing the second atom in the bond to be closed.
-   **atom2**: (REQUIRED) The second atom (given as an atom name string) in the bond to be closed.
-   **bondlength**: (REQUIRED) The length of the bond to be closed.
-   **angle1**: (REQUIRED) The bond angle defined by B1, A1, A2, where A1 and A2 are the atoms in the bond to be closed and B1 is the last atom in the chain to be closed that's prior to the bond to be closed.
-   **angle2**: (REQUIRED) The bond angle defined by A1, A2, B2, where A1 and A2 are the atoms in the bond to be closed and B2 is the first atom in the chain to be closed that's past the bond to be closed.
-   **randomize_flanking_torsions**: If true, bonds flanking the bond to be closed will have their torsion values randomized.  If present, requires "prioratom_res" and "followingatom_res" attributes to be set.
-   **prioratom_res**: The atom preceding the bond to be closed.  This is only required if the "randomize_flanking_torsions" option is used.
-   **prioratom**: The atom preceding the bond to be closed.  This is only required if the "randomize_flanking_torsions" option is used.
-   **followingatom_res**: The atom following the bond to be closed.  This is only required if the "randomize_flanking_torsions" option is used.
-   **followingatom**: The atom following the bond to be closed.  This is only required if the "randomize_flanking_torsions" option is used.
-   **torsion**: An optional torsion value for the bond to be closed.  If not specified, the input value persists.

Subtag **AddPerturber**:   The "AddPerturber" sub-tag is used to add and configure GeneralizedKICperturbers.  GeneralizedKICperturbers alter the chain to be closed in some way prior to kinematic closure, allowing definition of a desired conformation or conformational sampling. They can only act on the chain to be closed, and have no effect on tail residues or on any other part of the input structure. Perturbers are applied in the order that they are defined. Different perturbers may alter the same degrees of freedom, sequentially.

-   **effect**: (REQUIRED) The name of the GeneralizedKICperturber (e.g. "perturb_dihedral", "set_bondangle", "randomize_alpha_backbone_by_rama", etc.).  See the Rosetta documentation wiki for a full list of available perturbers.
-   **bin_params_file**: The "randomize_backbone_by_bins" and "perturb_backbone_by_bins" perturbers require a bin definition file, set using this option.
-   **iterations**: The "perturb_backbone_by_bins" perturber requires that a number of iterations be set. If the number of iterations is set to 1, only one residue, randomly chosen from the list provided, will have its mainchain torsions perturbed. If it is set higher, the algorithm iteratively picks a residue at random and perturbs it.
-   **must_switch_bins**: This option is only used by the "perturb_backbone_by_bins" perturber.  If "must_switch_bins" is set to true, the chosen residue is forced into a different torsion bin; if false, it has some probability of remaining in the same torson bin, in which case its mainchain torsion values will be chosen randomly (in a biased manner, if possible) from within that bin.
-   **bin**: The "set_backbone_bin" perturber draws random mainchain torsion values from a mainchain torsion bin defined in a bin params file.  The "bin" option names the bin from which the torsion values will be drawn.  Required for this perturber only.
-   **custom_rama_table**: The "randomize_alpha_backbone_by_rama" perturber may optionally draw random phi and psi values from one of several custom Ramachandran tables that offer either flattened or more stringent distributions.  These are listed on the Rosetta help wiki.


Subtag **AddResidue**:   The "AddResidue" sub-sub-tag in an "AddPerturber" sub-tag permits a residue to be defined on which the perturber may act.  Use multiple "AddResidue" tags to define more than one residue.

-   **index**: (REQUIRED) The index, in Rosetta numbering, of a residue on which this perturber should act.

Subtag **AddAtoms**:   The "AddAtoms" sub-sub-tag in an "AddPerturber" sub-tag permits one or more atoms to be defined, on which the perturber may act.  A particular type of perturber may take a list of one, two, three, or four atoms, depending on what it acts on.

-   **res1**: (REQUIRED) The residue (specified using Rosetta numbering) containing the first atom.
-   **atom1**: (REQUIRED) The first atom, specified as an atom name string.
-   **res2**: The residue (specified using Rosetta numbering) containing the second atom.
-   **atom2**: The second atom, specified as an atom name string.
-   **res3**: The residue (specified using Rosetta numbering) containing the third atom.
-   **atom3**: The third atom, specified as an atom name string.
-   **res4**: The residue (specified using Rosetta numbering) containing the fourth atom.
-   **atom4**: The fourth atom, specified as an atom name string.

Subtag **AddValue**:   The "AddValue" sub-sub-tag in an "AddPerturber" sub-tag permits a value to be set for those perturbers that take a value.  (An example of this is the "set_dihedral" perturber, which takes a value for the dihedral angle to set.)  Use multiple "AddValue" tags to specify more than one value.

-   **value**: (REQUIRED) The value to pass to the perturber.

Subtag **AddFilter**:   An "AddFilter" sub-tag adds a GeneralizedKICfilter, which discards solutions that do not pass certain criteria.  Generally, GeneralizedKICfilters are written to be considerably faster than conventional Rosetta filters, since they usually do not act on full poses.  They are applied before pre-selection movers.

-   **type**: (REQUIRED) The name of the GeneralizedKICfilter to apply (e.g. "backbone_bin", "rama_prepro_check", "atom_pair_distance", etc.).  See the Rosetta help wiki for a full list of avaliable filters.
-   **residue**: A parameter required by several filters, including "backbone_bin", "alpha_aa_rama_check", and "rama_prepro_check": the index, in Rosetta numbering, of the residue that we're examining with this filter.
-   **bin_params_file**: A parameter specific for the "backbone_bin" filter: a filename for a file defining mainchain torsion bins.
-   **bin**: A parameter specific for the "backbone_bin" filter: the mainchain torsion bin in which an amino acid residue must lie.  If the residue is not in this bin, the solution is discarded.
-   **rama_cutoff_energy**: A parameter specific for the "alpha_aa_rama_check" and "rama_prepro_check" filters: the value for the rama or rama_prepro score terms above which solutions are discarded.


Subtag **AddFilterParameterReal**:   An "AddFilterParameterReal" sub-sub-tag in an "AddFilter" tag sets a real-valued setting for a filter.  For example, the "atom_pair_distance" filter takes a real-valued parameter, called "distance", for the cutoff separation between two atoms used to discard solutions.

-   **value**: (REQUIRED) The value of the real-valued parameter.

Subtag **AddFilterParameterInteger**:   An "AddFilterParameterInteger" sub-sub-tag in an "AddFilter" tag sets an integer setting for a filter.  For example, the "atom_pair_distance" filter takes two integer parameters, called "res1" and "res2", for the indices of the two residues containing the two atoms whose separation is to be measured.

-   **value**: (REQUIRED) The value of the integer parameter.

Subtag **AddFilterParameterBoolean**:   An "AddFilterParameterBoolean" sub-sub-tag in an "AddFilter" tag sets a Boolean setting for a filter.  For example, the "atom_pair_distance" filter has a Boolean parameter called "greater_than" which, when set to "true" selects for interatomic separation greater than a cutoff rather than less than the cutoff.

-   **value**: (REQUIRED) The value ("true" or "false") of the Boolean parameter.

Subtag **AddFilterParameterString**:   An "AddFilterParameterString" sub-sub-tag in an "AddFilter" tag sets a string setting for a filter.  For example, the "atom_pair_distance" filter takes two string parameters, called "atom1" and "atom2", for the names of the two atoms whose separation is to be measured.

-   **value**: (REQUIRED) The value of the string parameter.

Subtag **AddAtomPairDistanceFilter**:   The "AddAtomPairDistanceFilter" sub-tag is a shorthand for adding an "atom_pair_distance" GeneralizedKICFilter.  It discards solutions if pairs of atoms are separated by more than a cutoff distance.

-   **res1**: (REQUIRED) The residue (Rosetta index) containing the first atom in the pair whose separation we will be measuring.
-   **atom1**: (REQUIRED) The first atom in the pair whose separation we will be measuring, specified as an atom name string.
-   **res2**: (REQUIRED) The residue (Rosetta index) containing the second atom in the pair whose separation we will be measuring.
-   **atom2**: (REQUIRED) The second atom in the pair whose separation we will be measuring, specified as an atom name string.
-   **distance**: (REQUIRED) The cutoff inter-atomic distance for discarding solutions.
-   **greater_than**: If "greater_than" is set to true, the filter will discard any solution for which the atoms are not separated by AT LEAST the cutoff distance.  If it is false (the default), then any solution for which the atoms are separated by more than the cutoff distance is discarded.

---