# complex-project-protocol

A Claude Code skill: a **three-stage design protocol** for large, complex projects — especially scientific and engineering work that needs trade-offs decided *before* any code is written.

It pairs with a small always-on brake in your global `~/.claude/CLAUDE.md`:

- Small task → answer directly.
- Large task → stop, restate Goal / Success criterion / Assumptions, await approval.
- Large **+ design-class** (system / architecture / algorithm) → run this skill.

## The three stages

One conversation round = one stage. Each round ends with a fixed English summary you re-upload as the ref for the next round.

1. **S1 — Needs & Architecture**: first-principles needs breakdown; 2–3 architectures with trade-offs; lock software scope & done-definition.
2. **S2 — Model & Gaps**: module decomposition; per-module theory with numbered LaTeX equations; flag theory-vs-practice gaps.
3. **S3 — Implementation & Validation**: software contract (files, signatures, data shapes, algorithm steps bound to equation IDs) + two-layer validation set. No coding in chat.

After all three: fill `spec_template.md` → `CC_Develope_Spec.md`, a self-contained spec Claude Code implements directly.

## Install

```sh
git clone https://github.com/colorcolor4/complex-project-protocol ~/.claude/skills/complex-project-protocol
```

## Files

- `SKILL.md` — the protocol (loaded on trigger).
- `spec_template.md` — handoff template for the final spec.
