---
name: record-show
description: Use when the user asks to see their engineering record, asks where they stand, what their level is, what their strengths or weaknesses are, what is blocked, or what study or re-test is due.
---

# My Record

Read the engineering record and render it. **Never sweep, never test, never rebuild.**

## Where it lives

`~/.claude/skills/job-fit/references/record.md`

If it is missing, look for `record.archived-*.md` in the same directory, render the newest one,
and say it is an archive rather than the live record. If neither exists, say so and point at
`record-build`.

## What to show

Keep it terminal-length. Five parts, in order:

1. **Levels** — the ratings table from §1, with deltas where the record has them.
2. **Strongest five axes and weakest five** — from §3, each with its basis label. Sort by score.
3. **The structural finding** — §2, if there is one. Two or three sentences.
4. **Blocked** — §7, as claim → the gate that clears it.
5. **Due** — the re-test date from §10, plus anything parked or pending.

End with the file path. Do not dump the file.

## Rules

- Every score carries its basis. A number without one reads as an opinion.
- `—` or unmeasured is not weak. Say unknown.
- Never collapse a practice-vs-theory split into one average — the gap is the point.
- If the user asks for a chart or a page, offer one; otherwise plain text.

## Related

`record-build` to create or advance it · `record-add` to log a certificate or a new job ·
`job-fit` to score a job description against it.
