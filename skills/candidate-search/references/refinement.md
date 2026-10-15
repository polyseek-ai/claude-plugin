# Second pass on a finished search

Use this when the consultant wants more or different candidates after reading a result. Everything goes through `talent_landscape_refine` on the finished search, which prepares a new plan version; the search itself runs only after confirmation, as in the first pass.

## Collect the feedback

Turn what the consultant says into these parts, and ask only for what is unclear:

| Consultant says | Parameter | Effect |
| --- | --- | --- |
| "Anna Maier is exactly right", "more like the top two" | `benchmarks`: those candidates | A benchmark lane searches for structural twins. Benchmarks are not returned again. |
| "Not Peter Huber, notice period too long" | `rejected`: candidate with the reason | Excluded for good; the reason adjusts the frame. Always ask for the reason if none is given; it improves the next pass. |
| "The client already knows Lisa Berger" | `known`: those candidates | Moved to the known list and excluded. |
| "Look further", "widen it" | `actions`: `widen_next` | Applies the plan's next widening step as a lane. |
| "Search the same lanes again, without the people we have" | `actions`: `expand` | Repeats the lanes and excludes everyone found so far. |
| "Also try family offices", any new idea | `actions`: `add_lane` with `lane_text` | Turns the idea into a lane. |
| "Check the candidates again" | `actions`: `verify` | Verifies all delivered candidates again. |
| "Go deeper", "make it thorough" | `upgrade`: `standard` or `premium` | Raises the depth; the lanes are proposed again. Only depths the consultant may start. |
| Changes to the frame ("Switzerland too", "no banks") | `edits` | Corrections in plain words, as for a plan. |

## Run the second pass

1. Call `talent_landscape_refine` with the search and the collected parts. It takes 1 to 5 minutes; wait with `get_job_result` as for a plan.
2. Show the new plan version: what changed and which lanes will run.
3. Wait for the consultant's explicit confirmation, then call `talent_landscape_run` with the plan, as in the first pass.
4. Present the new result. Point out which candidates are new in this version.

Each second pass counts as a research job, and its run as a new search, against the allowance.
