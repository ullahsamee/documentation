# Hydrogen bond network score (hbnet score term)
Documentation created by Vikram K. Mulligan (vmullig@uw.edu), Baker laboratory, on 3 Nov 2017.
_Note:  This documentation is for the `hbnet` design-centric score term.  For information on the HBNet mover, an alternative method for creating hydrogen bond networks, see [[this page|HBNetMover]]._

[[_TOC_]]

## Purpose and algorithm

This scoring term is intended for use during design, to provide a bonus for hydrogen bond netwworks.  A network is defined as a set of two or more residues contiguously connected by sidechain-sidechain or sidechain-backbone hydrogen bonds.

While the pairwise hydrogen bonding terms can encourage residue-residue hydrogen bonding, they award the same score to, for example, three independent pairs of hydrogen bonded residues or a contiguous network of six highly-interconnected hydrogen bonded residues.  The detection of hydrogen bond networks is an inherently non-pairwise-decomposible problem.  The `hbnet` score term is therefore a non-pairwise whole-body energy term that produces a bonus that grows ever larger (_i.e._ more negative) in proportion to the square of the number of residues in the network.  If multiple networks are preset, the `hbnet` score is the sum of the scores for the individual networks.

Despite being non-pairwise-decomposible, the `hbnet` score term _is_ compatible with the packer.  It uses a fast node representation of the hydrogen bond network, rapidly updated on the fly, and an efficient connected components algorithm to compute hydrogen bond networks quickly during a packer trajectory.  The term's quadratic ramping guides the packer towards solutions with large hydrogen bond networks.  The term is currently discrete, however, meaning that it does _not_ provide derivatives that guide the minimizer towards better hydrogen bond networks.  For this, the conventional hydrogen bonding terms are relied upon.

## Relation to Scott Boyken's HBNet protocol

The `hbnet` score term is a different approach to the same problem solved by Scott Boyken's [[HBNet|HBNetMover]] protocol: that of placing residues to form hydrogen bond networks during design.  Where Dr. Boyken's approach uses a rapid exhaustive enumeration approach to find rotamer combinations that produce hydrogen bond networks, the use of this score term during conventional design converts the energy optimization problem typically solved by the packer into a constrained optimization problem.  In effect, the packer simultaneously tries to optimize the Rosetta energy and maximize the size of hydrogen bond networks.  This approach has both advantages and disadvatages compared to the HBNet protocol:

### Advantages of the `hbnet` score over the HBNet protocol

* **Simultaneous optimization.**  By simultaneously optimizing the conventional Rosetta energy and `hbnet` score, one can design for favourable hydrophobic packing _and_ favourable polar networks in a single step.  In contrast, the HBNet protocol places polar networks first, after which one uses conventional packing to try to place hydrophobic residues around the networks.  Where the most favourable networks might not subsequently be amenable to good packing, simultaneous optimization can sometimes find a better compromise.
* **Simpler setup and compatibility with all design workflows.**  To use the `hbnet` score, simply turn it on (change its weight to a nonzero value) in the scorefunction being used for design.  Complex design protocols, such as [[FastDesign|FastDesignMover]], can place hydrogen bond networks simply by having this score term on.
* **Tunable relative importances of networks vs. packing.**  By adjusting the weight given to the `hbnet` score term, the user can direct the packer to focus more or less on producing extensive hydrogen bond networks, or on optimizing the other things (Van der Waals interactions, hydrophobic interactions, _etc._) that the Rosetta scorefunction reflects.
* **Compatibility with other design-centric score terms.**  The `hbnet` score term can be used in conjunction with other score terms to guide the design process, such as the [[`aspartimide_penalty`|NC-scorefunction-info]] score term (penalizing aspartimide-forming amino acid sequences that can hinder chemical synthesis of peptides), the [[`aa_repeat`|Repeat-stretch-energy]] score term (penalizing repeat sequences that can impede NMR structure determination), or the [[`aa_composition`|AACompositionEnergy]] score term (penalizing deviations from a desired amino acid composition).  This means that one can, for example, solve a problem like this: "I want a well-packed core that's 75% hydrophobic, 25% polar, and contains exactly 2 charged residues and 1 tryptophan, with no repeat sequences or aspartimide-forming sequences, in which the polar residues form good hydrogen bond networks."
* **Speed.**  Using the `hbnet` score term adds no additional steps to the design process.  The term itself slows the packer down by about 10-20%, which is a relatively small impact.

### Disadvantages of the `hbnet` score as compared to the HBNet protocol

* **Stochasticity.**  Because the packer is stochastic (optimizing eneries by performing simulated annealing trajectories and returning the lowest-energy state encountered), there is no guarantee that the hydrogen bond network produced using the `hbnet` energy is the best possible.  The HBNet protocol, in contrast, does produce a ranked list of the very best hydrogen bond networks given the rotamers considered.
* **Imperfect definition of a hydrogen bond.**  In its current implementation, the `hbnet` score term uses a simplified hydrogen bond detection algorithm for speed, based only on donor-acceptor distances (with no angular consideration).  This yields occasional false positives, in which a donor-acceptor pair is in close proximity but oriented incorrectly to form a hydrogen bond, yet it is counted as a hydrogen bonded pair.  Plans are in place to address this in the future.
* **No consideration of buried unsatisfied donors or acceptors.**  In its present implementation, the `hbnet` score can yield hydrogen bond networks with buried unsatisfied hydrogen bond donors or acceptors, without penalty.  There are plans to implement another, similar score term to penalize buried unsatisfied donors and acceptors during design.
* **Single solution.** Unlike the HBNet protocol, which returns a ranked list of solutions, the use of the `hbnet` score term during design results in just one solution.  This can be an advantage or disadvantage, depending on the time that one wants to spend selectively optimizing hydrogen bond networks versus letting the software handle the global design problem.

## Usage

To use the `hbnet` score term in design, simply follow the following steps:

1.  Turn on (reweight to a nonzero value) the `hbnet` score term in the scorefunction used for design.  A value between 1.0 and 10.0 is recommended.  Higher values will promote more extensive networks at the expense of other score terms.  Activation of the `hbnet` score term can be done with a weights file, or in RosettaScripts as follows:

```xml
<SCOREFXNS>
	<ScoreFunction name="r15" weights="ref2015.wts" >
		<Reweight scoretype="hbnet" weight="1.0" />
	</ScoreFunction>
</SCOREFXNS>
```

2.  Design with any mover or protocol that invokes the packer, using the scorefunction defined above.  Ensure that the task operations passed to the packer allow polar residues at the relevant design positions (or it will not be possible to put in hydrogen bond networks).  [[FastDesign|FastDesignMover]] is particularly advantageous since the rounds of minimization with the softened force field can pull hydrogen bond donors and acceptors into better hydrogen bond-forming positions.

3.  (Recommended).  Perform a final round of minimization or relaxation with the `hbnet` score term turned _off_.  This ensures that the score term is not forcing unrealistic rotamers that would not be held in place given the hydrogen bonding.

## Use with symmetry
The `hbnet` score term is fully compatible with symmetry with no special setup required.

## Organization of the code

* The score term is defined in namespace `core::scoring::hbnet_energy`, and is located in `source/src/core/scoring/hbnet_energy/HBNetEnergy.cc/hh`.
* A unit tests for the asymmetric and symmetric cases are located in `source/test/core/scoring/hbnet_energy/HBNetEnergyTests.cxxtest.hh`.

##See Also

* [[Scoring explained]]
* [[Score functions and score types |score-types]]
* [[Adding a new energy method to Rosetta|new-energy-method]]
* [[AACompositionEnergy]]
* [[AddCompositionConstraintMover]]
* [[ClearCompositionConstraintsMover]]
* [[AddHelixSequenceConstraints mover|AddHelixSequenceConstraintsMover]]
* [[HBNet mover|HBNetMover]]