_Autogenerated Tag Syntax Documentation:_

---
A scoring grid that gives penalties for being too close to an atom; the too close distance is 2.25A

```xml
<RepGrid name="(&string;)" grid_name="(&string;)" bb="(&real;)" sc="(&real;)"
        ligand="(&real;)" weight="(&real;)" />
```

-   **grid_name**: The name used to insert the scoring grid into the GridManager
-   **bb**: The repulsive value assigned to the grid for backbone atoms; positive values are considered unfavorable. If provided, then both 'sc' and 'ligand' attributes need to be provided also
-   **sc**: The repulsive value assigned to the grid for sidechain atoms; positive values are considered unfavorable. If provided, then both 'bb' and 'ligand' attributes need to be provided also
-   **ligand**: The repulsive value assigned to the grid for ligand atoms; positive values are considered unfavorable. If provided, then both 'bb' and 'sc' attributes need to be provided also
-   **weight**: (REQUIRED) XRW TO DO

---