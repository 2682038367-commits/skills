# Persistent reproduction state

Maintain one `reproduction-state.md` in the paper workspace. Keep it concise but sufficient to resume in a new conversation. Update facts in place instead of appending contradictory summaries.

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

## Current stage

- Phase and last completed checkpoint
- Work completed
- Next planned checkpoint
- Pending user decision

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
- Recommended next single-factor action and alternatives
- Decision requested from the user
