---
name: record-add
description: Use when the user reports something to log against their engineering record — a certificate, a course finished, a new job, a promotion, a talk given, a published package, a recommendation received, or a shipped side project.
---

# Record Add

Log a declared fact into the engineering record. **No sweep, no test.** Seconds, not minutes.

## Where it lives

`~/.claude/skills/job-fit/references/record.md` — section 8, *Credentials & milestones*.

If there is no record, say so and point at `record-build`.

## What to do

1. Append a row to §8: date, item, basis, effect.
2. Basis is `declared` — the user's own statement. If they give a verifiable link (credential URL,
   talk recording, published package, public repo), record the link and use `attested` instead.
3. Update the `Last updated` line at the top of the file.
4. Say what changed in one or two lines. Do not re-render the whole record.

## The rule that matters

**A declared fact never moves an axis score.**

A certificate changes a *claim's status* in §7, not a *score* in §3. Say it explicitly:

> AWS certification logged. Kubernetes moves from "zero evidence — do not claim" to
> "certified, no shipped artifact." The axis stays at 0 until code exists.

Scores move only on tested answers or shipped commits. That distinction is the whole point of the
record; a credential that raised a score would make it a CV again.

## Special cases

| Item | Also do this |
|---|---|
| **New job** | Note in §8 that the prior employer's repositories are now historical, and the new role has no evidence until work lands. Ask whether a new git identity or org comes with it |
| **Promotion** | Record it, but do not touch the career-stage rating in §1 — that is measured, not granted |
| **Course finished** | If it targets a known weak axis, say the axis is still unmeasured and suggest the re-test that would move it |
| **Shipped side project** | This is evidence, not a declaration. Offer to sweep it with `record-build` in advance mode |

## Related

`record-show` to view · `record-build` to advance with real evidence.
