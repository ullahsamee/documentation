<!-- THIS IS AN AUTOGENERATED FILE: Don't edit it directly, instead change the schema definition in the code itself. -->

_Autogenerated Tag Syntax Documentation:_

---
Computes the overall ResidueLipophilicity of the pose.

```xml
<ResidueLipophilicity name="(&string;)" threshold="(-10 &real;)"
        output_file="(TR &string;)" print_splines="(false &bool;)"
        confidence="(1.0 &real;)" />
```

-   **threshold**: if ResidueLipophilicity score is lower than threshold, than pass.
-   **output_file**: where to print the result to. default to TRACER. use auto for job_name_RS.txt
-   **print_splines**: whehter to print the splines, default=false
-   **confidence**: Probability that the pose will be filtered out if it does not pass this Filter

---