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
- Stopped hypotheses and stopping-rule evidence
- Smallest decisive single-factor experiments
- Remaining compute, data, or information blockers
