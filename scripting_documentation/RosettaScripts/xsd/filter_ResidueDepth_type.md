_Autogenerated Tag Syntax Documentation:_

---
Filter for measuring minimum distance from any sidechain atom in a residue to the closest water molecule

```xml
<ResidueDepth name="(&string;)" mindist="(0.0 &real;)" maxdist="(99.0 &real;)"
        dcut1="(2.6 &real;)" dcut2="(4.2 &real;)" evalres="(&bool_cslist;)"
        confidence="(1.0 &real;)" />
```

-   **mindist**: Minimal distance between sidechain atom and water molecule
-   **maxdist**: maximum distance between sidechain and water molecule
-   **dcut1**: XSD XRW TO DO
-   **dcut2**: XRW TO DO
-   **evalres**: Residues to evalute
-   **confidence**: Probability that the pose will be filtered out if it does not pass this Filter

---