# TRINE — A Trait-Based Multi-Agent Accountability Ledger

TRINE is an interactive demo built to accompany my MSc dissertation on
trait-based governance of multi-agent AI systems in financial services
(University of Edinburgh, Data and AI Ethics).

**TRINE** stands for the five ethically relevant traits at the centre of the
dissertation — **T**raceability, **R**eversibility, **I**ndependence,
**N**etwork scope, and **E**xposure. The thesis argues that the unit of
governance for multi-agent systems should shift from the *system* to the
*agent role*, because different roles carry structurally different trait
profiles and therefore structurally different risk. A planning agent's low
traceability makes it a sleeper risk; a retrieval agent's low autonomy hides
its high propagation risk; an execution agent's irreversibility places it at
the point of highest consequence.

This demo visualises that argument in miniature.

**Live demo:** https://francesssss.github.io/T.R.I.N.E/

## What it shows

A four-agent loan-underwriting pipeline mapped to the dissertation's role
taxonomy — **Orchestration → Retrieval → Planning → Execution** — where each
agent carries a visible T/R/I/N/E trait profile, and a rule layer *external to
the agents* audits every output and stamps it **verified** or **flagged** in a
live ledger.

Critically, the flagging logic is **trait-specific per role**, not one blanket
rule set:

| Role | Dominant trait audited | Example failure caught |
|---|---|---|
| Orchestration | **I** — Independence | High-autonomy delegation with no compliance constraint set downstream |
| Retrieval | **N** — Network scope | Proxy-correlated data entering the pipeline and propagating to every downstream agent |
| Planning | **T** — Traceability | A proxy factor formalised into scoring logic without transparent justification |
| Execution | **R** — Reversibility | An irreversible decision instantiated below the confidence bar the role demands |

## The five scenarios

1. **Standard applicant** — clean baseline; all four agents verify.
2. **Proxy bias propagation** — a postcode-linked risk factor is flagged at
   three different traits (N → T → R) as it travels through the pipeline,
   demonstrating the bias-propagation dynamic analysed in the thesis: the
   same root cause produces different trait failures at each stage.
3. **Thin-file uncertainty** — a data-insufficiency case where low confidence
   propagates system-wide.
4. **Silent mis-delegation** — an Orchestration-only failure: a complex case
   is delegated as routine, and the single flag fires at the *top* of the
   pipeline while every downstream agent verifies cleanly — the least visible
   kind of governance failure.
5. **Irreversible decline** — an Execution-only failure: an automated decline
   that cannot be unwound is instantiated below the required confidence bar,
   while everything upstream verifies.

## How it runs

The demo replays **scripted representative pipeline runs** — deterministic
outputs authored to exercise each trait-specific rule — so the site works
instantly for any viewer with no API key and no backend. The agent role
definitions and system prompts for a live LLM-backed version are retained in
the source as documentation of each role's design.

## Tech stack

Single-file vanilla HTML/CSS/JS — no build step, no dependencies, no network
calls. Design language follows University of Edinburgh brand colours
(University Blue `#041E42`, University Red `#D50032`), Playfair Display for
headers, IBM Plex Mono for ledger data.

## Status and roadmap

This version implements the dissertation's Chapter 2 conceptual framework:
the role taxonomy, the TRINE trait definitions, and trait profiles derived
from the trait-distribution analysis in Section 2.3.2. The per-trait
numerical scores (1–5) and flagging thresholds are illustrative
placeholders pending the finalised governance requirements in Chapter 6, at
which point they will be replaced with the framework's actual calibrations.
See `ARTEFACT_NOTES.md` for the full mapping between demo features and
dissertation sections.

## Author

Built by Francesca Beaumont as a companion artefact to my MSc dissertation,
and as an ongoing portfolio piece.
