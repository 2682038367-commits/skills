# Final reproduction report

Use only relevant sections. Link every observed result to a complete run snapshot and raw artifact.

## Evidence labels

- **[Paper]:** paper or supplement fact with precise citation.
- **[Code]:** inspected code/configuration fact with commit and file reference.
- **[Observed]:** reproduction evidence linked to an artifact or Run ID.
- **[Hypothesis]:** inference with supporting/conflicting evidence and falsifying check.

## Scope and selected route

- Paper, version, and primary source
- Goal: verification, execution, reimplementation, or replication
- Selected repository/version or paper-faithful specification
- Why this route was chosen and what it can establish
- Claims, target metrics, and success tolerances

## Paper map

- Method and contribution
- Data and preprocessing
- Training and inference
- Evaluation and target tables/figures
- Missing, ambiguous, or conflicting details

## Main and core experiment priority

| Role | Experiment / paper location | Innovation claim tested | Target metric or pattern | Minimum viable version | Required artifacts | Cost | Final status |
|---|---|---|---|---|---|---|---|
| Main | | | | | | | |
| Core | | | | | | | |

- Relationship: same / prerequisite-dependent / validity-dependent / shared-base but outcome-independent / independent-parallel
- Operational dependency and prerequisites:
- Interpretive dependency:
- Whether the main result predicts the core result, with evidence:
- Initial time-limited recommendation:
- Post-main recommendation: full core / minimum viable core / repair main first / deferred
- User decision and resulting evidence gained or lost:

## Artifact manifest

| Artifact | Source or path | Version / commit / checksum | Evidence label and notes |
|---|---|---|---|
| Paper | | | [Paper] |
| Code | | | [Code] |
| Data | | | |
| Checkpoint | | | |

## Paper-to-code configuration ledger

| Item | [Paper] | [Code] | Actual [Observed] | Difference and impact | Confidence |
|---|---|---|---|---|---|
| | | | | | |

## Run snapshots

Every result-bearing run must link a manifest containing repository commit and dirty diff, configuration files and resolved overrides, exact command/arguments, data version and split, all seeds, environment versions, and output artifacts.

| Run ID | Snapshot manifest | Changed factor | Controlled factors | Auditable? |
|---|---|---|---|---|
| | | | | |

## Results

| Claim / metric | Current [Observed] | Paper [Paper] | Absolute / relative gap | Beyond multi-seed variation? | Could affect conclusion? | Status | Run ID / evidence |
|---|---:|---:|---|---|---|---|---|
| | | | | yes / no / unknown | yes / no / uncertain | | |

State how the multi-seed range was obtained. If the paper and local experiments provide no comparable range, mark it unknown.

## Conclusion reproduction status

Judge each material conclusion, not only the headline metric. Numerical, trend, and mechanism reproduction are separate dimensions and may coexist.

| Paper conclusion | Numerical reproduction | Trend reproduction | Mechanism reproduction | Not reproduced / inconclusive | Supporting Run IDs | Configuration fidelity and limitations |
|---|---|---|---|---|---|---|
| | yes / no / inconclusive | yes / no / inconclusive | yes / no / inconclusive | status and tested dimension | | |

- **Numerical reproduction:** target values fall within predeclared tolerance or comparable multi-seed variation.
- **Trend reproduction:** direction, ranking, scaling behavior, or ablation pattern matches across the necessary conditions.
- **Mechanism reproduction:** targeted intervention, ablation, or trace supports the proposed causal mechanism; similar outputs alone do not qualify.
- **Not reproduced:** sufficiently comparable evidence contradicts the tested claim.
- **Inconclusive:** evidence is missing, unauditable, underpowered, non-comparable, or non-discriminating.

Give an overall synthesis only after the per-claim table. Do not infer mechanism reproduction from numerical or trend reproduction.

## Controlled experiment and diagnosis ledger

| [Hypothesis] | One changed factor | Controlled factors | Evidence and outcomes | Falsifications | Decision / stop reason |
|---|---|---|---|---:|---|
| | | | | | |

Separate established [Paper], [Code], and [Observed] facts from [Hypothesis]. Document bundled changes as non-attributable. Record rejected or reopened directions and why.

## Interpretation

- Which claims were reproduced and at what level
- Configuration deviations and likely impact
- Whether gaps exceed meaningful random variation
- Whether any gap could alter the paper's conclusion
- Threats to validity and limits
- Whether this is author-code execution or stronger independent replication

## Decisions and next experiments

- User decisions made during the workflow
- Main/core experiment selection, dependency assessment, and post-main core-gate decision
- Stopped hypotheses and stopping-rule evidence
- Smallest decisive single-factor experiments
- Remaining compute, data, or information blockers
