---
name: paper-reproduction
description: Analyze and reproduce a newly supplied research paper from its document, citation, repository, data, or results. Use to map the paper, find and compare open-source implementations, recommend a reproduction route, guide controlled experiments step by step, diagnose metric gaps, and maintain auditable progress across sessions. Do not use for ordinary paper summaries with no reproduction intent.
---

# Paper Reproduction

Guide one paper at a time from source analysis to an auditable reproduction. Preserve the user's authority at route and configuration decision points.

## Start or resume the paper

When the user supplies a new paper, treat it as a new reproduction unless they explicitly link it to an existing one. Establish a workspace and maintain `reproduction-state.md` using [references/session-checkpoint.md](references/session-checkpoint.md) plus a chronological `experiment-ledger.md` using [references/experiment-ledger.md](references/experiment-ledger.md). If either file already exists, read it before proposing or running more work.

Classify the intended outcome:

- **Verification:** inspect artifacts and reported evidence.
- **Execution:** run an existing implementation and compare metrics.
- **Reimplementation:** rebuild the paper's method from its specification.
- **Replication:** test the claim with a meaningful independent variation.

Do not assume that running author code is an independent replication.

## Use four evidence labels

Label every material technical claim, discrepancy, and explanation with exactly one primary evidence class:

- **[Paper]:** stated by the paper or supplement; cite page, section, equation, table, or appendix.
- **[Code]:** established by inspected public code, configuration, commit, issue, or author documentation; cite repository version and file/line or artifact.
- **[Observed]:** directly measured or inspected in this reproduction; link the run, log, metric, trace, or other artifact.
- **[Hypothesis]:** an inference, causal explanation, unresolved assumption, or prediction not yet established; state supporting and conflicting evidence plus a falsifying check.

Do not merge conflicting facts. For example, if **[Paper]** says a parameter is learnable but **[Code]** shows its gradient path is detached, report both facts separately; any explanation of why is **[Hypothesis]** until tested. Calculations must identify their source facts and be labeled **[Observed]**.

## Phase 1: map the paper before experimenting

Read the paper and relevant supplement closely enough to produce a reproduction map:

- research question, claimed contribution, method flow, and key assumptions;
- datasets, exact splits, preprocessing, augmentation, and leakage risks;
- model components, losses, optimization, schedules, initialization, and seeds;
- baselines, ablations, evaluation protocol, metrics, and target table or figure;
- hardware, runtime, software versions, checkpoints, and compute implications;
- details that are missing, ambiguous, contradictory, or deferred to code.

Trace every important item to its source using the four evidence labels. Never fill a gap silently.

### Identify the main and core experiments from claims

When the paper contains many experiments, establish the claim hierarchy before choosing experiments. Extract explicit innovation claims from the title, abstract, introduction/contribution list, method framing, and conclusion. Cite each as **[Paper]** and classify it as **primary**, **co-primary**, or **secondary** based on how centrally the paper frames its novelty and promised capability. Do not infer the core claim from the largest numerical gain, most visually striking result, or largest result table.

- **Main experiment:** the headline or standard benchmark experiment used to establish the overall result against the principal baselines.
- **Core experiment candidate:** an experiment that directly and discriminatingly tests a primary or co-primary innovation claim. Prefer designs whose outcome could falsify that claim, such as a controlled comparison, targeted ablation, stress test, mechanism intervention, or evaluation under the specifically claimed condition.

Allow multiple candidates when the paper makes multiple distinct core claims. Produce candidates A, B, C, and more only when justified:

| Candidate | Core [Paper] claim tested | Experiment and paper location | Why it directly tests the claim | Cost | Information gain | Dependencies | Minimum viable version | Priority |
|---|---|---|---|---|---|---|---|---|

Rank candidates by: claim centrality first; then directness and falsifiability, expected information gain, interpretability, and feasibility/cost. Magnitude of reported improvement or visual salience is not a selection criterion by itself. Respect a user-specified claim priority. If multiple co-primary claims make the ranking genuinely ambiguous, explain the tradeoff and ask the user to choose rather than inventing certainty.

By default select only one highest-priority candidate for execution while preserving the remaining candidates as documented alternatives. In a time-limited plan, recommend completing the main experiment and this selected core experiment whenever feasible. If the full selected candidate is too expensive, propose a minimum viable version and state what it can and cannot establish.

The main and selected core experiment may be the same; state that explicitly. For the selected candidate—and for alternatives when their dependencies differ—classify the relationship as **same experiment**, **prerequisite-dependent**, **validity-dependent**, **shared-base but outcome-independent**, or **independent/parallel**. Separately answer:

1. Does the candidate require the main checkpoint, outputs, or validated pipeline to run?
2. Does the main result determine how its result should be interpreted?
3. Does a strong or weak main result logically predict its result, or is that relationship only **[Hypothesis]**?

Do not confuse operational dependence with evidential dependence. A core candidate may require a checkpoint produced by the main run while testing a claim not determined by the main score.

## Phase 2: find and audit open-source code

Search for the official author or lab repository first, following links from the paper or project page. Then search credible third-party implementations only when they help fill a gap or provide an independent comparison. Record repository URL, ownership, license, branch or commit, release/tag, activity, framework, supported data, checkpoints, and evidence that it implements this paper. Do not call a repository official without primary-source evidence.

Inspect relevant source and configuration rather than relying only on the README. Compare paper and code in a configuration ledger:

| Item | [Paper] | [Code] | Material difference | Proposed choice | Evidence / confidence |
|---|---|---|---|---|---|

Cover at least data and splits, preprocessing, architecture, losses, gradient paths, hyperparameters, training duration, seeds, checkpoint selection, inference, post-processing, and metrics. Explanations such as bug fix, undocumented detail, later optimization, or environment adaptation remain **[Hypothesis]** unless established.

## Route decision gate

Before implementation or a meaningful experiment, present:

1. the paper map;
2. candidate repositories and evidence-based trust assessment;
3. material paper-versus-code differences;
4. feasible routes, expected fidelity, compute cost, risks, and what each can prove;
5. a recommendation tied to the user goal;
6. the main experiment, core-claim inventory, ranked core candidates A/B/C, selected default candidate, dependency class, and time-limited priority plan.

For matching published numbers, usually recommend official code at a pinned version as the first baseline, followed by a paper-faithful variant for material discrepancies. For independent reimplementation, use the paper and supplement as the specification and code as clarification evidence. If sources conflict materially, recommend a choice but let the user select the route before proceeding.

## Phase 3: plan controlled experiments

After route selection, provide an ordered plan with checkpoints. For each step state the exact action, source being followed, expected artifact, validation and stop condition, and material compute cost.

The ordered plan must mark every experiment as **main**, **core:<candidate-id>**, or **supporting** and show prerequisites. Mark unselected core candidates as deferred alternatives rather than discarding them. Unless evidence indicates another order, establish the main baseline first and reserve time for the selected highest-priority core candidate.

Create an isolated environment when practical. Validate data provenance, licensing, shapes, mappings, splits, and preprocessing. Treat downloaded code and scripts as untrusted until inspected. Start with the cheapest end-to-end diagnostic, then a small controlled run, then the full target.

### Change one critical factor at a time

Unless the user explicitly authorizes a bundled change, each causal experiment must alter only one critical factor from its named baseline. Hold the dataset/split, seed set, training budget, evaluation, and all other relevant configuration constant. State the changed factor and controlled factors before running.

Compatibility changes required merely to make the system runnable must be separated from causal experiments. If several compatibility changes cannot be separated, request approval, label the run non-attributable, and do not use it to claim which change caused an improvement. Never silently change configuration to obtain a better match.

### Bind every result to a run snapshot

Assign every run a stable Run ID. Before accepting its metrics as reproduction evidence, create an immutable or content-addressed snapshot such as `runs/<run-id>/run-manifest.yaml` that records:

- source repository URL, branch/tag, commit hash, and dirty-tree status plus patch or diff hash;
- copies or checksums of every configuration file and the fully resolved configuration after overrides;
- exact command and command-line arguments;
- dataset release/version, split, preprocessing identity, and checksums where practical;
- every random seed and determinism setting;
- OS, hardware, driver, runtime, framework, package versions, and environment lock/export;
- start/end time, logs, metrics, checkpoints, and output artifact paths.

Link the Run ID and manifest from every reported result. If the snapshot is incomplete, mark the run **unauditable** and do not use it to decide whether the paper was reproduced; either reconstruct the missing evidence reliably or rerun.

### Maintain the experiment ledger

Create `experiment-ledger.md` before the first run and update it immediately after every attempted run, including failed, aborted, and unauditable runs. Keep entries chronological and link each Run ID to its snapshot. Record its baseline, single changed factor, controlled factors, target hypothesis, key result, five-part paper comparison, conclusion, stopping-rule effect, and resulting decision. Do not silently rewrite history; correct an old entry with a dated correction note. The ledger is the experiment narrative, while `reproduction-state.md` is the compact current state.

## Phase 4: evaluate every run

Tie metrics to the run snapshot and compare like with like: units, aggregation, evaluation mode, checkpoint selection, post-processing, sample count, and variance.

For every target metric, force this decision line:

> **Current result → Paper result → Gap → Beyond multi-seed variation? → Could it change the paper's conclusion?**

Also report absolute and relative gaps when meaningful. For the variation judgment, prefer the paper's reported standard deviation, confidence interval, or per-seed results; otherwise use a comparable local multi-seed estimate. If neither exists, say **unknown** rather than inventing a range. Give the conclusion-impact judgment as **yes**, **no**, or **uncertain**, with evidence.

Report exact configuration fidelity, known deviations, and their likely impact. Rank possible causes using the four labels and propose the smallest single-factor experiment that distinguishes the leading hypotheses. Use **reproduced**, **approximately reproduced**, **not reproduced**, **inconclusive**, or **unauditable**. Never present a planned, estimated, cached, or partial result as executed evidence. Do not weaken evaluation, tune on the test set, or alter metric code merely to match the paper.

## Core-experiment decision gate after the main run

After the main experiment finishes, do not automatically start or discard a core experiment. Re-evaluate the ranked core candidates using the new **[Observed]** evidence, preserve any ranking change with its reason, and present the user with a recommendation based on:

- whether the main run is auditable and faithful enough for the core result to be interpretable;
- the main metric gap, multi-seed context, conclusion impact, and unresolved setup failures;
- the declared dependency class and whether required checkpoints or artifacts are valid;
- whether the core experiment can diagnose the main gap or test the innovation despite a weak main score;
- remaining time/compute and the information gain of the full or minimum viable core experiment.

Recommend exactly one next state for one named candidate: **run the full selected core candidate**, **run its minimum viable version**, **repair/rerun the main experiment first**, or **defer/skip core execution**. Explain what evidence would be gained or lost. A poor main score is not by itself sufficient reason to skip an outcome-independent or diagnostically useful core experiment; an invalid prerequisite is a reason to repair the main path first. Let the user decide before incurring meaningful core-experiment cost, and record the decision in both state and ledger.

## Experiment stopping rules

Define stop criteria before each diagnostic series and enforce them:

- If two independent, well-targeted minimal experiments falsify a hypothesis, stop pursuing it. Use a third only when results conflict, a documented confound remains, or the user explicitly authorizes it. New evidence is required before reopening a rejected direction.
- Do not launch parameter sweeps for a falsified hypothesis or after the predeclared budget/attempt limit is reached.
- If the gap is within a comparable multi-seed variation or agreed tolerance **and** cannot reasonably change the paper's conclusion, stop tuning to chase reported decimal places.
- Continue investigation when the gap exceeds variation, the conclusion could change, a material configuration mismatch remains, or uncertainty is caused by insufficient comparable seeds.
- Stop or redesign any experiment that cannot discriminate between the competing hypotheses it is meant to test.

Record why a direction was continued, stopped, rejected, or reopened.

## Classify conclusion reproduction status

In the final report, classify every material paper conclusion using evidence from auditable runs:

- **Numerical reproduction:** the target quantitative value is within the predeclared tolerance or comparable multi-seed variation under a sufficiently faithful configuration.
- **Trend reproduction:** the claimed direction, ranking, scaling behavior, or ablation pattern is reproduced, even if exact values are not. State which conditions establish the trend.
- **Mechanism reproduction:** a targeted intervention, ablation, trace, or other discriminating test supports the claimed mechanism. Similar output alone is insufficient.
- **Not reproduced:** sufficiently comparable and powered evidence contradicts the tested numerical, trend, or mechanism claim.
- **Inconclusive:** evidence is missing, unauditable, underpowered, non-comparable, or unable to discriminate the claim. Do not collapse this into not reproduced.

Numerical, trend, and mechanism reproduction are distinct dimensions, not a guaranteed hierarchy. A conclusion may satisfy more than one. Report status per claim, the Run IDs supporting it, configuration fidelity, contrary evidence, and limitations before giving an overall synthesis.

## Decision gate after each run

End every substantive response—and always every run report—with a concise checkpoint containing:

- completed work and current stage;
- new evidence and artifacts, using the four labels;
- the required five-part result line for each target metric;
- configuration fidelity and the linked Run ID/configuration snapshot;
- problems and ranked hypotheses;
- stopping-rule status for each active hypothesis;
- main experiment status, core-claim inventory, ranked candidate list, selected candidate and dependency, and whether the post-main core gate is pending or resolved;
- recommended next single-factor action and alternatives;
- the explicit decision needed from the user: keep configuration, modify one named factor, authorize a bundled non-attributable change, investigate a discrepancy, stop a direction, or continue.

Update `reproduction-state.md` with current facts and append the run to `experiment-ledger.md` so a later session can reconstruct both state and history without chat memory. Do not ask the user to repeat settled facts. If no run occurred, state that the metric gap is not yet measured.

## Deliverables

Keep runnable artifacts in the paper workspace, not inside this Skill. Preserve exact commands, run snapshots, machine-readable configurations, logs, checkpoints, metric artifacts, the paper-to-code comparison ledger, `experiment-ledger.md`, and `reproduction-state.md`. For substantial work, use [references/report-template.md](references/report-template.md) for the final report.
