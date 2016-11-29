_Autogenerated Tag Syntax Documentation:_

---
Places hotspot residues simultaneously on a scaffold, rather than iteratively as in PlaceStub. It is faster therefore allowing more backbone sampling, and should be useful in placing more than 2 hotspots.

```xml
<PlaceSimultaneously name="(&string;)" chain_to_design="(2 &positive_integer;)"
        max_cb_dist="(3.0 &real;)" cb_force="(0.5 &real;)"
        stubscorefxn="(backbone_stub_constraint &string;)"
        host_chain="(2 &positive_integer;)" optimize_fold_tree="(false &bool;)"
        minimize_rb="(true &bool;)" task_operations="(&string;)"
        coor_cst_cutoff="(100.0 &real;)" repack_non_ala="(true &bool;)"
        after_placement_filter="(true_filter &string;)" >
    <StubMinimize min_repeats_before_placement="(0 &non_negative_integer;)"
            min_repeats_after_placement="(1 &non_negative_integer;)"
            cb_force="(&real;)" >
        <Add mover_name="(&string;)" bb_cst_weight="(10.0 &real;)" cb_force="(&real;)" />
    </StubMinimize>
    <DesignMovers >
        <Add mover_name="(&string;)" use_constraints="(true &bool;)"
                coord_cst_std="(0.5 &real;)" cb_force="(&real;)" />
    </DesignMovers>
    <NotifyMovers >
        <Add mover_name="(&string;)" cb_force="(&real;)" />
    </NotifyMovers>
    <StubSets explosion="(0 &non_negative_integer;)"
            stub_energy_threshold="(1.0 &real;)" max_cb_dist="(3.0 &real;)"
            cb_force="(&real;)" >
        <Add stubfile="(&string;)" filter_name="(&string;)" cb_force="(&real;)" />
    </StubSets>
</PlaceSimultaneously>
```

-   **chain_to_design**: Chain where design ought to be performed, numbered sequentially from 1
-   **max_cb_dist**: Maximum distance from ideal placement that is nonetheless considered a hit
-   **cb_force**: Force to apply to CB atoms
-   **stubscorefxn**: Scoring function to apply to the stubs being placed
-   **host_chain**: Probably the chain where the stub goes
-   **optimize_fold_tree**: setup new fold_tree for better numerical behaviour between the residue at the center of target_residues and the nearest residue on the partner
-   **minimize_rb**: do we want to minimize the rb dof during stub placement? This will allow a previously placed stub to move a a little to accommodate the new stub. It's a good idea to use this with the previously placed stub adding its implied constraints.
-   **task_operations**: XRW TO DO
-   **coor_cst_cutoff**: the threshold coordinate constraint energy between the added hotspot residues and the one in the stub library. Use with stubscorefxn=backbone_stub_linear_constraint. PlaceSimultaneously fails if placed residues deviates beyond this threshold.
-   **repack_non_ala**: clearly implies something about repacking, although the only comment I could find mentioned reDESIGN instead
-   **after_placement_filter**: The name of a filter to be applied immediately after stub placement and StubMinimize movers, but before the DesignMovers run. Useful for quick sanity check on the goodness of the stub.


Subtag **StubMinimize**:   Defines Movers used to minimize w/r/t stub placement

-   **min_repeats_before_placement**: minimization trials before placement
-   **min_repeats_after_placement**: minimization trials before placement
-   **cb_force**: the force on CB atoms


Subtag **Add**:   

-   **mover_name**: (REQUIRED) Name of the Mover (defined elsewhere in the XML)
-   **bb_cst_weight**: determines the strength of the constraints derived from the stubs. This value is a weight on the cb_force, so larger values are stronger constraints.
-   **cb_force**: the force on CB atoms

Subtag **DesignMovers**:   Defines Movers used to do design after stub placement



Subtag **Add**:   

-   **mover_name**: (REQUIRED) Name of the Mover (defined elsewhere in the XML)
-   **use_constraints**: obey constraints
-   **coord_cst_std**: standard deviation (width) on coordinate constraint
-   **cb_force**: the force on CB atoms

Subtag **NotifyMovers**:   Defines Movers (named elsewhere in XML) that must be aware of the protected stub locations so they are not lost



Subtag **Add**:   

-   **mover_name**: (REQUIRED) Name of the Mover (defined elsewhere in the XML)
-   **cb_force**: the force on CB atoms

Subtag **StubSets**:   What are the Stubs we are placing?

-   **explosion**: which chis to explode, which probably means 'sample extensively'
-   **stub_energy_threshold**: after placement and minimization, what energy cutoff to use for each of the hotspots
-   **max_cb_dist**: Maximum distance from ideal placement that is nonetheless considered a hit
-   **cb_force**: the force on CB atoms


Subtag **Add**:   

-   **stubfile**: (REQUIRED) File that has a stub in it
-   **filter_name**: Stub placement tied to this Filter
-   **cb_force**: the force on CB atoms

---