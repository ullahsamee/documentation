_Autogenerated Tag Syntax Documentation:_

---
The ChainSelector sets the positions corresponding to all the residues in the given set of chains to true, and all the other positions to false.

```xml
<Chain name="(&string;)" chains="(&chain_cslist;)" />
```

-   **chains**: The string given for the "chains" option should be a comma-separated list of chain identifiers. Each chain identifier should be either an integer, so that the Pose chain index will be used, or a single character, so that the PDB chain ID can be used.

---