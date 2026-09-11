---
name: job-fit
description: Use when the user asks whether they are a fit for a job, pastes a job description or job ad, asks to be rated or scored against a role, asks what to study before applying or interviewing, or asks which of several roles to pursue.
---

# Job Fit

## Overview

Score a job description against a **measured** engineering record rather than against a CV. The
record separates what was tested, what is evidenced in shipped commits, what a third party
attested, and what was never measured — so a fit score says how it was known, not just how high
it is.

**Core principle:** unmeasured is not weak. Report it as unknown and say so.

## Procedure

1. Read `references/record.md` in full. It is the only source of truth about the candidate.
   Do not score from memory, from a CV, or from earlier conversation.
2. Extract every requirement the JD states, including the ones buried in prose ("root cause
   analysis", "rapidly growing company"). Keep the JD's own wording.
3. Score each requirement against the record.
4. Produce the output below.

## Scoring legend

| Mark | Meaning |
|---|---|
| 🟢 | Evidenced or tested at or above the bar. Name the commit, score, or attestation |
| 🟡 | Partial — adjacent experience, older experience, or strong in practice but weak in theory |
| 🔴 | Gap. Measured low, or zero evidence for something the JD names as required |
| ⚪ | Never measured. Unknown, not weak |

## Output contract

Produce exactly these parts, in this order:

1. **Fit score** — two numbers, never one: **fit today** and **fit after the prep in item 6**,
   with a one-line reason. Then state whether the gaps are *closable* or *capped*.

   A single number reads as a verdict when it is only a snapshot. Two roles can both score 5.5
   today and deserve opposite advice — one because every gap closes with study and a pushed
   artifact, the other because the binding requirement is years of experience in a role the
   candidate has never held. Say which kind it is in the same breath as the number.

   Format: `Fit today: X/10 · after ~Nh: Y/10 · gaps: closable | capped`
2. **Requirement table** — one row per JD requirement: requirement · what the record holds · mark.
   Every 🟢 row names its evidence.
3. **What gets the interview** — the two or three strongest matches, tied to the employer's stated
   problem, not to generic strengths.
4. **What sinks the technical round** — the specific questions an interviewer would reach for, and
   the measured score that predicts the answer.
5. **Probabilities** — CV screen, technical round as-is, technical round after prep. Ranges, with
   the reasoning visible.
6. **Shortest prep** — a table of tracks, hours, and which requirement each one turns from red to
   amber. Prefer prep that produces a linkable artifact over prep that produces a claim.
7. **Verdict** — apply now, apply after N hours, or skip. One paragraph.

## Rules

- **Separate practice from theory.** Where §2 of the record documents a practice-vs-theory split,
  score the requirement and then say which kind of round it will be probed in. A candidate strong
  in practice and weak in theory on the same subject passes code-reading and practical rounds and
  fails rapid-fire theory questions on that subject. Say so explicitly rather than averaging.
- **Never upgrade a blocked claim.** Section 7 lists claims that are not yet defensible. A strong
  shipped artifact does not clear a blocked claim — both facts go in the row.
- **A score is not a probability.** "6.5/10 fit" means the requirements partially match. Say that
  rather than implying a hiring chance.
- **A score is not a recommendation either.** The highest-scoring role is often the wrong target —
  a strong match to a role a level below the candidate is a band reset that follows them into
  every later negotiation. Weigh title against the record's own career-stage rating in §1, and
  say so in the verdict. Where a lower score has closable gaps and a higher one is a level down,
  recommend the lower score and explain why.
- **Flag anything the record marks for verification** — a PR that shows merged but whose code is
  absent from the current checkout, an axis marked stale — before using it to support a row.
- **Surface an open gate when the JD touches it.** Where a JD asks for something §7 lists as not
  yet defensible, say both halves: the shipped evidence *and* the reason the claim is still
  blocked. A strong artifact does not clear a blocked claim.
- If several roles are compared, score each separately, then say which shares the most prep with
  the others.

## Keeping the record current

`references/record.md` is the updatable part. After any new assessment, git sweep, shipped
artifact, or closed gate, edit the relevant section and the date at the top. Sections most likely
to move: §3 axes, §7 blocked claims, §8 credentials, §10 assessment history, §11 prior scorings.

Leave `SKILL.md` alone unless the output contract itself should change.

## Common mistakes

| Mistake | Fix |
|---|---|
| Scoring from the CV instead of the record | The CV is a claim. The record is a measurement. Read the record |
| Treating ⚪ as 🔴 | Unmeasured means unknown. Say unknown |
| Inflating a 🟡 because adjacent experience exists | MongoDB in 2019 is not MongoDB now. Say when the experience is old |
| Reporting a fit score as a hiring probability | Separate items 1 and 5 of the output contract |
| Printing one fit number | Always print fit-today and fit-after-prep. One number hides whether the gaps move |
| Recommending the highest score | Check the title against §1's career stage. A high fit one level down is a demotion |
| Recommending prep that only produces a talking point | Prefer prep that ends in a committed artifact |
| Running repeated fit checks instead of closing a gap | Scoring five JDs moves no axis. If the prep converges on the same tracks, say so and stop |
