# Design B — Pure Inter-Participant Translation

> **Premise.** There is no common `X` — or it is unavailable, or not agreed. Participants
> have their own domains, ontologies, logics and state spaces. Some observe each other.

There is nothing to intersect. What exists instead is a **network of partial translations**,
and the system's knowledge is the *coherence structure* of that network rather than a
shared estimate of anything.

---

## What replaces fusion

Objects are participants' perspectives (each with its own ontology `Oᵢ`, logic `Lᵢ`, state
space). Morphisms are translations `F: Oᵢ → Oⱼ` with declared `Loss(F)`. The system is a
category of perspectives, and **in general there is no global section** — no single
description all views project from. That is not a defect to be engineered away. It is the
premise.

### Bridges are the primary artifact

In A, observations matter most. In B, **building a bridge is the contribution.** A
participant that produces a working translation between two previously incommensurable
perspectives has done more than one that produces another observation.

Bridges carry named loss (D11t), worked examples, and — most valuable — *counterexamples*:
instances where the translation demonstrably fails. A bridge without known failure cases is
an untested bridge.

### Holonomy replaces empty intersection

The Design A alarm has an exact Design B counterpart. Compose translations around a cycle:

```
F_ki ∘ F_jk ∘ F_ij  ≟  identity
```

If a claim translated around a loop does not come back to itself, the translation network
is **path-dependent**. Non-trivial holonomy means the perspectives cannot be globally
reconciled, and it localizes *where* — which edge of which cycle carries the discrepancy.

This is computable, meaningful, and it is the only convergence-style signal available
without a shared referent. It is also the same obstruction machinery as B5, so it needs no
new subsystem.

### Truth is local and coherence-constrained

A claim is valid *in* a perspective. Cross-perspective validity means **transportability
along bridges with acceptable loss**. "True" without a frame index is not a well-formed
statement in Design B.

### Agreement is weak evidence — and sometimes anti-evidence

This is the inversion specific to B, and it is easy to get backwards.

Two participants appearing to agree may be agreeing only because `Loss(F)` destroyed the
distinction that separated them. **Lossy translation manufactures consensus.** So agreement
must be re-checked at the *finest common refinement* of the two perspectives; if it does
not survive there, it was an artifact of the bridge.

Combined with B4 (correlated observers), Design B leaves agreement carrying very little
weight. Almost all the information is in the disagreements and in the structure of the
translations themselves.

### Disagreement is the primary product

The full eight-type taxonomy (D3t) gets a real workout here, and **ontological mismatch
dominates** — the case that barely appears in Design A. D3's "generative boundary" is the
normal operating condition rather than an exception: two models each work well and fail to
connect, and the failure locates where a coupling is missing.

### Probes target bridges, not the world

C3 changes character. The question is not "what observation discriminates hypotheses about
`X`" — there is no `X`. It is:

- *What would improve this translation?*
- *Can anyone construct an instance where this bridge fails?*
- *What is the finest refinement at which these two still agree?*

Counterexample solicitation is the dominant probe form.

### Quality signals without ground truth

No calibration is possible — there is no outcome to score against. Two signals remain, and
they are the only ones:

1. **Yield** (D4t/C4) — does this participant's disagreement produce artifacts?
2. **Bridge quality** — do translations through this participant compose well (low
   holonomy, low loss, few counterexamples)?

Both are real, and neither is a popularity contest, which matters given the next section.

---

## Repo shape

```
perspectives/<name>/
  ontology/           # Oᵢ — what kinds of things exist, per participant
  logic/              # Lᵢ — inference rules in use
  membrane/           # == πᵢ; here it is a boundary between ontologies, not onto a shared H
  claims/             # valid in-frame; never asserted unqualified
  viability/ regimes/ regulators/ core/
bridges/
  <Oᵢ→Oⱼ>/            # F, named Loss(F), worked examples, counterexamples
  composition/        # holonomy checks around cycles; path-dependence findings
  pivots/             # hub ontologies used as intermediate languages
coherence/
  internal/           # each perspective consistent on its own terms
  transport/          # cross-perspective claim movement with loss accounting
tensions/             # full 8-type taxonomy; ontological mismatch dominates
yields/               # the primary quality signal
ledger/  probes/  verdicts/  theories/  levels/  substrate/  observatory/
```

---

## Failure modes

**Relativism drift.** If everything is valid in its own frame, nothing can be wrong, and
the system degenerates into a catalogue of opinions. Three things remain binding and must
be enforced, or B is worthless:
- internal coherence — a perspective can fail *on its own terms*;
- holonomy — translation cycles must close, or the discrepancy must be located;
- yield — a perspective that never produces artifacts is not contributing.

**No convergence.** B accumulates perspectives without necessarily getting sharper. The
yield gate (D4t) is the only pressure toward progress, which makes it non-optional here
rather than merely important.

**Consensus creep.** Without an `X`, the pull toward treating majority as truth is strong
and completely unjustified — there is nothing for a majority to be right *about*. This
needs an explicit guard: vote counts are not a status in this system, and B4 already
explains why they would be untrustworthy even if they were.

**Bridge combinatorics.** `n` perspectives admit `n²` bridges. Do not build the complete
graph. Build a spanning structure with a few **pivot ontologies**, accept that some pairs
communicate only through composition, and track accumulated loss along composition paths —
a claim transported through three bridges has three losses stacked, and that must be
visible at the destination.

---

## Choose B when

- Participants are genuinely heterogeneous — different disciplines, organizations, goals,
  or agent architectures.
- No shared ontology is achievable, or forcing one would destroy what makes participants
  individually valuable.
- The point is not truth about a common object: negotiation, design, planning, values,
  interpretation.
- Participants will not or cannot expose enough internals to be modeled as instruments.

Typical fits: cross-disciplinary or cross-organizational systems; federated participants
under separate ownership; agents with different objectives rather than different views of
one objective; any setting where "whose model is right" is the wrong question.
