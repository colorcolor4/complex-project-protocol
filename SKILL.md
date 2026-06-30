---
name: complex-project-protocol
description: Three-stage design protocol for large, complex projects — especially scientific and engineering work (systems, solutions, architectures, algorithms) that requires trade-offs before building. Trigger when starting such a project, or when the global CLAUDE.md brake routes a "large + design-class" task here. Stages advance only on explicit approval; each finished stage writes a fixed English summary to protocol/S<n>.md so work can resume cold. Not for small tasks or large-but-non-design tasks (those run directly after the brake).
---

# Complex Project Protocol

Design work only (system / solution / architecture / algorithm requiring trade-offs).
Large-but-non-design tasks run directly after the brake — do **not** invoke this.

## Operating mode

- **A stage spans as many exchanges as it needs** (propose → discuss → decide). Keep iterating within the current stage; **advance to the next stage only on the user's explicit go.**
- **Continuous run (opt-in).** Default = stop at each stage boundary. If the user explicitly says to run straight through (e.g. "跑完 S1–S3 / run all stages"), proceed across stages without pausing: write each `protocol/S<n>.md` as you go, and make the trade-off calls yourself from the aligned goal + stated assumptions, logging each under `## Decisions` / `## Rejected`. Two hard stops remain: pause for any fork that genuinely **can't** be defaulted (ask, don't guess), and stop before the final handoff (`CC_Develope_Spec.md`) for approval.
- **Orient when resuming cold** (new session / after compaction): read the latest `protocol/S*.md`, then open with one line — *"We're in S<n>; settled: …; open: …"*. Highest-numbered file = current stage; none = start S1. Create `protocol/` (under the project working dir) if missing.
- **Write `protocol/S<n>.md` only when that stage is approved-done**, right before advancing — never mid-discussion. Use the Stage Summary structure below; English, Markdown + LaTeX, self-contained so a cold round resumes with nothing else.
- **Backtracking is allowed.** To revise an earlier stage, edit its `S<n>.md` and state the downstream impact on later stages before continuing.
- The first S1 restatement **is** the global brake — restate once, not twice.
- Track two parallel lines throughout: **physics line** (real-world model) and **software line** (what gets built). Keep both visible.

## Stages

### S1 — Needs & Architecture
- Break needs down from first principles.
- Propose 2–3 top-level architectures with trade-offs; help the user decide.
- Lock the **software scope & done-definition**.
- The S1 restatement at the top is the brake itself (see Operating mode) — no second confirmation.

### S2 — Model & Gaps
- Decompose into modules.
- Per module: theoretical model, numbered equations (LaTeX, e.g. `(1)`,`(2)`), technical approach, resources.
- Right after each module's theory, flag **theory-vs-practice gaps** and failure-prone points (a real clock drifts, a real sensor reads off — leave the calibration knob).

### S3 — Implementation & Validation
- **Software contract**: file structure, function signatures, data shapes, algorithm steps bound to equation IDs from S2, dependencies.
- **Two-layer validation set**: (1) unit/analytic checks per equation, (2) integration/physical-plausibility checks end-to-end.
- No coding in chat — only the contract and the tests.

## Stage Summary (fixed structure, English, one line per bullet, conclusions only, self-contained)

```
## Stage
## Decisions
## Carry-forward
## Rejected
## Software thread   ← current scope & done-definition; numbered equation IDs; tests still to generate
## Next entry
```

## Handoff (after all three stages)

Propose generating `CC_Develope_Spec.md` (at the project root) by filling `spec_template.md` (in this skill dir).
Begin only after the user's approval. Output must be self-contained for Claude Code to implement directly.

`S3.md` holds the *conclusions* (one line per bullet); `CC_Develope_Spec.md` is their *full expansion* into an implementable spec — expand from `S1–S3.md`, don't re-derive.
