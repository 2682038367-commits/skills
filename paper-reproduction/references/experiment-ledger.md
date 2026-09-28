# Experiment ledger

Create `experiment-ledger.md` in the paper workspace before the first run. It is an append-oriented chronological history, not a replacement for run manifests or `reproduction-state.md`.

## Rules

- Add every attempted run, including failed, aborted, and unauditable runs.
- Order entries by ISO 8601 start time and use a stable Run ID.
- Link the exact run snapshot; never duplicate an incomplete approximation of its configuration.
- Name the baseline Run ID, the single changed factor, and controlled factors.
- Use [Paper], [Code], [Observed], and [Hypothesis] labels for material claims.
- Do not silently rewrite old conclusions. Add a dated correction that links the new evidence.

## Chronological index

| Time | Run ID | Baseline | Changed factor | Target hypothesis | Key result | Five-part comparison | Conclusion / decision | Snapshot |
|---|---|---|---|---|---|---|---|---|
| | | | | | | Current → Paper → Gap → Beyond seed range? → Conclusion impact? | | |

## Run entry

### `<run-id>` — `<ISO 8601 time>`

- Status: completed / failed / aborted / unauditable
- Baseline Run ID:
- Single changed factor:
- Controlled factors:
- Target [Hypothesis]:
- Snapshot manifest:
- Key [Observed] results and artifacts:
- Current → Paper → Gap → Beyond multi-seed variation? → Could affect conclusion?:
- Interpretation with evidence labels:
- Hypothesis outcome: supported / weakened / falsified / inconclusive
- Stopping-rule effect:
- Decision and next experiment:
- Correction history, if any:
