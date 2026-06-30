---
name: complex-project-protocol
description: Three-stage design protocol for large, complex projects — especially scientific and engineering work (systems, solutions, architectures, algorithms) that requires trade-offs before building. Trigger when starting such a project, or when the global CLAUDE.md brake routes a "large + design-class" task here. One conversation round = one stage; each round ends with a fixed English summary the user re-uploads as the ref for the next round. Not for small tasks or large-but-non-design tasks (those run directly after the brake).
---

# Complex Project Protocol

Design work only (system / solution / architecture / algorithm requiring trade-offs).
Large-but-non-design tasks run directly after the brake — do **not** invoke this.

## Operating mode

- **One round = one stage.** Never advance on your own; at each stage end, STOP and wait for explicit instruction.
- **Open every round by reading the prior stage summary** (the ref) to re-align before discussing.
- **End every round with the Stage Summary** (fixed structure below), in English, Markdown + LaTeX. The user uploads it as the ref for the next round.
- Track two parallel lines throughout: **physics line** (the real-world model) and **software line** (what gets built). Keep both visible.

## Stages

### S1 — Needs & Architecture
- Break needs down from first principles.
- Propose 2–3 top-level architectures with trade-offs; help the user decide.
- Lock the **software scope & done-definition**.
- The S1 restatement at the top doubles as the brake — no second confirmation.

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

Propose generating `CC_Develope_Spec.md` by filling `spec_template.md` (in this skill dir).
Begin only after the user's approval. Output must be self-contained for Claude Code to implement directly.
