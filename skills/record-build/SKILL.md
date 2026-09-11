---
name: record-build
description: Use when the user wants an engineering record built for the first time, wants an existing record advanced with new evidence or a due re-test, asks to be assessed or calibrated against their own code, asks what their CV can actually prove, says they feel lost or unsure of their level despite years of experience, or wants a skills audit of their own repositories.
---

# Build Record

## Overview

Produce an engineering record in which every claim carries its **basis** — tested under
examination, evidenced in shipped commits, attested by a named third party, or never measured.

**Core principle:** a CV is a claim; a record is a measurement. The gap between them is the
deliverable, in both directions — claims that don't hold, and shipped work the CV never mentions.

**The most common finding** is not incompetence. It is a person strong in practice and weak in
theory on the same subject, who concludes they are a fraud. Naming that split is usually the
single most valuable output.

## The four commands

| Command | Use it for | Cost |
|---|---|---|
| **`/record-build`** | First build, or advancing an existing record with new evidence or a due re-test | Long — this file |
| **`/record-show`** | Seeing where you stand: levels, strengths, weaknesses, what is blocked, what is due | Seconds |
| **`/record-add`** | Logging a certificate, course, new job, promotion, talk | Seconds |
| **`/job-fit`** | Scoring a job description against the record | ~2 minutes |

This skill handles the first one only. It has two modes:

- **build** — no record exists → Phases 0 → 6, the full first pass.
- **advance** — a record exists → re-run only the stale or unmeasured areas, append dated rows,
  never overwrite §10.

If the user only wants to *look* at the record, or to log a declared fact, hand off to
`record-show` or `record-add` instead of running any phase here.

## When NOT to use

- The user wants a resume rewritten or tailored to a job → that is resume tailoring, not this.
- The user wants a JD scored → that is `job-fit`, which consumes the record this produces.
- No access to their code and no willingness to be tested → without evidence or measurement there
  is nothing to build. Say so rather than producing a record from self-report.

## Phase 0 — Privacy, before anything else

The record holds the user's measured weaknesses, internal repository names and commit hashes.
Treat it as sensitive from the first line — but keep defects out of it entirely (see below).

- Write it to a private location. Add it to `.gitignore` before creating it, not after.
- Never publish it, paste it into a public issue, or include it in anything shared.
- **Never write bugs, vulnerabilities or code defects into the record.** If a live security
  problem turns up during the sweep, tell the user in conversation — plainly, no softening, no
  exploit — and stop there. It does not go in the file.

  Two reasons. A record naming unpatched defects in an employer's production code is a liability
  the user has to keep secret forever. And a defect is not a skill measurement: the record exists
  to hold strengths and weaknesses, not an issue tracker. The finding matters; persisting it does
  not.

## Phase 0.5 — Check what already exists

**Do this before the first sweep.** Two cases, and both change what happens next.

**1. An existing record.** Check the destination path. If `record.md` is already there, do **not**
rebuild — switch to *advance* mode:

- Read it. Report what is measured, what is stale, and what is still marked pending.
- Re-run only the areas that are stale or unmeasured. Keep §10 assessment history intact; it is
  the one thing no sweep can reconstruct.
- Append dated rows rather than overwriting. A record's value is the trend.

If the user explicitly wants a clean baseline, archive the old file (`mv`, not `rm`) and say
where it went.

**2. Prior analysis the user already has.** Ask:

> Have you had your code, CV or skills analyzed before — a review document, an assessment, a
> previous record, notes in a wiki?

This is not optional politeness. Such documents routinely contain **evidence the sweep cannot
recover**: PR review trails from an organization the current token cannot read, a former
employer's repositories, assessment scores from sessions that no longer exist. In the founding
session the live sweep could not see the work org at all, while a document on disk held the full
review analysis for it.

Treat what they hand over as evidence with a *source* label — `document (2026-09-08)` rather than
`git` — so a later reader can tell what was verified live and what was inherited.

## Phase 1 — Inventory the evidence sources

Ask the user for, and then verify:

1. **Every git identity they commit under** — name variants, personal and work emails, GitHub
   handles, `noreply` addresses.
2. **Which paths and accounts you may read. Ask; never infer.** A working directory visible
   earlier in the session is not consent to walk it — it may hold client code under NDA, a
   colleague's repository, or someone else's take-home. Name the paths back to the user before
   the first `ls`.
3. Their current CV.
4. Anything attested — recommendations, public posts naming them, awards, formal mentor roles.

> **A sweep is not complete until every identity has been checked.** Searching one handle and
> declaring the picture complete is the single most common failure of this process. In the session
> that produced this skill, sweeping a second handle surfaced six additional repositories,
> including the only evidence for an entire CV claim.

### Only pushed work counts

**A repository with no git history, or with git but no remote, is not evidence.** Code that
cannot be shown to anyone cannot support a claim on a CV or in an interview. Exclude it, and say
that you excluded it rather than listing what was there.

```bash
git -C "$repo" remote get-url origin    # empty output → local only → not evidence
git log --format='%an|%ae' | sort | uniq -c | sort -rn     # per repo
```

Practice projects and study exercises are the usual local-only case. They belong in a study
tracker, not in the record — and reclassifying a technology from "zero evidence" on the strength
of an unpushed toy is a false upgrade.

Watch for a misconfigured `user.name` (a bare `=`, `unknown`, a hostname) — attribute it by date
range against known-good commits rather than assuming.

## Phase 2 — Sweep the code for evidence

Per repository, establish commit count, active date range, and which domains the user actually
owns. Then find the work that carries a claim.

**Attribution rules — each of these was learned by getting it wrong:**

| Rule | Why |
|---|---|
| `git blame` is not authorship | A day-one bulk scaffold commit (whole lockfile, thirty classes at once) is a repo migration, not original design. Check the PR trail for who refined it afterwards |
| Volume is not ownership | 2–6 commits in one week and untouched since is migration noise. Sustained commits across months is ownership |
| Check review trails separately | Reviewing, approving and merging others' PRs is a different axis from authoring. A silent approval is merge gatekeeping, not review |
| Absence in git is not absence of skill | Teaching, pairing, design discussions and verbal direction leave no commits. Ask before scoring a people axis at zero |

**What to look for, in descending value:**

- A defect found and fixed with **real production numbers** attached ("26,000 rows for 6,000
  clients", "96% of user-days received more than one push"). This is the highest-value evidence
  that exists; it is unfakeable and it interviews well.
- The same component hardened **more than once**, each round finding a deeper problem. Distinguishes
  senior from mid better than any single commit.
- Security-relevant code: constant-time comparison, fail-closed defaults, signature validation,
  timing-leak handling. Also its opposite — check whether signature checks actually compute a HMAC.
- Deletions: a cache removed, an abstraction collapsed, a source of truth consolidated. Removing
  something that was causing bugs is stronger evidence of judgment than adding something.
- Tests written alongside fixes, especially regression tests that replay the failure.
- Design docs or ADRs committed before the feature.

## Phase 3 — Map CV claims to evidence

For each CV claim, mark: **holds** (name the commit), **partial** (say which half), **unverified**
(no evidence found, not disproven), or **does not hold**.

For a claim marked unverified, ask the user before concluding. Work often exists outside the
reachable accounts — a private org, a client repo, a machine. Two claims in the founding session
were wrongly called unverifiable this way, and both turned out real.

## Phase 4 — Measure what code cannot show

Git shows what was built. It cannot show whether the person understands why it worked. Test that.

**Format:** rounds of 5 multiple-choice questions, one competency area per round, scored per round
with an explanation of every miss. Derive the areas from their own claims and stack, not from a
generic syllabus.

**Rules:**

- `skip` is allowed and scores better than a guess. Report the raw score **and** the answered-only
  percentage; a person who skips honestly looks worse on raw score than they are.
- Prefer questions where a plausible wrong answer is the one most people give. A question everybody
  gets right measures nothing.
- **Where a subject was found in Phase 2, test that same subject here.** The divergence is the
  finding. Someone who fixed a lost update with a row lock in production and then answers that a
  transaction prevents lost update has a retrieval problem, not a knowledge problem — and that
  distinction changes the entire study plan.
- Stop and explain at each miss. The explanation is most of the value to the user.

## Phase 5 — Emit the record

Write `references/record-template.md`'s structure, filled in. Required sections:

1. Identity, experience, current level ratings
2. **The structural finding** — any practice-vs-theory split, with the proof
3. Every axis, with a score and a basis label
4. Technology inventory, split into evidenced / lighter / **zero evidence, do not claim** / unmeasured
5. Signature evidence, each with its commit reference and what it demonstrates
6. Repositories swept, with commit counts
7. Claims not yet defensible, with the gate that would clear each
8. **Credentials & milestones** — degrees, certificates, formal roles, talks. Basis `declared` unless a link exists
9. Market-required gaps, if they have applied anywhere
10. Assessment history, dated
11. Prior job-fit scorings

**Every score states its basis.** A number without a basis is an opinion wearing a measurement's
clothes.

## Phase 6 — Make it a record, not a snapshot

- Set a re-test date and put it in the record. **Re-test on the calendar, not on the feeling** —
  the "I feel lost" feeling recurs while the person is measurably competent.
- Scores regress. The founding session saw concurrency go 3/5 → 1/5 over five weeks, visible only
  because there was a history. A one-shot assessment cannot see this.
- **Reading a documented belief does not correct it.** Where a belief inversion is found, the gate
  is a runnable artifact that fails if the belief is wrong — not a re-read. That specific inversion
  was written down, re-read, and still wrong five weeks later.

## Common mistakes

| Mistake | Fix |
|---|---|
| Rebuilding over an existing record | Check for one first. Advance it; never discard the assessment history |
| Not asking for prior analysis | Old review documents hold evidence a live sweep cannot reach. Ask in Phase 0.5 |
| Sweeping one git identity | Check every handle and email before claiming the sweep is complete |
| Walking a directory without asking | Get the paths named first. Visible ≠ permitted |
| Counting local-only repos as evidence | No remote means nobody can see it. Exclude it |
| Crediting someone else's repo | Check the remote owner and the commit split before attributing |
| Crediting design from `git blame` | Check who refined it in PRs afterwards |
| Scoring a people axis from git | Ask. Teaching leaves no commits |
| Testing theory only | Find the same subject in their code. The gap is the finding |
| Producing a flat average | A bimodal 92%/33% profile and a flat 63% are different people. Never collapse them |
| Treating unmeasured as weak | Unknown is unknown. Label it and say so |
| Writing a defect into the record | Report it in conversation. The file holds strengths and weaknesses, not bugs |
| Letting a certificate move an axis | A credential changes the claim status in §7, not the score in §3 |
| Calling the output a measurement | It is calibrated judgment against a rubric. Say that in the record |
