# Second pass on a finished search

Use this when the consultant wants more or different candidates after reading a result. Everything goes through `talent_landscape_refine` on the finished search, which prepares a new plan version; the search itself runs only after confirmation, as in the first pass.

A second pass needs a change. Searching the same way again is refused, so when the consultant only says "again" or "more", ask what should be different and offer what the result's summary suggests under its next actions: a search route not yet run, the next widening step, more depth.

The parameter names and action values below are for your calls only. To the consultant, describe every option in their words (a wider frame, a search route not yet tried, more depth, more people like a named candidate, leaving someone out); never say or write a name such as `widen_next`, `add_lane` or `expand`.

## Collect the feedback

Turn what the consultant says into these parts, and ask only for what is unclear:

| Consultant says | Parameter | Effect |
| --- | --- | --- |
| "Anna Maier is exactly right", "more like the top two" | `benchmarks`: those candidates | A benchmark lane searches for structural twins. Benchmarks are not returned again. |
| "Not Peter Huber, notice period too long" | `rejected`: candidate with the reason | Excluded for good; the reason adjusts the frame. Always ask for the reason if none is given; it improves the next pass. |
| "The client already knows Lisa Berger" | `known`: those candidates | Moved to the known list and excluded. |
| "Look further", "widen it" | `actions`: `widen_next` | Applies the plan's next widening step as a lane. Refused when the plan has none left; then offer a new search idea or more depth. |
| "Also try family offices", any new idea | `actions`: `add_lane` with `lane_text` | Turns the idea into a lane. `lane_text` is required. |
| "Search the same lanes again, without the people we have" | `actions`: `expand` | Repeats the lanes and excludes everyone found so far. Only together with another change in the same request (a benchmark, a rejection, a known candidate, a widening step, a new search idea, more depth or a correction); alone it is refused. |
| "Check the candidates again" | `actions`: `verify` | Verifies all delivered candidates again. |
| "Go deeper", "make it thorough" | `upgrade`: `standard` or `premium` | Raises the depth; the lanes are proposed again. Only depths the consultant may start, and only upwards. |
| Changes to the frame ("Switzerland too", "no banks") | `edits` | Corrections in plain words, as for a plan. |

Candidates are passed by their id from the result. If a name the consultant gives matches no candidate or more than one, read the candidate pages again or ask which one is meant; never guess.

## Run the second pass

1. Call `talent_landscape_refine` with the search and the collected parts. It takes 1 to 5 minutes, longer when benchmarks or corrections rebuild the search; wait with `get_job_result` as for a plan.
2. Show the new plan version: what changed, what was not applied and why, and which lanes will run.
3. Wait for the consultant's explicit confirmation, then call `talent_landscape_run` with the plan, as in the first pass.
4. Present the new result as in the first pass, including the candidate table. Point out which candidates are new in this version.

Preparing a second pass is free; its run costs the credits of its depth. Name that price and the balance (`credits` in the new plan version) when asking for the confirmation.
