# Design A — Shared Referent (Intersecting Ambiguity Sets)

> **Premise.** There is a common underlying `X`. Every participant observes it through a
> different `πᵢ`. There is a fact of the matter, even if no participant can reach it.

Fusion is **intersection**: `x ∈ ⋂ᵢ πᵢ⁻¹(yᵢ)`. Combining views *narrows* the space of
possibilities. This is the strong case in D2, and the one where the mathematics is
cleanest.

---

## What makes A work

Ambiguity sets are only intersectable if they are subsets of the *same* space. So Design A
has one non-negotiable, expensive commitment the other designs do not:

**The hypothesis space `H` must be explicitly represented, shared, and versioned.**

`H` is the collective's model of what states `X` could be in. It may be an enumerated
hypothesis set, a parameterized model, a factor graph, or a probabilistic program — but it
must exist as an artifact, not as an assumption living in participants' heads.

Everything else follows from that.

### Participants emit constraints, not values

An observation is a **restriction on `H`** — a hard constraint set, or a likelihood
`p(yᵢ | x, θᵢ)`. This is B1 with the value field given a specific meaning: not "here is
what I saw" but "here is what I have ruled out."

### Blind-spot manifests become computable

Because `H` is explicit, B2 stops being prose. A participant's blind spot is precisely
*which distinctions in `H` its projection collapses*, and can be checked mechanically. You
can ask "is any participant sensitive to dimension D?" and get a real answer, and you can
compute the residual ambiguity of the whole collective before running anything.

### Fusion is intersection, then Bayesian update

```
posterior(x) ∝ prior(x) · ∏ᵢ p(yᵢ | x, θᵢ)     [conditional independence]
```

The product form is only valid under independence, which is exactly what B4 exists to
police. Shared sources, shared models, shared retrieval and shared priors collapse the
product. **In Design A the independence ledger is not a nicety — it is the difference
between the math working and the math lying.**

### Empty intersection is the most valuable event in the system

```
⋂ᵢ πᵢ⁻¹(yᵢ) = ∅
```

means one of exactly three things:

1. an observation is wrong,
2. an observer model `θᵢ` or `εᵢ` is wrong,
3. **`H` itself is missing a dimension.**

The third is the Design A analogue of a Gödel boundary: the hypothesis space is too small
to contain the truth. It gets an **`H`-extension ledger** structurally identical to D7t's
`T ↪ T⁺` — record the added dimension `A*` and the new vulnerability `V*`, because
expanding `H` can make previously discriminating observations non-discriminating.

Empty intersection is the trigger that keeps `H` honest. Without it, `H` silently becomes
the shared blind spot of everyone.

### Probes are well-defined

C3 becomes classical optimal experimental design: choose the next observation maximizing
expected information gain over `H`. This is the sharpest form of the probe loop available
in any of the three designs, and it is a genuine reason to prefer A when it applies.

### Calibration is possible

Ground truth exists, so participants can be scored against outcomes over time — sharpening
`εᵢ`, detecting drift in `πᵢ`, and giving a *non-vote-based* reliability signal. Neither B
nor unpromoted regions of C can do this.

### Commutation tests are meaningful

B6 requires a modeled fine-grained dynamics `F`. If `H` includes dynamics, leakage becomes
measurable for every declared macrovariable — the strongest quality metric in the catalog,
available only here.

---

## Repo shape

```
referent/
  space/              # H — the shared hypothesis space, versioned
  dynamics/           # F, if modeled — enables B6 commutation tests
  extension-ledger/   # H ↪ H⁺, with A* and V*, driven by empty-intersection events
projections/          # πᵢ, θᵢ, εᵢ, blind-spot manifests expressed as collapses in H
participants/<name>/
  membrane/           # == πᵢ  (unification 1)
  viability/ regimes/ regulators/ core/ variants/
fusion/
  intersect/          # constraint intersection
  update/             # Bayesian combination, discounted by n_eff
  empty-detector/     # the H-insufficiency alarm
ledger/               # dependency graph, effective observer count
probes/               # expected information gain over H
tensions/             # typed, but with A-mode priors (see below)
substrate/  contracts/  invariants/  verdicts/  observatory/
```

## What gets lighter in A

The tension taxonomy is **less** exercised here. Committing to a shared `H` means
participants have already agreed on an ontology fragment, so ontological mismatch and
model-framework disagreement are rare by construction. Most tensions are measurement
disagreement, which is genuinely resolvable by better observation, and perspectival
disagreement, which resolves into different fibers over the same `H`.

D1t's inversion still applies — opposition must be demonstrated — but the alignment
obligations are usually cheap to discharge, because a shared `H` already fixes referent,
sense and scale.

---

## Failure modes

**`H` is a projection too, and it is everyone's blind spot at once.** Anything outside `H`
is invisible to the entire collective, and the intersection machinery will happily converge
confidently on the wrong region. The empty-intersection detector is the only structural
defence, so it must be loud and it must never be tuned into silence.

**Ontological agreement is the entry fee, and it is often the thing you cannot get.**
Stating `H` requires participants to agree on what kinds of things exist before they can
contribute anything at all. Where that agreement is unavailable, Design A cannot start —
which is precisely the situation Design B exists for.

**Opaque participants break the likelihood.** Interpreting a report requires `θᵢ` and
`εᵢ`. A black-box model, a human expert, or a third-party service may not expose enough to
model, and hand-waving the likelihood silently corrupts the posterior.

**Correlated observers destroy the math quietly.** Worth stating twice. The product form
is seductive and wrong the moment B4 is skipped.

---

## Choose A when

- There is a real system being observed and a fact of the matter about its state.
- Participants can agree on an ontology sufficient to state `H`.
- Observers are modelable — you know roughly what each measures and how it errs.
- The goal is **convergence**: reduce uncertainty about something.

Typical fits: sensor and telemetry fusion; multiple analyses of one codebase, dataset, or
incident; several agents investigating one bug; diagnostic settings where the answer
exists and is merely hidden.
