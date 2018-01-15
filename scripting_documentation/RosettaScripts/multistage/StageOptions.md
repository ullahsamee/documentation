#MultistageRosettaScripts Stage Options

[[_TOC_]]

##Overview

TODO

##XML Format

###Skeleton

```
<Stage
    num_runs_per_input_struct=“(uint)”
    total_num_results_to_keep=“(uint)”
    result_cutoff=“(uint)”
    max_num_results_per_instance=“(uint)”
    job_bundle_size=“(uint)”
    merge_results_after_this_stage=“(bool)”
>

    <Add mover=“” filter=“”/>
    <Add mover_name=“” filter_name=“”/>
    <Sort filter=“” negative_score_is_good=“true”/>

</Stage>

```

###num_runs_per_input_struct

This is MRS's equivalent to the `-nstruct` command line option.
For the first stage, the number provided here declares the number of times the stage will run for each `<Job/>` tag.
For example, if `num_runs_per_input_struct=40` and there are 5 `<Job/>` tags, then the stage will end up running a total of 200 times.

For each additional stage, the number provided here declares the number of times the stage will run for each result from the previous stage.
If `num_runs_per_input_struct=5` and `total_num_results_to_keep=10` for the previous stage, then the stage will end up running a total of 50 times.

###total_num_results_to_keep

This number defines the maximum number of job results from the current stage that will survive and go on to the next stage (or to be output, if this is the final stage).
Unlike `num_runs_per_input_struct`, this option is not affected by the number of `<Job/>` tags.
The combination of `num_runs_per_input_struct=40`, `total_num_results_to_keep=10`, and 5 `<Job/>` tags results in 200 jobs - of which only 10 results will survive until the next round.

###result_cutoff

This options allows a stage to stop submitting jobs once a certain number of results have come in.
For example, say you are docking two proteins and you have some idea about how you want these proteins to interact.
You can run your docking mover as normal (with or without constraints) and follow up the docking mover with one or more filters.
The job will not return a result unless it passes all of these filters (including the one in `<Sort/>`).
Now you can set `num_runs_per_input_struct` to a very large number and `result_cutoff` to 1000 and Rosetta will essentially keep sampling until it finds 1000 results that pass all of your filters.

###max_num_results_per_instance

Some movers can return multiple results ([[HBNet|HBNet]], for example).
This is challenging for use to handle in a well-organized manner.
The current format only allows for the final mover in a stage to return multiple results.
This number defines a cap for a single mover.
If this value is set to 10, for example, a single instance of HBNet would only be able to return up to 10 results.
So if you have `num_runs_per_input_struct=1000` and `max_num_results_per_instance=2`, you can get a maximum of 2000 results.

###job_bundle_size

This option is rarely useful.

There may be a situation where a single stage is incredibly fast, so fast that the job distribution overhead is no longer negligible (perhaps the whole stage is just a single filter).
This option allows you to group jobs of the same stage together so that they more-or-less share overhead.
If `num_runs_per_input_struct=1000` and `job_bundle_size=10`, then the job distributor sends out 100 jobs that each repeat the work 10 times.

This does not require compensation in the other options. `max_num_results_per_instance` is still applied to each individual job, not to each bundle.

###merge_results_after_this_stage

By default all of the results of a stage are thrown into the same pool, sorted, and the top few are chosen to survive.
This option allows you to create a separate pool for each `<Job/>` tag until a certain point.

Suppose you have 2 `<Job/>` tags and 3 stages: (1) Dock, (2) Design, (3) Minimize.
Perhaps you want a 50/50 split of results until the final stage.
If you set `merge_results_after_this_stage="true"/>` in the second stage tag, then you will have a 50/50 split of jobs until after the Design step.
All of the results of the Design step will go into the same pool and the jobs for stage 3 will not necessarily be a 50/50 split.

[[/merge_results_after_this_stage.png]]

###Add

`<Add/>` means the exact same thing here as it does in [[traditional|RosettaScripts]] rosetta scripts.
It takes up to 1 mover (can use either `mover_name` or `mover`) and up to 1 filter (`filter_name` or `filter`).
If both a mover and filter are given, then mover is applied before the filter is.

###Sort

`<Sort/>` is similar to `<Add/>` but only takes a filter (`filter_name` or `filter`).
The metric measured by this filter is used to sort the results of this stage and determines which are kept and which are discarded.
More negative numbers are assumed to be better for this metric, but this can be changed by setting `negative_score_is_good="false"`.

##See Also

* [Introductory RosettaScripting Tutorial](https://www.rosettacommons.org/demos/latest/tutorials/scripting_with_rosettascripts/scripting_with_rosettascripts)
* [Advanced RosettaScripting Tutorial](https://www.rosettacommons.org/demos/latest/tutorials/advanced_scripting_with_rosettascripts/advanced_scripting_with_rosettascripts)
* [[Scripting Documentation]]: The Scripting Documentation home page
* [[Getting Started]]: A page for people new to Rosetta
* [[Application Documentation]]: Links to documentation for a variety of Rosetta applications

<!-- SEO
scriptvars
-->