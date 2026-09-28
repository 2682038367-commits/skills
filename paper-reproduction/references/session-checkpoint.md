# Persistent reproduction state

Maintain one `reproduction-state.md` in the paper workspace. Keep it concise but sufficient to resume in a new conversation. Update facts in place instead of appending contradictory summaries.

Use `experiment-ledger.md` for chronological run history; keep only the current summary and links here.

## Evidence labels

Use only these primary labels for material claims:

- **[Paper]:** paper or supplement fact with precise citation.
- **[Code]:** inspected code/configuration fact with commit and file reference.
- **[Observed]:** reproduction evidence linked to an artifact or Run ID.
- **[Hypothesis]:** inference with supporting/conflicting evidence and falsifying check.

## Identity and goal

- Paper title, version, and source
- Workspace
- Reproduction type and target claims
- User-selected route and decision rationale
- Pinned repository commit, data version, and target configuration

## Main/core experiment priority

### Core claim inventory

| Claim ID | [Paper] claim and citation | Primary / co-primary / secondary | Why central to the paper |
|---|---|---|---|
| | | | |

### Core experiment candidates

| Candidate | Claim ID | Experiment / paper location | Directness / falsifiability | Cost | Information gain | Dependencies | Minimum viable version | Priority / status |
|---|---|---|---|---|---|---|---|---|
| A | | | | | | | | selected / alternative / deferred |
| B | | | | | | | | selected / alternative / deferred |
| C | | | | | | | | selected / alternative / deferred |

- Main experiment and paper location:
- Selected default core candidate and claim:
- Selection rationale: claim centrality → directness/falsifiability → information gain → interpretability → feasibility/cost
- Ranking ambiguity or user-selected priority:
- Relationship to main: same / prerequisite-dependent / validity-dependent / shared-base but outcome-independent / independent-parallel
- Operational dependency:
- Interpretive dependency:
- Does the main result predict the selected core result? yes / no / partially / unknown, with [Paper], [Code], or [Hypothesis] evidence
- Time-limited recommendation:
- Post-main core gate: pending / full selected candidate / minimum viable version / repair main first / defer core
- Ranking changes after main and [Observed] reason:
- User decision and rationale:

## Current stage

- Phase and last completed checkpoint
- Work completed
- Next planned checkpoint
- Pending user decision
- Latest experiment-ledger entry and Run ID
- Main status, ranked core candidates, selected candidate, and next decision gate

## Configuration fidelity

| Item | Selected [Paper] or [Code] requirement | Actual | Status | Evidence label and source |
|---|---|---|---|---|
| | | | exact / deviated / unknown | |

## Run ledger

A result without a complete linked snapshot is `unauditable` and cannot support a reproduction conclusion.

| Run ID | Snapshot manifest | Single changed factor | Controlled factors | Key metrics | Five-part comparison | Status | Artifacts |
|---|---|---|---|---|---|---|---|
| | | | | | Current → Paper → Gap → Beyond seed range? → Conclusion impact? | | |

Each run manifest must bind commit and dirty diff, config files and resolved config, exact command/arguments, data version/split, seeds, environment versions, and output artifacts.

## Hypothesis ledger and stopping status

| [Hypothesis] | Supporting/conflicting evidence | Minimal tests and outcomes | Falsification count | Continue/stop/reopen | Reason and next check |
|---|---|---|---:|---|---|
| | | | | | |

Default: stop after two independent targeted falsifications; a third requires conflicting evidence, an unresolved confound, or explicit user authorization. Stop decimal chasing when the gap is inside comparable multi-seed variation and cannot affect the paper's conclusion.

## Session checkpoint

- Progress this session
- New [Paper], [Code], [Observed], and [Hypothesis] items
- For each metric: Current → Paper → Gap → Beyond multi-seed variation? → Could affect conclusion?
- Run ID and complete snapshot link, or `not run` / `unauditable`
- Exact matches, deviations, and unknowns
- Active hypotheses and stopping-rule status
- Conclusion reproduction status changed by this session, if any
- Recommended next single-factor action and alternatives
- Decision requested from the user
