# 09 — Fields: Beyond the Multitude

Integrates two further source documents:

| Ref | Source | Contributes |
|-----|--------|-------------|
| **D5** | *Binary → structured field* | the field form, the generative-region catalog |
| **D6** | *Beyond multitudes* | the escalation ladder, generated dimensions, mutual constitution |

D5 delivers a direct correction to this design, so that first.

---

## The correction: `M` was a multitude

C1 specified:

```
M = { shared_invariants, perspective_specific, conflicts, uncertainties, unobserved }
```

That is a **list of buckets** — a multitude, not a field. It records *what positions exist*
and nothing about how they relate. D5 is right that replacing "either/or" with "A, B, C, D"
is still a compression, just a wider one.

**Upgrade `M` to a field:**

```
M = (P, D, R, C, T)
      P   positions — observations, claims, tensions (provenance intact)
      D   dimensions — the coordinates along which positions differ
      R   relations among positions
      C   contexts in which each holds
      T   transitions — how positions become one another
```

The bucket list survives as *derived views* over the field, not as the storage form.

### Relations `R` are typed, and most of them are not disagreement

The design had a rich vocabulary for conflict (D3t's eight types) and almost none for
everything else. D5 supplies it:

`supports` · `contradicts` · `complements` · `contains` · `depends-on` ·
`transforms-into` · `holds-at-another-scale` · `same-outcome-different-mechanism` ·
`not-yet-translatable`

Two are worth calling out. **`same-outcome-different-mechanism`** is degeneracy (A5) seen
in claim space rather than implementation space. **`not-yet-translatable`** is the honest
default that D1t's inversion demands — the relation that most pairs actually stand in.

### Positions are regions, not points

A participant's view is rarely one coordinate. It may be a region `pᵢ ⊆ M` or a
distribution `μᵢ(x)` — confident on one axis and not another, context-dependent, internally
divided, or changing.

This generalizes something Design A already required (emit constraints, not point
estimates) to **all three designs**: B1's `value` field admits a region or distribution
everywhere, not only where there is a shared referent. Forcing a participant to a point to
make the display tractable is a projection nobody declared.

### The field must remain plural

After rejecting a binary, the failure mode is building one authoritative multidimensional
framework and forcing everything into it — a more sophisticated compression wearing the
costume of pluralism.

So: `M₁, M₂, …, Mₘ` with an atlas, not one final field. Several coordinate systems, local
rather than universal metrics, contested dimensions, participants who reject the framing,
untranslated observations, and revision of the field's own structure. This is C2 (plural
synthesizers) extended from the synthesizer to the *representation itself*.

---

## The generative-region catalog

B7 had three detectors. D5 supplies nine. Notably, three of them the design had already
arrived at under other names — weak evidence the catalog is picking out something real:

| Region | Signature | Status here |
|---|---|---|
| **Seam** | two perspectives overlap and disagree | B5 gluing obstruction |
| **Hole** | a combination of perspectives has no connecting account | **new** — missing observer, scale, or mechanism |
| **Curvature** | translation is path-dependent: `A→B→C ≠ A→D→C` | already present as **holonomy** (Design B) |
| **Bifurcation** | small condition change → qualitatively different outcome | **new** — exposes hidden control variables |
| **Frustration** | several constraints cannot all be satisfied | **new**, and important |
| **Degeneracy** | different processes, same visible result | already present as A5 |
| **Hysteresis** | same present state, different futures | already present as B7's non-Markovian detector |
| **Singularity** | the coordinate system stops working | **new** — must report *"the current distinction is no longer adequate here"*, never an error |
| **Boundary case** | recurrent ambiguity at a category edge | **new** — shows how the category was constructed, not noise around it |

**Frustration deserves first-class status.** A set of mutually unsatisfiable constraints —
stable *and* adaptable *and* cheap *and* accurate — is not a failure to be resolved. It is
the geometry of a trade-off, and it is one of the few structures that tells you something
true about the whole system rather than about one position in it. The system should detect
constraint sets that admit no joint satisfaction and publish the trade-off surface rather
than reporting infeasibility.

**Singularity handling is a real discipline.** D6t's `Verdict` type already forbids bare
booleans; the singularity case extends it — when a coordinate system breaks down, the
honest return is that the distinction has stopped applying, which is different from
`unknown` and different from `error`.

---

## The escalation ladder, and where this design actually sits

D6's progression:

```
binary            A or B
multitude         {A, B, C, …}
structured field  positions + relations + dimensions
dynamic field     positions and relations changing over time
generative field  new positions, relations, and dimensions emerge
reflexive field   the field models and modifies its own organization
open becoming     no fixed inventory of future possibilities
```

An honest placement of the current design:

| Rung | Where the design reaches it |
|---|---|
| structured field | **yes** — `M` as `(P,D,R,C,T)`, this file |
| dynamic field | **partly** — A6 morphology, A4 regimes, A8 lineage, epoch markers (M6) |
| generative field | **narrowly** — only the extension ledgers: `H ↪ H⁺`, `T ↪ T⁺`, and D4t's yield gate, which is the thing that *drives* dimension generation |
| reflexive field | **partly** — C2 plural synthesizers, C4 yield-scoring feeding back into the cover, D13t level marking |
| open becoming | **no** — not represented |

Two observations from that table.

**The yield gate is the dimension-generating engine.** D6 §4 says a field must be able to
transform `Fₙ → Fₙ₊₁` where the new field has a coordinate absent from the old, and that
persistent contradiction is one mechanism of dimensional generation. That is precisely what
D4t enforces: a tension cannot be filed until it emits a distinction, variable, or bridge.
The design had the engine and had not noticed what it was for.

**"Open becoming" is not a build target.** It is a constraint on claims: the design must
not assert that its inventory of possible future forms is complete. Mechanically that
reduces to `Mₜ → Mₜ₊₁` with no terminal state and no completeness claim anywhere in the
system — which D6 §12 states directly. Completeness is replaced by revisability, and that
is implementable; "open becoming" as a feature is not.

---

## Two consequences that change earlier files

### The possibility space is itself state

D6 §8: `dx/dt = F(x, X)` **and** `dX/dt = G(x, X)`. The system moves within a possibility
space while transforming that space.

Two systems identical now may differ entirely in reachable futures — a stem cell and a
differentiated cell; an ecosystem that looks stable but has lost recovery capacity. So a
participant's state must include actuality *and* accessible repertoire:

```
state = what is actual + what is accessible + what is becoming accessible
```

This is what makes M4 (epistemic cost of irreversibility) coherent rather than decorative:
foreclosure is a measurable change in `X`, not a vague loss of optionality.

### Mutual constitution breaks a background assumption

D6 §11 is the sharpest challenge to the earlier designs. `yᵢ = πᵢ(x, oᵢ)` — observation
participates in the dynamics rather than reading them off. Combined with the answer that
the collective *acts*, the consequence is recorded in `08-action.md` M6: Design A's
intersection semantics hold **between** actions, not across them, and every A-mode region
needs an epoch marker.

This is a genuine limitation on the strongest of the three designs, and it was invisible
until the "does it act?" question was answered.

---

## Individuation: participants are not necessarily pre-given

D6 §9 — before a tissue differentiates, its future cell types exist as tensions, gradients
and capacities rather than as separate entities.

The design already has the mechanism: A6 says a joining participant reads its role from
surviving topology and local gradients rather than static config. D6 supplies the framing
and the questions the system should be able to answer about any participant:

- How did this boundary form?
- What maintains it?
- Could it dissolve?
- **Which alternatives were suppressed?**
- What new participants could emerge from the current field?

The fourth is the one with teeth, and it is the participant-level version of M4: the
history of an individuation records what did *not* differentiate, which is exactly the kind
of foreclosure no roster ever shows.
