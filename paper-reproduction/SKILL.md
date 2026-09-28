---
name: paper-reproduction
description: Analyze and reproduce a newly supplied research paper from its document, citation, repository, data, or results. Use to map the paper, find and compare open-source implementations, recommend a reproduction route, guide experiments step by step, diagnose metric gaps, and maintain evidence-backed progress across sessions. Do not use for ordinary paper summaries with no reproduction intent.
---

# Paper Reproduction

Guide one paper at a time from source analysis to an auditable reproduction. Preserve the user's authority at route and configuration decision points.

## Start or resume the paper

When the user supplies a new paper, treat it as a new reproduction unless they explicitly link it to an existing one. Establish a workspace and maintain `reproduction-state.md` there using [references/session-checkpoint.md](references/session-checkpoint.md). If a state file already exists, read it before proposing or running more work.

Classify the intended outcome:

- **Verification:** inspect artifacts and reported evidence.
- **Execution:** run an existing implementation and compare metrics.
- **Reimplementation:** rebuild the paper's method from its specification.
- **Replication:** test the claim with a meaningful independent variation.

Do not assume that running author code is an independent replication.

## Phase 1: map the paper before experimenting

Read the paper and relevant supplement closely enough to produce a reproduction map:

- research question, claimed contribution, method flow, and key assumptions;
- datasets, exact splits, preprocessing, augmentation, and leakage risks;
- model components, losses, optimization, schedules, initialization, and seeds;
- baselines, ablations, evaluation protocol, metrics, and target table or figure;
- hardware, runtime, software versions, checkpoints, and compute implications;
- details that are missing, ambiguous, contradictory, or deferred to code.

Trace every important item to a page, section, table, equation, appendix, or source file when available. Mark it as **reported**, **observed**, **derived**, or **assumed**. Never fill a gap silently.

## Phase 2: find and audit open-source code

Search for the official author or lab repository first, following links from the paper or project page. Then search credible third-party implementations only when they help fill a gap or provide an independent comparison. Record repository URL, ownership, license, branch or commit, release/tag, activity, framework, supported data, checkpoints, and evidence that it implements this paper. Do not call a repository official without primary-source evidence.

Inspect the relevant code and configuration rather than relying only on the README. Compare paper and code in a configuration ledger with these columns:

| Item | Paper / supplement | Public code | Material difference | Proposed choice | Provenance / confidence |
|---|---|---|---|---|---|

Cover at least data and splits, preprocessing, architecture, losses, hyperparameters, training duration, seeds, checkpoint selection, inference, post-processing, and metrics. Explain whether each difference is likely a bug fix, an undocumented implementation detail, a later optimization, an environment adaptation, or an unresolved conflict. Label such explanations as hypotheses unless established by evidence.

## Route decision gate

Before implementation or a meaningful experiment, present the user with:

1. the paper map;
2. candidate repositories and an evidence-based trust assessment;
3. material paper-versus-code differences;
4. feasible routes, expected fidelity, compute cost, risks, and what each route can prove;
5. a recommendation tied to the user's goal.

For matching published numbers, usually recommend the official code at a pinned version as the first baseline, followed by a paper-faithful variant for material discrepancies. For independent reimplementation, use the paper and supplement as the specification and treat code as clarification evidence. If the sources conflict materially, recommend a choice but let the user select the route before proceeding. Do not hide the decision inside setup work.

## Phase 3: make a source-bound reproduction plan

After the route is chosen, provide an ordered plan with checkpoints. For each step state:

- the action and exact command or file change when applicable;
- whether it follows the paper, supplement, selected code, or an explicit user decision;
- the expected artifact or observable result;
- a validation check and stop condition;
- expected compute or time when material.

Create an isolated environment inside the reproduction workspace when practical and capture runtime, packages, framework, drivers, hardware, commit, data version, and seeds. Validate data provenance, licensing, shapes, mappings, splits, and preprocessing. Treat downloaded code and scripts as untrusted until inspected.

Proceed checkpoint by checkpoint. Start with the cheapest end-to-end diagnostic, then a small controlled run, then the full target. Do not silently change configuration to obtain a better match. Obtain approval before meaningful external cost or unusually long compute.

## Phase 4: evaluate every run

After every run, tie observed metrics to raw logs or artifacts and compare like with like: units, aggregation, evaluation mode, checkpoint selection, post-processing, sample count, and variance.

For every target metric report:

- paper value, observed value, absolute difference, and relative difference when meaningful;
- target tolerance and whether it was met;
- the exact configuration used and whether it matches the chosen source;
- known deviations and their expected direction or magnitude of impact;
- possible causes ranked by evidence, explicitly separating facts from hypotheses;
- the smallest next experiment that can distinguish the leading explanations.

Use **reproduced**, **approximately reproduced**, **not reproduced**, or **inconclusive**. Never present a planned, estimated, cached, or partial result as an executed result. Do not weaken evaluation, tune on the test set, or alter metric code merely to match the paper.

## Decision gate after each run

End every substantive response—and always every run report—with a concise checkpoint containing:

- completed work and current stage;
- new evidence and artifacts;
- current metric gap from the paper;
- configuration fidelity: exact matches, deviations, unknowns, and assumptions;
- problems and ranked possible causes;
- recommended next action and alternatives;
- the explicit decision needed from the user: keep the selected configuration, modify named settings, investigate a discrepancy, or continue to the next experiment.

Update `reproduction-state.md` with the same facts so a later session can resume without relying on chat memory. Do not ask the user to repeat settled facts. If no run occurred, state that the metric gap is not yet measured.

## Deliverables

Keep runnable artifacts in the paper workspace, not inside this Skill. Preserve exact commands, machine-readable configurations, logs, checkpoints, metric artifacts, the comparison ledger, and the state file. For substantial work, use [references/report-template.md](references/report-template.md) for the final report.
