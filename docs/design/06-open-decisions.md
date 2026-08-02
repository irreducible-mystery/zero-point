# 06 — Open Decisions, Risks, and Falsifiers

## Open decisions

Ordered by how much they change the build.

### 1. A / B / C — the fusion fork
Laid out in `02`–`05`. Recommendation: **C, built in B's shape.** Still yours to make.

### 2. What are the participants, concretely?
Still unanswered, and it changes the meaning of nearly every mechanism:

- **Language-model agents** — B4 (independence ledger) becomes critical rather than
  prudent, because correlated blindness is the default and is invisible. `θᵢ` includes the
  model, the prompt, the retrieval corpus, and the context window.
- **Network services / instruments** — `θᵢ` and `εᵢ` are modelable, so Design A is
  genuinely available and calibration works.
- **Humans** — not instrumentable. Their reports carry judgment, not measurement, and
  modelling them as sensors is a category error that Design B's ontology bridges exist to
  avoid.
- **Simulation entities** — `F` is known exactly, so B6 commutation tests become the
  strongest available tool.
- **Mixed** — almost certainly the real answer, and it argues for C.

### 3. How independent is independent?
Same process → membrane (A1) is a lint rule. Separate machines → it is a protocol. Separate
owners → it is a trust boundary, and D12t (certificates) stops being optional. Monorepo
with hard internal membranes is recommended for the first two; the third forces a spec repo
plus federation.

### 4. Does the collective act, or only know?
If it acts, C3 (probes) and D2's §16 action-relevant projection become the spine, and
"which distinctions matter" gets settled by consequences rather than taste — a much better
teacher. If it only knows, the yield gate (D4t) is doing all the work of keeping the system
honest, alone.

### 5. Do participants carry history?
Identity-through-continuous-history (D1) only means something if there is persistent state
to carry. Long-lived stateful participants make A4 (regimes), A6 (morphology) and A7 (scar
log) meaningful. Stateless responders make most of Group A decorative.

### 6. Runtime and language
Elixir/OTP gives A1, A4 and A7 nearly for free — supervision trees, let-it-crash, and
reconciliation are the platform's native model. Weigh that against the ecosystem you
actually want for the epistemic layer, which is the larger body of code.

### 7. Governance of bridges and ontologies
Who may declare an ontology, author a bridge, or assert a `Loss(F)`? In B and C this is the
main extension point, so it is also the main attack surface for incoherence. Unresolved.

### 8. Tension lifecycle and storage
The yield gate (D4t) bounds the *active* set. Still undecided: retention policy for
archived residue, and whether a retired tension can be reopened by anything other than its
`reopening_trigger`.

### 9. Is `practical_opposition` acceptable?
See the paralysis risk below. A status weaker than logical contradiction but strong enough
to force a choice would relieve it — at the cost of some of D1t's purity.

---

## Risks

**Paralysis — the cost of the non-opposition default.** If contradiction requires seven
alignment conditions and each is challengeable, the system may never conclude anything.
This is the serious objection to D1t. Three guards are required, not optional:
a classification budget (D6t applied to the classifier itself), a weaker
`practical_opposition` status sufficient to force a decision without asserting logical
contradiction, and operational closure with declared residue (D5t). Without them,
"opposition must be demonstrated" degrades into "nothing is ever decided."

**The classifier is a semantics problem in an engineering costume.** "Same referent, same
sense, same scale" is the hard part of meaning. If participants are language models it will
be unreliable in both directions. Making the classifier's output a challengeable claim
helps; do not under-budget it. Every path through this design routes through it.

**Envelope weight.** `Cᵢ = (p, O, L, S, T, D, M, R)` is eight fields nobody will fill in.
Inheritance from registered participant defaults, with claims carrying only deltas, is
mandatory rather than an optimization.

**Correlated model-driven observers.** Stated three times in this document set because it
is the most likely way the system produces confident nonsense. Same base model plus same
context equals one observer, regardless of headcount.

**Metaphor tax.** Biological vocabulary that does not do work is a cost paid by every future
contributor. The naming rule in the README is a real constraint, not a stylistic note.

**Framework before metabolism.** This design is seductive enough to build indefinitely
without anything flowing through it. Two real participants producing real disagreement, on
a real domain, before more than the spine gets built.

**Orchestrator creep.** D1's §4 says no scale carries the whole pattern. The likely betrayal
is a "coordinator" that becomes the brain. C2 (plural synthesizers) is the structural
defence; if one component knows every participant by name, identity has centralized.

**Over-typing.** Eight tension types × four status axes × four ontology-compatibility values
is a taxonomy nobody holds in their head on day one. Start with three tension types.

**Design-specific:** `H` as the collective blind spot (A) · relativism drift and bridge
combinatorics (B) · premature promotion (C).

---

## What would falsify parts of this design

Worth writing down now, while it is cheap to be honest.

- **If the tension store fills with low-yield entries**, the typing is wrong or the
  participants are not epistemically diverse — C4's per-pair yield scoring will show which.
- **If `n_eff` is almost always ≈ 1**, the participant set is not actually plural and the
  entire collective-observation premise is unearned. Fix the roster, not the math.
- **If no region ever earns an A-mode certificate**, either the domain is genuinely
  incommensurable (Design B was right, drop C's machinery) or the certificate thresholds
  are miscalibrated.
- **If every region earns one immediately**, Design A was right and C is overhead — but
  check the drills first, because premature promotion looks exactly like this.
- **If commutation leakage (B6) is unmeasurable everywhere**, no participant has a modeled
  dynamics, and the abstraction-quality claims in this design are aspirational rather than
  testable.
- **If the classifier's `unclassified` backlog grows without bound**, the paralysis risk has
  materialized and `practical_opposition` is needed.

---

## Immediate next step, when we decide to build

Not the framework. The spine from `01`, applied to two real participants with a real
disagreement:

1. `B1` observation envelope, with inheritance so it is not painful.
2. `B2` blind-spot manifests for both participants.
3. `B4` independence ledger, crude version.
4. `D1t` + `D3t` with three tension types.
5. `D4t` yield gate and `D5t` decision/closure split.
6. `C1` structured `M`.

Everything else waits for traffic to justify it.
