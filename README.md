# Node-Decision Annotation Interface — GPU trajectories

Fork of [handoff-annotation](https://github.com/Sophie508/handoff-annotation) pointed at a
different dataset: the 10-task GPU trajectory snapshot from `handoff_bench`'s
`tree_construction` branch, after conversion to the 7-type schema (RESEARCH_PROBLEM /
RESEARCH_QUESTION / HYPOTHESIS / PLAN / EXPERIMENT / EVIDENCE / INFERENCE) and same-parent
same-type sibling merging (2,617 raw nodes → 518). Same mechanics as the original: a
preference-parameter quiz, then independent CONTINUE / STOP / ESCALATE labeling of decision
points, with optional voice rationales. Fully static — answers and recordings stay in the
annotator's browser and leave only as a downloadable zip.

**Open points not yet settled (see data/index.json / data/subset.json for the exact wording):**
- No luna/sonnet machine labels exist for this dataset yet, so `luna_label`/`sonnet_label`
  will be blank in every export until that labeling pass is added.
- The merge rule collapses same-type siblings across all 7 types uniformly, including
  HYPOTHESIS nodes (which are themselves synthetic, deduped-by-text nodes from the earlier
  conversion step) — not confirmed with the collaborator who asked for the 7-type data.
- Item selection (8 nodes/tree cap) has no machine "flip" signal to prioritize by, so it uses
  a deterministic one-per-type-then-round-robin sample instead — documented in
  `data/subset.json`'s `selection` block.

Live: https://sophie508.github.io/handoff-annotation-gpu/
