# ARTEFACT NOTES — mapping the demo to the dissertation

This file documents how each element of the TRINE demo corresponds to the
dissertation, and which values are placeholders pending Chapter 6. It is
intended for inclusion in the thesis appendix alongside the artefact itself.

## Feature → dissertation mapping

| Demo feature | Dissertation source |
|---|---|
| Role taxonomy: Orchestration, Retrieval, Planning, Execution | §2.3.1 — Agent role taxonomy |
| Trait definitions shown in the legend chips (hover) | §2.3.2 — TRINE trait definitions |
| Trait profile bars on each agent card | §2.3.2 trait-distribution analysis (Table 1) |
| External rule layer (flags not self-reported by agents) | Thesis core claim: accountability enforced outside the decision-makers |
| Trait-specific flagging per role | §2.5 — governance calibrated to role trait profile, not system-wide blanket rules |
| Scenario 2 (proxy bias propagation, N → T → R) | §3.5 — Bias propagation: the same root cause producing distinct failures at each pipeline stage |
| Scenario 4 (silent mis-delegation) | §2.3.2 — Orchestration as highest-network-scope role; failure shapes the entire system |
| Scenario 5 (irreversible decline) | §2.3.2 — Execution irreversibility as primary determinant of harm magnitude; §3.6 meaningful human control at machine speed |

## Trait profiles used (1–5 scale)

| Role | T | R | I | N | E | Basis |
|---|---|---|---|---|---|---|
| Orchestration | 3 | 3 | 5 | 5 | 5 | "Shapes the behaviour of the entire system" (§2.3.2) |
| Retrieval | 2 | 2 | 1 | 5 | 4 | Low autonomy but head-of-pipeline propagation risk (§2.3.2) |
| Planning | 5 | 3 | 3 | 3 | 4 | Low traceability, "least visible point of governance failure" (§2.3.2). Note: bar shows *risk* on the trait, so Planning scores highest on T-risk |
| Execution | 3 | 5 | 4 | 5 | 5 | Irreversible, market-facing, highest consequential risk (§2.3.1) |

**Convention:** bars represent *governance risk carried on that trait* (5 =
highest risk), not the trait's presence. E.g. Planning's T=5 means highest
traceability *risk* (lowest interpretability); Execution's R=5 means highest
reversibility *risk* (least undoable).

## Placeholder values to replace from Chapter 6

These are illustrative assumptions, not derived from any stated threshold in
Chapter 2. Each should be replaced once Chapter 6's governance requirements
are finalised:

1. **Numeric trait scores (1–5)** in `TRINE_PROFILES` — currently inferred
   from the qualitative trait-distribution discussion in §2.3.2.
2. **Confidence thresholds** in `accountabilityCheck()`:
   - 75 — Execution's bar for instantiating an irreversible action, and
     Orchestration's bar for unconstrained delegation
   - 60 — Retrieval's data-sufficiency floor
   - 55 — the general low-confidence floor across roles
3. **Proxy-variable detection** — currently a keyword pattern
   (postcode / zip code / address). Chapter 6 may specify a fuller proxy
   variable list or a different detection principle.
4. **Demo run data** — the pre-recorded outputs are scripted representative
   runs authored to exercise each rule deterministically; they are not
   captured live-API outputs.

## Repository contents

- `index.html` — the complete artefact (single file, no dependencies)
- `README.md` — public-facing description
- `ARTEFACT_NOTES.md` — this file

An earlier draft (generic agent names, blanket rule set, optional live-API
mode) is preserved in a separate v1 repository, documenting the artefact's
development from generic accountability rules to the TRINE taxonomy.
