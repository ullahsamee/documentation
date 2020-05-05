<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
This is a mover that can create a pose from a sequence, or fasta. if you use a fasta that has multiple sequences in it, and use the 'use_all_in_fasta' tag (set to true) it will use all of the sequences in the fasta and separate them by '/'.  Also you can build the pose extended if you set the 'extended' tag.

```xml
<PoseFromSequenceMover name="(&string;)" fasta="(&string;)"
        sequence="(&string;)" use_all_in_fasta="(false &bool;)"
        extended="(false &bool;)" residue_type_set="(fa_standard &string;)" />
```

-   **fasta**: Fasta file name
-   **sequence**: sequence as a string
-   **use_all_in_fasta**: instead of using only first sequence in a fasta, use them all (and join them via '/')
-   **extended**: extend the pose
-   **residue_type_set**: Residue representation, centroid, fa_standard

---