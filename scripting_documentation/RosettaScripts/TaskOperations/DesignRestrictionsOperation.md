Concise way to combine residue selectors and residue-level task operations. The Action subtags allow you to specify several modifications to a packer task simultaneously. Using the 'selector_logic' attribute, you can combine as many previously-defined ResidueSelectors as you would like using AND, OR, ! (not), and parentheses or you can choose a particular, previously defined ResidueSelector using the 'residue_selector' attribute. One of the two must be provided. Then you may specify the set of canonical amino acids you'd like to restrict the indicated set of residues using the 'aas' attribute and/or by listing a set of previously-declared ResidueLevelTaskOperations.

```xml
<DesignRestrictions name="(&string;)" >
    <Action residue_selector="(&string;)" selector_logic="(&string;)"
            aas="(&string;)" residue_level_operations="(&string;)" />
</DesignRestrictions>
```



Subtag **Action**:   

-   **residue_selector**: The name of the already defined ResidueSelector that will be used by this object
-   **selector_logic**: Logically combine already-delcared ResidueSelectors using boolean AND, OR, and ! (not) operators. As convnetional, ! (not) has the highest precedence, then AND, then OR. Parentheses may be used to group operations together.
-   **aas**: A list of the canonical L amino acids that are to be allowed for the selected residues. Either upper or lower case letters are accepted. Note that if an amino acid is allowed for a residue that is selected by one action, but disallowed for that residue selected by a second action, the amino acid will not be allowed.
-   **residue_level_operations**: A comma-separated list of residue-level-task operations that will be retrieved from the DataMap.