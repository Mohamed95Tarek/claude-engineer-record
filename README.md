# Engineer Record

**Find out what your CV can actually prove.**

Four Claude Code skills that build a record of your engineering ability from evidence — your own
commits, your own answers — and then score job descriptions against it.

A CV is a claim. This produces a record where **every score states how it was obtained**: tested
under examination, evidenced in shipped commits, attested by a named third party, or never
measured at all.

---

## Why this exists

Most job-search tooling matches keywords. You hand it a CV and a job ad, and it tells you how well
two documents overlap. Neither document is evidence.

This does the opposite. It reads your git history to find what you can actually demonstrate, tests
you on the theory behind the code you've shipped, and writes down which is which. The output is
often uncomfortable and occasionally the opposite of what you expected.

The most common finding is not incompetence. It is someone **strong in practice and weak in theory
on the same subject**, who has quietly concluded they are a fraud. In the session that produced
these skills, the record showed:

| Subject | In practice | As theory |
|---|---|---|
| Concurrency / locking | 8.5 / 10 | 4 / 10 |
| Security | 8 / 10 | 2 / 10 |
| DB internals | 7 / 10 | 4 / 10 |

Correct locking primitives shipped in three independent codebases, in two languages — and the same
concept missed five times on a written test. That is a **retrieval** problem, not a knowledge
problem, and it changes the entire study plan. No keyword matcher can see it.

---

## The four commands

| Command | Use it for | Cost |
|---|---|---|
| **`/record-build`** | Build the record, or advance it with new evidence | 2–3 hours, once |
| **`/record-show`** | Where you stand: levels, strongest and weakest axes, what's blocked, what's due | seconds |
| **`/record-add`** | Log a certificate, course, new job, promotion, talk | seconds |
| **`/job-fit`** | Paste a job description, get scored against the record | ~2 minutes |

Each also fires from plain English — *"what are my weaknesses"*, *"I got AWS certified"*,
*"am I a fit for this role"*.

---

## Install

```bash
git clone https://github.com/Mohamed95Tarek/claude-engineer-record.git
ln -s "$PWD/claude-engineer-record/skills/record-build" ~/.claude/skills/record-build
ln -s "$PWD/claude-engineer-record/skills/record-show"  ~/.claude/skills/record-show
ln -s "$PWD/claude-engineer-record/skills/record-add"   ~/.claude/skills/record-add
ln -s "$PWD/claude-engineer-record/skills/job-fit"      ~/.claude/skills/job-fit
```

Then run `/record-build` in Claude Code.

**Requirements:** Claude Code. Local clones of your repos, or the [GitHub CLI](https://cli.github.com)
authenticated (`gh auth status`) — without it you lose PR review trails and repo discovery, but the
commit evidence and the assessment still work.

---

## What `/job-fit` produces

Paste a job ad and you get a requirement-by-requirement table where each row is marked:

- 🟢 evidenced or tested at the bar — **naming the commit, score or attestation**
- 🟡 partial — adjacent, older, or strong in practice and weak in theory
- 🔴 a real gap
- ⚪ never measured — **unknown, not weak**

Then: what gets you the interview, what sinks the technical round and the measured score that
predicts it, honest probability ranges for the screen and the technical, and the shortest prep
that turns a red row amber.

---

## What it deliberately does not do

- **No bugs in the record.** If the sweep finds a live security defect it is reported to you in
  conversation and never written to the file. A record naming unpatched defects in your employer's
  production code is a liability you would have to keep secret forever, and a defect is not a
  skill measurement.
- **A credential never moves a score.** Tell it you're Kubernetes certified and the *claim* status
  changes from "no evidence" to "certified, no shipped artifact". The axis stays where it was until
  code exists. Otherwise it's a CV again.
- **Local-only code is not evidence.** A repository with no remote can't be shown to anyone, so it
  can't support a claim. Practice projects belong in a study tracker.
- **Unmeasured is never reported as weak.** Unknown is unknown.
- **It won't write your resume.** That's a different tool and there are several good ones.

---

## The hard-won rules

Most of the value sits in the attribution rules, each learned by getting it wrong:

- **A sweep is incomplete until every git identity is checked.** One missed handle hid six
  repositories, including the only evidence for an entire CV claim.
- **`git blame` is not authorship.** A day-one bulk scaffold commit is a repo migration, not
  original design. Check who refined it in PRs afterwards.
- **Volume is not ownership.** Six commits in one week and untouched since is migration noise.
- **Absence in git is not absence of skill.** Teaching, pairing and design conversations leave no
  commits. The skill asks rather than scoring a people axis at zero.
- **Reading a documented belief does not correct it.** A wrong belief was written down, re-read,
  and still wrong five weeks later. Belief inversions get a **runnable-artifact gate** — something
  that fails if the belief is wrong — not a re-read.
- **Never collapse a bimodal profile into an average.** 92% / 33% and a flat 63% are different
  people.

---

## Honest limitations

**The scores are calibrated judgment against a rubric, not psychometrics.** There is no validation
cohort, no test-retest reliability study, no norming. What they offer instead is that each number
states its basis, links to evidence, and can be re-tested on a schedule so you can see it move.

**It is written from a sample of one.** The phases were derived from auditing a single engineer's
13 repositories and ten assessments. Some of it will generalise and some of it is that person's
shape. If you run it and a phase only works because the author already knew the answer, open an
issue — that's the most useful contribution available.

**Assessment results cannot be re-derived.** Git evidence regenerates any time. Test scores exist
only because you sat and answered. Back the record up.

**Your record is private by default and should stay that way.** It names internal repository names
and your own weaknesses. A `.gitignore` covering `record.md` and any archive ships with it.

---

## License

MIT
