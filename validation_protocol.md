# Protocol for validating the spreading-repair proxy (R14) and the AI markers

**Status.** Not yet carried out. Register this protocol before any label is assigned.

## Samples
- **(a) Precision of R14.** R14-positive events per group (marked, control), drawn within repository strata in proportion to each repository's share of events (`sample_events.py`). Pilot: 400 per group (95% half-width about 7 points). Ruling out the precision gap that would erase the effect (2.8 points at precision 0.5) needs about 2,530 per group; 400 per group has only 12% power against it.
- **(b) Recall.** 400 marked and 400 control commits drawn irrespective of outcome, followed for 14 days by the annotators.
- **(c) Marker precision.** At least 400 AI-marked commits, stratified by tool family with at least 20 per family (`marker_audit.py`).
- **Optional.** Pre-period placebo events, labelled the same way (`sample_events.py --include-pre`), to test for labelling conventions that change with AI use.

## Annotation
Two annotators label each case independently and blind to marker status:
- **A** repair of a defect introduced by the original commit, in files outside it;
- **B** repair of a defect with another cause;
- **C** planned continuation;
- **D** refactoring, maintenance, documentation or tooling;
- **E** cannot be determined.

A third annotator resolves disagreements. Report Cohen's kappa with a bootstrap interval and raw agreement. For markers, label Y (AI-assisted), N (not) or U (cannot tell).

## Outputs (`analyse_labels.py`, `marker_audit.py analyse`)
- Precision (share labelled A) by group with Wilson intervals, and their difference with a Newcombe interval.
- Whether that interval excludes the nullifying precision gap.
- The effect recomputed with class A as the outcome, with a bootstrap interval combining label and repository sampling.
- Marker precision overall and by tool family.

## Decision rule
Downgrade the conclusions if the precision interval does not exclude the nullifying gap, or if the interval for the class-A effect includes zero. Report both outcomes whichever way they fall.
