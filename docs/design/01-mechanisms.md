# 01 — Mechanism Catalog

The durable core. Each mechanism states the claim it encodes, its concrete shape, and its
source. Tags indicate build priority:

- `core` — cheap, high leverage, do first. These eight or so are the spine.
- `strong` — real value, moderate cost.
- `deep` — research-flavoured or expensive. Defer until the system earns it.

---

## Group A — Boundary and identity

### A1 · Membrane `core`
**Claim (D1 §1, D2 §16).** Every participant maintains a selectively permeable boundary,
which is also its projection. Fully closed starves; fully open dissolves.
**Shape.** `participants/<name>/membrane/` declares what it accepts, what it emits, and an
admission policy (validation, rate, trust, backpressure). Enforced *structurally*:
participants may import only `contracts/` and `substrate/`, never each other. CI fails on
violation, so the module dependency graph is the membrane topology.

### A2 · Viability envelope `core`
**Claim (D1).** `x(t) ∈ Ω`, not `x(t) = x(0)`. Identity is a maintained regime.
**Shape.** Replace boolean health with `viability() → {inside, margin, violations}`. Ω is a
set of predicates over observable state. Restart, degrade, shed-load and alerting key off
*margin and trajectory*, so action happens while approaching the boundary rather than
after crossing it.
**Prior art.** Aubin's viability theory; the viability kernel is literally Ω.
**Note.** This report is itself a projection (A1) and carries a fiber. It is subject to
B2.

### A3 · Regulators with movable setpoints `strong`
**Claim (D1 §3).** `dx/dt = -k(x - x*)` where `x*` itself moves — allostasis, not
homeostasis.
**Shape.** Every magic constant (concurrency, batch size, poll interval, retry budget)
becomes a regulated variable whose setpoint is data and can be renegotiated by context.
Setpoint changes are logged; that log is the allostatic history.

### A4 · Regimes, not states `strong`
**Claim (D1 §7).** Identity is an attractor repertoire — the set of transformations
survivable while remaining able to return to viable organization.
**Shape.** Each participant declares regimes (active / recovering / degraded / idle) and
legal transitions. Gives a precise perturbation-test spec: kick it, assert re-entry into
*some* viable regime within N steps — never "returns to prior state."

### A5 · Degeneracy, not redundancy `strong`
**Claim (D1 §8).** `x₁, x₂, x₃ ⟼ F`. Different structures, same function, different
circumstances.
**Shape.** N *different* implementations behind one contract, selected by circumstance
(fast path vs. robust path; model-driven vs. deterministic). The shared conformance suite
is the "function"; implementations are interchangeable "means." Explicitly **not**
replicas.

### A6 · Morphology as durable state `strong`
**Claim (D1 §5–6).** Present geometry restricts future trajectories; spatial organization
stores memory; higher-level organization constrains what replaces a component.
**Shape.** Persist the interaction graph itself — who talks to whom, edge weights,
reinforcement and decay, history — as first-class inspectable state. A joining or
replacement participant reads its role from surviving topology and local gradients rather
than static config. This is what makes hot-swap safe.

### A7 · Reconciliation, not rollback `strong`
**Claim (D1 §9).** `damaged organization → new viable organization`, not
`damaged → original`.
**Shape.** Repair loops compare current organization against declared invariants and move
toward viability. Divergence is recorded in an append-only **scar log** — never erased,
because the substitution is part of the history that constitutes identity.

### A8 · Lineage as the versioning invariant `strong`
**Claim (D1 §10).** The invariant is transformational continuity, not shape.
**Shape.** Contract versions connected by *declared, tested morphisms*. `v1 → v2` is an
artifact in the repo, not a migration note. Critically, lineage covers **projections**
too (B1): a participant that changes its internal compression changes what its reports
mean while the wire format stays stable. That is silent semantic drift and normal schema
versioning cannot see it.

### A9 · Autopoiesis as a CI check `core`
**Claim (D1 §2).** `organization → component production → organization`.
**Shape.** Derived artifacts (routing tables, client stubs, invariant tests) are generated
from declared contracts, and CI runs `regenerate && git diff --exit-code`. Anything
hand-written that could be derived is a place identity leaks.

---

## Group B — Observation and projection

### B1 · Observation envelope `core`
**Claim (D2).** `yᵢ = πᵢ(x; θᵢ) + εᵢ`. Without knowing `πᵢ` you cannot compare two reports
at all.
**Shape.** No participant ever emits a bare value.
```
Observation {
  value                     # yᵢ
  projection {id, version}  # πᵢ — what this view preserves and erases
  vantage θᵢ                # position, scale, instrument, time window,
                            #   categories, assumptions, priors
  window [t0, t1]
  uncertainty               # εᵢ model, not a scalar confidence
  upstream [obs_ids...]     # dependency lineage — feeds B4
}
```
**Cost control.** Register θ once in `projections/`; messages carry an id plus deltas.
Participants declare ontology, logic and default scale once and inherit. Eight mandatory
fields per claim is a wall nobody climbs.

### B2 · Blind-spot manifest `core`
**Claim (D2 §1).** Behind every observation is a fiber `πᵢ⁻¹(yᵢ)` of states it cannot
distinguish.
**Shape.** Each participant publishes, alongside its capabilities, what its projection
*erases*: which states does it collapse together? Even the crude form ("I distinguish A
from B; I am blind to C") is far more useful than a capability list, which only says what
a component *can* do. Enables ambiguity-set intersection and makes coverage gaps auditable
before they cost something.

### B3 · Equivalence at a stated scale `core`
**Claim (D1 §"equivalence class").** `[x] = {y | y ~ x}` — identity is scale-dependent.
**Shape.** Every equality check names its scale. Dedup keys, idempotency keys, caching and
tests all use declared projections. "Is the system still itself?" is asserted at the
ensemble projection, where byte-level difference is irrelevant. Kills a whole class of
retry/replay bugs.

### B4 · Independence ledger `core`
**Claim (D2 §"agreement can conceal blindness").** If `π₁ ≈ π₂ ≈ … ≈ πₙ`, consensus
reproduces one blind spot n times.
**Shape.** Track shared upstream — data source, model, retrieval, library, prompt,
assumptions — and compute an **effective observer count** `n_eff`, not a raw count. If all
n reports trace to one root, `n_eff = 1` and confidence does not grow no matter how many
agree.
**Why this ranks highest in practical risk.** Five agents on the same base model reading
the same document are *one observer sampled five times*. Every naive aggregator reports
high confidence. Start crude: distinct-source counting with hard discounts for shared
model and shared context. Crude beats the implicit `n_eff = n` everyone ships.

### B5 · Engineered cover `strong`
**Claim (D2 §"local views and global coherence").** Descriptions on `Uᵢ ∩ Uⱼ` must be
mutually transformable to glue.
**Shape.** Overlaps are a resource you *allocate*. Disjoint coverage means nothing can ever
be cross-checked; total overlap gives redundancy without reach. The cover is an explicit
topology decision stored in morphology (A6). Failure to glue is an **obstruction** —
published as a finding, not a crash. It means one of: an incorrect observation,
incompatible coordinates, a changing system, an overlooked boundary, or that no single
global description exists.
**Prior art.** Sheaf-theoretic sensor fusion (Robinson), including a computable
consistency radius. Start with pairwise overlap checks; formalize only if it earns it.

### B6 · Commutation test `deep`
**Claim (D2 §3).** `π ∘ F_t ≈ G_t ∘ π` is the condition for a higher level to have
autonomous dynamics.
**Shape.** Every abstraction is a projection with a claimed macro-dynamics — a status
summary, a dashboard metric, a health roll-up, a routing decision. Measure **leakage**:
evolve fine-grained then project, versus project then evolve coarse, and track divergence.
Growing error is an automatable signal that the abstraction is incomplete, and D2 supplies
the remedy menu. Requires a modeled `F`, which is why this is `deep` — but it is the best
single quality metric in the design.

### B7 · Generative-region detectors `strong`
**Claim (D2 §4, §7, §8; D5 §"where generative regions appear").** Discarded variables return
as memory, as noise, or as apparent crossings — and more generally, generativity appears
wherever the current representation repeatedly fails.
**Shape.** Nine detectors, catalogued in full in [`09-fields.md`](09-fields.md). The
originals:
- *Non-Markovian / hysteresis* — if adding history improves prediction of a macrostate, the
  state variable is missing a dimension.
- *Apparent-crossing* — if two observed trajectories converge then diverge, the observation
  space is under-dimensioned.
- *Threshold-legitimacy* — for every categorical field, test whether the boundary
  corresponds to actual dynamical separation (density gap, hysteresis) or is purely the
  observer's rule.

Added from D5: *seam* (= B5 obstruction), *hole*, *curvature* (= holonomy, Design B),
*bifurcation*, **frustration**, *degeneracy* (= A5), *singularity*, *boundary case*.
Frustration — a constraint set admitting no joint satisfaction — is first-class: publish
the trade-off surface, never "infeasible." Singularity returns *"the current distinction is
no longer adequate here"*, which is neither `unknown` nor `error`.

All of them convert "it's just noisy" into "there is structure in a dimension you are not
measuring."

### B8 · Categories carry their continuous coordinate `core`
**Claim (D2 §6).** Thresholding turns continuous variation into apparent types, and the
boundary may belong to the observer rather than the system.
**Shape.** `status: healthy|degraded|failed` and `priority: high|low` are thresholds *you*
chose. Keep the continuous coordinate beside the category. Most such boundaries are
imposed rather than dynamical — which is fine, provided it is known and marked.

### B9 · Aggregates carry their stratifiers `core`
**Claim (D2 §13).** Removing a stratifying variable can reverse an association.
**Shape.** No published aggregate without the stratification it was computed over.
Simpson's paradox is not exotic; roll-ups across participants reverse relationships
routinely.

### B10 · Correlations are first-class `strong`
**Claim (D2 §10–12).** A population is not its average individual; what survives the scale
transition is often the pattern of dependence, not the magnitude.
**Shape.** `⟨xᵢxⱼ⟩ ≠ ⟨xᵢ⟩⟨xⱼ⟩` is a published quantity, not something derived on demand.
Order parameters (collective alignment, synchronization, clustering) are declared
macrovariables subject to B6 and to D2 §14's six criteria — predictive, stable, observable,
causally meaningful, approximately closed, scale-appropriate.

---

## Group C — Combination

### C1 · Structured synthesis output `core`
**Claim (D2 §"better synthesis preserves disagreement").** Averaging destroys exactly the
information you need; the midpoint may correspond to no real state.
**Shape.** Synthesis emits a **field**, never a value and never a bucket list — see
[`09-fields.md`](09-fields.md), which corrects the earlier list form:
```
M = (P, D, R, C, T)      P positions (provenance intact) · D dimensions ·
                         R typed relations · C contexts · T transitions
```
Derived views over the field recover the original buckets — shared invariants,
perspective-specific features, conflicts, uncertainties, unobserved regions — plus
`foreclosed` (see `08-action.md` M3), the regions of possibility this collective has
permanently removed. Positions may be regions or distributions, never forced to points.
`M₁ … Mₘ` with an atlas; there is no single authoritative field.

### C2 · Plural, non-privileged synthesizers `core`
**Claim (D2 §"the collective observer becomes another projection").** `Σ: Y₁×…×Yₙ → Z` is
another projection with its own θ and blind spots.
**Shape.** Σ is a participant. It publishes its own manifest (B2), is versioned, and obeys
every rule above. Run **several** synthesizers with different weighting policies — their
disagreement is signal about the synthesis method itself. This is what structurally
prevents the orchestrator/God's-eye node, rather than relying on discipline.

### C3 · Probe loop `strong`
**Claim (D2 §"triangulation", D3 §12).** Disagreement tells you what to measure next.
**Shape.** A component reads current `M` and proposes the observation `π_{n+1}` that
maximally discriminates between live hypotheses. If models `M₁` and `M₂` predict different
values of `O*`, then `O*` is high-value.
**Why it matters.** Without this the architecture is passive and everything above is
elaborate bookkeeping. When *no* possible observation discriminates, that fact is itself a
finding: the disagreement is metaphysical, linguistic, or underdetermined.

### C3b · Action and probe are one category `core`
**Claim (D2 §16; run 001).** A probe is an action with near-zero foreclosure; an action is a
probe with consequences.
**Shape.** One type carrying `(collapse cost, information yield)`. Prefer, among actions of
comparable expected value, the highest yield per unit foreclosure. Under uncertainty prefer
the action that is also a probe — it is the only class that increases `M` while acting on
it. Full treatment in [`08-action.md`](08-action.md).

### C4b · Epistemic cost of irreversibility `strong`
**Claim (D6 §8; run 001).** The possibility space is itself state — `dX/dt = G(x, X)` — so
an irreversible action deletes regions of it.
**Shape.** `epistemic_cost(a) = measure of hypotheses rendered permanently untestable by a`,
published alongside expected value. Risk frameworks price expected loss; none price
destroyed falsifiability. First approximation: count the probes the action makes impossible.

### C5 · Collapse authority typed by foreclosure `core`
**Claim (run 001 §9; `07-participants.md`).** Foreclosure and consequence-bearing are
coupled, and only one kind of participant stands in the consequence-bearing relation.
**Shape.** Authority to collapse `M` into an action is indexed to the action's foreclosure
`E` and its consequence-bearer `W`, not to participant status. Probe-class actions: anyone.
Externally-borne or high-foreclosure actions: human authority. Total foreclosure: human
authority plus a published statement of what is being made permanently untestable.

### C4 · Yield scoring → cover redesign `strong`
**Claim (D2 §"toward a collective epistemic geometry").** The quality of collective
knowledge depends on the geometry of the observer network.
**Shape.** Score tension yields (D4 below). Track *per pair* which participants generate
high-yield tensions with each other — those are the epistemically complementary observers.
Feed that back into the cover (B5). The record of productive disagreement tells you how to
redesign the observer network; the system learns about the geometry of its own knowing.

---

## Group D — Tension

### D1t · Contradiction is derived, never primitive `core`
**Claim (D3 §2).** Two claims differing is not two claims conflicting. Opposition must be
demonstrated.
**Shape.** There is **no `contradiction` type a participant can write.** Every pair starts
`unclassified`. `contradiction` is the most expensive status to reach, requiring discharge
of alignment obligations: same referent, same sense, same time, same scale, same context,
same modality, and a logic in which they actually negate. Each alignment check is itself a
claim with provenance, and is challengeable.
**Failure mode, deliberately chosen.** When the classifier errs, the system under-detects
opposition and sits inert rather than manufacturing conflict and acting on it. Erring
toward "not yet comparable" is far cheaper than erring toward "these participants
disagree." See `06-open-decisions.md` for the paralysis guards this requires.

### D2t · Dichotomy audit `core`
**Claim (D3 §10 = D2 §4, see unification 2).** Apparent exhaustive opposites indicate a
collapsed dimension.
**Shape.** Mechanical procedure for any asserted opposition:
1. Auto-generate the 2×2: `A∧B`, `A∧¬B`, `¬A∧B`, `¬A∧¬B`.
2. Search the claim store for occupants of `A∧B` and `¬A∧¬B`.
3. If either is occupied → downgrade immediately to *distinct, not opposed*.
4. If both empty, that is not proof — emit a probe asking participants to construct an
   instance.
5. Only if probes return empty **and** alignment conditions hold does it remain a
   contradiction.
**The yield.** When `A∧B` is occupied, ask what distinguishes the cases landing there.
That recovered variable is the collapsed dimension.

### D3t · Tension typing `core`
**Claim (D3 §1, D2 §"four kinds of disagreement").** Different ruptures need different
responses; collapsing them into `conflict → vote` destroys the information.

| Type | Response |
|---|---|
| Measurement | replicate, recalibrate — this one *is* noise |
| Perspectival | integrate; both true of different aspects. Do not pick a winner |
| Scale | both valid at their scale; qualify and escalate to a cross-scale model |
| Model / framework | park as open contradiction; never auto-resolve |
| Indexical (time, context) | re-index rather than contradict |
| Equivocation | split the term into explicit senses |
| Ontological mismatch | build a bridge (D8t); do not merge |
| Self-reference | separate object and meta levels (D7t) |

**Start with three, not eight.** `not-yet-comparable` / `different-projection` /
`genuine-opposition`, splitting only when real traffic demands it.

### D4t · Yield gate `core`
**Claim (D3 §11 "Generate").** Tension must produce at least one constructive output.
**Shape.** A **hard, mechanically enforced gate**: a tension cannot leave the active set
until it emits an artifact — a new distinction, a recovered variable, an ontology bridge,
a probe, a counterexample, a boundary condition, or a meta-question. `closed` requires a
non-empty `yield` field.
**Why this is load-bearing.** It is the disposal mechanism that makes "preserve all
disagreement" survivable. Tensions are not resolved and not deleted — they are
*metabolized*. The residue is archived with a pointer to what it produced. Without this
gate, the tension store becomes a graveyard nobody reads.

### D5t · Decision ≠ closure `core`
**Claim (D3 §11 "preserve the residue").** Resolution for action does not imply resolution
in truth.
**Shape.** Two separate fields, never merged:
```
operational_decision { choice, rationale, reopening_trigger }
epistemic_status     { unresolved, residue, open_questions }
```
The `reopening_trigger` is the observation that would reopen it — the probe loop (C3)
pointed at past decisions. Conflating these is how organizations forget why they chose
things.

### D6t · Verdict as universal return type `core`
**Claim (D3 §7).** No general procedure decides every instance; bounded methods with
published bounds are the correct response.
**Shape.** Nothing returns a bare boolean:
```
Verdict { status, method, resource_bound, termination_condition, guarantee }
```
Including the contradiction classifier itself. *"No contradiction found at depth 50 under
classifier v3"* is a different object from *"no contradiction exists,"* and a system that
cannot express the difference will confidently assert the second.
**The asymmetry to keep loud.** "No general algorithm exists" ≠ "this instance is
intractable." Most concrete instances are decidable; what is lost is the uniform
guarantee. Default posture: bounded attempt plus published bound.

### D7t · Theory stamps and the extension ledger `strong`
**Claim (D3 §6).** Unresolvability is relative to a stated theory `T = (A, R, L)`, and
`T⁺` acquires its own limits.
**Shape.** Every derived claim is stamped with the theory it was derived in. Never
"unknowable" — always "not derivable or refutable within `T`." Extensions `T ↪ T⁺` are
logged with both the added assumption `A*` **and** the new vulnerability `V*`, because
extending `T` can import new undecidables or new inconsistency.
**Addition: assumption footprint as a ranking signal.** `T₁ ⊂ T₂ ⊂ T₃` means a claim
derivable in a weaker theory is more robust. The *minimal T in which a claim is derivable*
gives a principled preference ordering that is not vote-counting — which matters
enormously given B4.

### D8t · Assumption graph / switchboard `strong`
**Claim (D3 §9).** Contradiction is a visible structure of pathways, not a red mark.
Locate the minimal inconsistent set `I ⊆ A`.
**Shape.** Assumptions are nodes supporting conclusions. The system extracts minimal
inconsistent subsets and offers a switchboard: retain `A₁` → `P`; remove `A₁` →
undetermined; replace with `A₁'` → `¬P`; contextualize → `P` in `C₁`, `¬P` in `C₂`. Turns
argument into exploration of a possibility space.
**Prior art — this is solved engineering.** An ATMS (de Kleer, assumption-based truth
maintenance) gives exactly this: labels tracking which assumption sets support each node,
nogoods as minimal inconsistent sets, instant retraction queries. MUS extraction is
standard in SMT tooling.

### D9t · Paraconsistent store, classical working set `strong`
**Claim (D3 §4).** `P, ¬P ⊢ Q` must not hold system-wide.
**Shape.** Belnap four-valued evidence `v(P) = (e⁺, e⁻)` giving supported / opposed / both
/ neither, so one contradiction cannot trivialize the store.
**Two extensions the bare form needs:**
1. `e⁺` and `e⁻` carry their **dependency graphs**, not counts. Fifty supporters sharing
   one upstream source against one independent opponent must not look like a balanced
   split. B4's discounting applies to both poles.
2. **Two-tier storage.** Paraconsistency costs disjunctive syllogism and a surprising
   amount of ordinary inference goes with it. Keep a classical *working set* of
   consistency-checked claims for fast everyday reasoning over a paraconsistent full store
   that never explodes.

### D10t · Independent status axes `strong`
**Claim (D3 §5).** Flattening all uncertainty into "unknown" destroys information.
**Shape.** Four orthogonal axes on every proposition:
- **Evidential** — supported / opposed / both / neither
- **Proof, relative to `T`** — provable / refutable / independent / undetermined
- **Computational, relative to `M`** — computable / semidecidable / undecidable /
  complexity-limited / unknown
- **Ontological compatibility** — shared / translatable / partially translatable /
  category mismatch / unmapped

A claim can be empirically well-supported and formally unprovable; a question can have a
definite answer and no general algorithm to find it. These are different conditions.

### D11t · Ontology bridges with named loss `strong`
**Claim (D3 §8).** `F: O₁ → O₂` with `Loss(F) ≠ 0`. Do not force synthesis; sometimes two
ontologies preserve genuinely different distinctions.
**Shape.** Bridges live in the *same* registry as projection translation maps (unification
1 — a bridge is a restriction map that fails to be an isomorphism on an overlap, so B5's
obstruction machinery already covers it). `Loss(F)` must be **named**, not merely nonzero:
*which distinctions does this translation destroy?*

### D12t · Certificates `strong`
**Claim (D3 §7).** Certificates are checkable even when hard to discover.
**Shape.** Participants propose; others verify cheaply and independently. This asymmetry
is how a multi-participant system gets warranted trust *without* a central authority and
without accepting anything on reputation. Especially important where B4 makes
agreement-counting untrustworthy.

### D13t · Level marking and justification-cycle detection `deep`
**Claim (D3 §13).** Reflexivity is required but must not be infinite regress.
**Shape.** Mark levels `L₀` system under study, `L₁` observations, `L₂` relations among
observations, `L₃` synthesis rules. Strict stratification is too rigid in practice, so
instead: run **cycle detection on the justification graph**. A cycle is not fatal; a cycle
touching a meta-level rule with *no external support* is a self-justifying loop and gets
flagged and displayed. Reflexivity gets a resource budget, so regress terminates by
declaration rather than exhaustion — the same discipline as D6t.

---

## The spine

If only eight mechanisms are ever built, build these. They are all cheap and each one
prevents a failure that is expensive to reverse later:

| | Mechanism | Prevents |
|---|---|---|
| 1 | **B1** Observation envelope | uninterpretable claims; semantic drift |
| 2 | **B2** Blind-spot manifest | invisible coverage gaps |
| 3 | **B4** Independence ledger | false confidence from correlated observers |
| 4 | **D1t** Contradiction as derived | manufactured conflict |
| 5 | **D6t** Verdict return type | overclaiming beyond budget |
| 6 | **D4t** Yield gate | the tension graveyard |
| 7 | **D5t** Decision ≠ closure | lost rationale, unreviewable choices |
| 8 | **C1** Structured `M` | averaging away the signal |
