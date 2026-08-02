# Design C — Federated (Shared Referent as an Earned Property)

> **Premise.** Some things have a shared referent; some do not. **Which is which is itself
> contested, discovered, and revisable** — not declared at design time.

The weak version of C is "run A and B side by side." That is two systems in a trench coat,
with double the machinery and no principle for choosing between them.

The strong version rests on one observation:

> **Design A is a special case of Design B.** A shared referent is a bridge that happens to
> be lossless and shared among a group.

So the architecture is **B-shaped**, and A-mode is a capability that switches on locally,
where it has been *earned*.

---

## Shared referent as a certificate, not an assumption

A set of participants earns **shared-referent status** over a *region* of the domain when
all of the following hold, with evidence:

| Condition | Evidence |
|---|---|
| Common ontology fragment | an agreed `H` restricted to that region exists and is versioned |
| Bounded translation loss | `Loss(F)` into and out of `H` is below threshold for those participants |
| Trivial holonomy | translation cycles within the region close within tolerance |
| Rare, resolvable contradiction | empty-intersection events are infrequent and attributable |
| Modelable observers | `θᵢ` and `εᵢ` are known well enough to interpret reports |

When the certificate holds, **switch on A-mode inside that region**: intersect ambiguity
sets, run Bayesian fusion with `n_eff` discounting, compute EIG probes, run commutation
tests, calibrate participants against outcomes.

When it fails, **fall back to B-mode**: keep perspectives separate, work on bridges, do not
intersect anything.

Mode is a property of a **(participant group × domain region)** pair, never global. Three
participants may share a referent about latency and share nothing about severity.

## The map of modes is the system's model of its own objectivity

This is the part that makes C worth the extra machinery, and it is not available in either
pure design.

- Regions in **A-mode** are where a fact of the matter exists *and is accessible to this
  collective*.
- Regions in **B-mode** are where it does not, or is not yet.
- The boundary between them **moves**, and its movement is recorded.

That recorded movement is D1's developmental story applied to the system's own knowing:
identity preserved by transformation, with the trajectory as the invariant. The system does
not just model its domain — it maintains an explicit, revisable account of *where it has
earned the right to speak with one voice*.

## Promotion and demotion are logged events

**Promotion** (B → A) requires the certificate to hold over a window, not an instant.

**Demotion** (A → B) triggers on: empty intersection that cannot be attributed to an
observation or observer model; holonomy drift; `Loss(F)` growth; commutation leakage
(B6) climbing.

Demotion is the more informative event. It means: *we believed we were talking about the
same thing, and we were not.* That belongs in the tension store with a mandatory yield
(D4t), because the recovered variable — the thing that turned out not to be shared — is
usually the most valuable output the system produces.

## Guard against premature promotion

A-mode gives crisp answers, so the pull toward it is strong and mostly not epistemic. Three
guards:

1. **Certificates expire.** Shared-referent status has a TTL and must be re-earned.
2. **Randomized demotion drills.** Periodically re-run a certified region in B-mode and
   check that the shared referent still reproduces. This is chaos engineering pointed at
   ontology rather than infrastructure, and it is the cheapest way to catch a shared
   referent that quietly stopped being shared.
3. **Promotion requires the certificate, never convenience.** No manual override that
   bypasses evidence; if a region needs A-mode to ship something, that pressure is recorded
   as an operational decision (D5t) with its own reopening trigger, not as an epistemic
   claim.

## The A/B boundary is the highest-yield location in the system

D3 names this directly: the most productive disagreements occur where two models each work
well but fail to connect. In Design C that boundary is not a figure of speech — it is a
queryable data structure. Regions adjacent to a mode boundary are where probes (C3) should
be aimed first, and where new bridges pay the most.

---

## Repo shape

```
perspectives/<name>/        # B is the base case: every participant owns its ontology
  ontology/ logic/ membrane/ claims/ viability/ regimes/ core/
bridges/                    # translations, Loss(F), counterexamples, holonomy
  pivots/  composition/
regions/                    # the domain partition — the heart of Design C
  <region>/
    mode                    # translate | shared
    certificate/            # evidence, thresholds, TTL, participant group
    referent/               # H_region — exists ONLY in shared-mode regions
    history/                # promotion and demotion events, with yields
    drills/                 # randomized demotion results
fusion/
  transport/                # B-mode engine — always available, the default
  intersect/                # A-mode engine — runs only inside certified regions
tensions/                   # one store; classification priors differ by mode
  boundary/                 # tensions at mode edges — highest priority for probes
ledger/ probes/ yields/ verdicts/ theories/ levels/
substrate/ contracts/ invariants/ observatory/
```

Note `fusion/transport/` is the default path and `fusion/intersect/` is the exception. Build
them asymmetrically — B's substrate is the general case and must exist first; A-mode is a
plugin that activates on certified regions. Building both engines symmetrically is how C
becomes twice the work for no additional insight.

---

## What C costs

Strictly more machinery than either pure design: both fusion paths, plus the certificate,
mode-negotiation, promotion/demotion, and drill infrastructure. Roughly B's cost plus 40%,
not A + B.

The mitigation is sequencing, not scope reduction:

1. Build **B's substrate only.** Perspectives, bridges, tensions, yields, ledger. Everything
   works, nothing is certified, `regions/` all sit in `translate` mode.
2. Add the **certificate evaluator** as a read-only reporter. It observes and says *"this
   region would qualify for A-mode."* Nothing acts on it. This alone is valuable — it tells
   you where shared understanding actually exists rather than where you assumed it did.
3. Add **A-mode fusion** for the first region that has been reporting eligible for a while.
4. Add **drills and demotion** before adding a second region, not after. The failure path
   must exist before you depend on the success path.

---

## Choose C when

- Participants are heterogeneous but overlap on *some* subject matter — the realistic case
  for most multi-participant systems.
- You do not know in advance where shared understanding exists, and you would rather
  discover it than legislate it.
- Being wrong about *whether* there is a shared referent is itself a costly error worth
  detecting.

Typical fits: mixed human and automated participants; a system spanning several domains
where some are instrumented and others are interpretive; anything long-lived enough that
the boundary of shared understanding will move during its lifetime.
