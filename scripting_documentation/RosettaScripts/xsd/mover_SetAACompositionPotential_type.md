_Autogenerated Tag Syntax Documentation:_

---
Sets the target amino acid composition of a pose and adds the relevant term to the indicated score function

```xml
<SetAACompositionPotential name="(&string;)" file="(&string;)"
        weight="(1.0 &real;)" scorefxn="(&string;)" />
```

-   **file**: (REQUIRED) File specifying desired amino acid composition
-   **weight**: Weight for amino acid composition potential
-   **scorefxn**: (REQUIRED) Score function to add this potential to

---