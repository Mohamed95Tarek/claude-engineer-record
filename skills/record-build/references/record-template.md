# Engineer Record — {NAME}

> Evidence base for job-fit scoring and study planning.
> **This file is the updatable part.** Edit it as results change; leave SKILL.md alone.
> Last updated {DATE}. Sources: {N} assessments ({FIRST} → {LAST}), git sweep of {N}
> repositories, {N} third-party attestations.
>
> ⚠️ Private. Contains internal repository names and personal weakness scores. Do not publish.
> Keep it gitignored or in a private repo.
>
> **No bugs or vulnerabilities are recorded here, by design.** Defects found during a sweep are
> reported in conversation and not persisted — this file holds strengths and weaknesses, not an
> issue tracker.
>
> Scores are calibrated judgment against a rubric, not psychometrics. Their value is that each one
> states how it was obtained.

## 1 · Identity & headline

- Location. Degree, institution, years.
- **{N}+ years** professional experience. Current role, employer, dates.
- Prior roles with dates.
- Languages.

| Rating | Score | Note |
|---|---|---|
| Software engineer, overall | **/10** | |
| Backend — {primary stack} | **/10** | Primary stack |
| Backend — {secondary stack} | **/10** | |
| Career stage | | What the next level actually gates on |

## 2 · The structural finding — read before scoring anything

*State any practice-vs-theory split here, with proof. If there is none, say so — a flat profile is
a different person from a bimodal one and the distinction drives everything downstream.*

| Subject | In practice | As theory |
|---|---|---|
| | | |

**Proof:** name the two artifacts that contradict each other — ideally two files in the same
repository, one implementing the pattern correctly and one getting it wrong.

**Implication for scoring:** which kind of interview round each subject will survive.

## 3 · All axes

Basis: `test` = answered under examination · `git` = evidenced in commits · `att` = third-party
attested · `doc` = inherited from a prior analysis, not re-verified · `declared` = the user's own
statement · `—` = unmeasured

### Engineering execution
| Axis | Score | Basis |
|---|---|---|
| Debugging & root-cause analysis | | |
| Production correctness & data integrity | | |
| Concurrency — in practice | | |
| Concurrency — as theory | | |
| Testing discipline | | |
| Code hygiene | | |

### Technical depth
| Axis | Score | Basis |
|---|---|---|
| {Primary framework} internals | | |
| {Secondary stack} | | |
| DB engine — in practice | | |
| DB engine — as theory | | |
| Security — in practice | | |
| Security — as theory | | |
| Domain modelling / DDD | | |

### Systems & design
| Axis | Score | Basis |
|---|---|---|
| Architecture & design judgment | | |
| Event-driven architecture | | |
| Multi-tenancy | | |
| Caching / queue mechanics | | |
| Microservices — boundaries | | |
| System design at scale | | |

### Delivery & breadth
| Axis | Score | Basis |
|---|---|---|
| Integration breadth | | |
| Domain ownership | | |
| DevOps · CI-CD · containers | | Note whether verified beyond a single service |
| Full-stack / frontend | | |
| Parallel throughput | | |

### People & communication
| Axis | Score | Basis |
|---|---|---|
| Mentoring & teaching | | Often `att`; git cannot see it |
| Code review quality | | Distinguish substantive review from silent approval |
| Peer influence / tech leadership | | |
| Articulation under questioning | | |

## 4 · Technology inventory

**Strong, evidenced:**

**Used, older or lighter:** *(say how old — three-year-old MongoDB is not current MongoDB)*

**Zero evidence — do not claim:**

**Unmeasured, unknown (not weak):**

**Integrations shipped:**

## 5 · Signature evidence — cite these by name

| Work | Reference | What it demonstrates |
|---|---|---|
| | commit / PR / date | Prefer entries carrying real production numbers |

*Mark anything needing verification — a PR that shows merged but whose code is absent from the
current checkout, for instance — before it is used to support a claim.*

## 6 · Repositories swept

`repo` count · `repo` count · … · note which were founded by the user, and which show
review-only participation.

Identities checked: *(list every handle and email — an unlisted identity means an incomplete sweep)*

## 7 · Claims NOT yet defensible

| Claim | Status and the gate that clears it |
|---|---|
| | |

## 8 · Credentials & milestones

*Facts that cannot be swept or tested. Basis `declared` unless a verifiable link exists, in which
case `attested`. A credential changes a claim's status in §7 — it does not move a score in §3.*

| Date | Item | Basis | Effect on the record |
|---|---|---|---|
| | Degree, certificate, formal role, talk, published package | `declared` / `attested` | e.g. "moves Kubernetes from *no evidence* to *certified, no shipped artifact*" |

**Employment changes.** When a role starts or ends, note it here and say what it does to
verifiability: the former employer's repositories become historical, and the new role has no
evidence until work lands.

## 9 · Market-required gaps

| Gap | Demand seen across roles applied to |
|---|---|
| | |

## 10 · Assessment history

| Date | Test | Score |
|---|---|---|
| | | |

**Next re-test due: {DATE}** — on the calendar, not on the feeling.

Behavioural note: *does this person skip or guess when unsure? It changes how to read every score.*

## 11 · Prior fit scorings

| Role | Fit | Binding gaps |
|---|---|---|
| | | |
