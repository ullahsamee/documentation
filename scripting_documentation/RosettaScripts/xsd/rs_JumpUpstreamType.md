_Autogenerated Tag Syntax Documentation:_

---
The JumpUpstreamSelector sets the positions corresponding to all of the residues that are upstream of the indicated jump to true, and all the other positions to false. This selector is logically equivalent to a NotSelector applied to the JumpDownstreamSelector for the same jump.

```xml
<JumpUpstream name="(&string;)" jump="(&integer;)" />
```

-   **jump**: (REQUIRED) The integer given for the "jump" argument should refer to a Jump that is present in the Pose.

---