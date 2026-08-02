# 05 — Comparison

## Side by side

| | **A — Shared referent** | **B — Translation** | **C — Federated** |
|---|---|---|---|
| **Premise** | one `X`, many `πᵢ` | no common `X` | shared `X` is local and earned |
| **Fusion means** | intersect ambiguity sets | transport claims along bridges | intersect where certified, transport elsewhere |
| **Core artifact** | `H`, the hypothesis space | bridges with named `Loss(F)` | `regions/` and their mode certificates |
| **Primary contribution** | an observation | a translation | a promotion or demotion event |
| **Can a participant be wrong?** | yes — against `X` | only on its own terms, or by holonomy | depends on region mode |
| **Agreement means** | genuine evidence (if `n_eff` > 1) | weak; may be an artifact of lossy translation | mode-dependent |
| **Disagreement means** | measurement error or hidden dimension | ontological structure; the normal condition | at a mode boundary: highest-value signal |
| **Convergence alarm** | `⋂ πᵢ⁻¹(yᵢ) = ∅` → `H` too small | non-trivial holonomy around cycles | either, plus demotion |
| **Probe asks** | which observation discriminates hypotheses | what would break or improve this bridge | both, prioritized at mode edges |
| **Calibration** | yes, against outcomes | impossible — no ground truth | only inside A-mode regions |
| **B6 commutation test** | available | not meaningful | available inside A-mode regions |
| **Dominant tension type** | measurement, perspectival | ontological, model/framework | boundary tensions |
| **Main failure mode** | `H` becomes the collective blind spot | relativism drift; no convergence | premature promotion |
| **Entry cost** | ontological agreement up front | bridge combinatorics | B's cost + ~40% |
| **Right when** | there is a fact of the matter | there isn't, or it isn't the point | you don't know yet, and want to find out |

---

## One worked example through all three

**Scenario.** Five participants weigh in on: *is this change safe to deploy?*

| Participant | Projection `πᵢ` | Sees | Blind to |
|---|---|---|---|
| Static analyzer | code structure → defect classes | type errors, unsafe patterns | runtime behaviour, user impact |
| Test runner | execution → pass/fail | specified behaviour | unspecified behaviour |
| Profiler | execution → latency, memory | resource regressions | correctness |
| On-call engineer | incident history → risk judgment | operational fragility, past pain | code detail |
| User feedback stream | reports → sentiment, complaint volume | experienced impact | causation |

### Under Design A

Requires stating `H`: the space of possible "true states" of this change — e.g. a joint
space over `{correctness defects, latency regression, operational risk, user-visible
impact}`. Each participant contributes a likelihood over that space. Analyzer, tests and
profiler map cleanly. The on-call engineer and the feedback stream are the strain point:
their `θᵢ` is hard to model and their `εᵢ` is not stationary.

- **Fusion:** posterior over `H`, with `n_eff` discounting — note analyzer and tests likely
  share upstream (same source tree, possibly same fixtures), so they are *not* independent.
- **Alarm:** tests pass, profiler is clean, and on-call says "this touches the thing that
  broke twice." If no state in `H` explains all reports, `H` is missing a dimension —
  plausibly *operational blast radius*, which none of the first three instruments measure.
- **Probe:** the observation that best discriminates — likely a canary at 1% traffic.
- **Outcome:** a distribution over safety, plus a named missing dimension.

### Under Design B

No `H`. Five perspectives, each internally coherent, in different ontologies: *defect
class*, *specification conformance*, *resource envelope*, *operational risk*, *experienced
harm*. These are not the same kind of thing, and forcing them into one space is the
category error Design B refuses to make.

- **Bridges:** conformance → risk; resource envelope → experienced harm. Both lossy, and
  the loss is nameable: "tests passing" does not preserve *unspecified* behaviour, which is
  exactly where operational risk lives.
- **Holonomy check:** translate "safe" from tests → risk → harm → back to tests. If it does
  not close, the discrepancy is located on a specific edge.
- **Agreement guard:** analyzer and tests both say "safe." Re-check at the finest common
  refinement — do they agree about the *same* property, or does the bridge between them
  collapse "no unsafe patterns" and "no failing assertions" into one word?
- **Outcome:** not a verdict. A structured `M`: what all five preserve, where each is
  blind, which conflicts are ontological versus measurement, and what remains unobserved.

### Under Design C

The realistic reading. Analyzer, tests and profiler have plausibly earned a shared referent
over the region *"mechanical properties of this change"* — common ontology, bounded loss,
closing cycles. That region runs in **A-mode**: intersect, fuse, probe by information gain.

On-call judgment and user feedback stay in **B-mode**. There is no agreed `H` covering
"operational risk" and "experienced harm," and pretending otherwise would quietly convert
a human's contextual judgment into a mismodeled instrument.

- **The mode boundary is where the action is.** The tension between "mechanically clean" and
  "this feels dangerous" is a boundary tension — highest priority for probes, and the
  likeliest source of a recovered variable.
- **Demotion in practice:** ship it, it breaks, and post-incident it turns out the profiler
  and the test runner were measuring under a load profile that stopped being
  representative. That region loses its certificate. The demotion event carries a mandatory
  yield: the recovered variable is *load-profile representativeness*, which becomes a new
  observed dimension.
- **Outcome:** a fused estimate where fusion is warranted, preserved plurality where it is
  not, and an explicit record of which is which — that last part being the thing neither
  pure design produces.

---

## Recommendation

**Design C, built in B's shape, sequenced as described in `04`.**

Three reasons:

1. **B is the general case and A is a special case of it.** Building B first costs nothing
   extra even if you later discover everything is shared — you would have needed the
   bridges, ontologies and tension machinery regardless. Building A first and discovering
   participants do *not* share a referent is a rewrite, because `H` will have been baked
   into every message.

2. **Step 2 of the C sequence is valuable on its own.** A certificate evaluator that only
   *reports* which regions would qualify for A-mode answers your original question —
   *is there a shared X?* — empirically rather than by assumption. You may find shared
   referents where you expected incommensurability, or the reverse. Either way you learn
   it from traffic instead of guessing at design time.

3. **The A/B boundary is where the design pays off.** Both pure designs answer questions.
   Only C tells you where the collective has earned the right to speak with one voice, and
   watches that boundary move.

The honest caveat: if it turns out there genuinely *is* one clean shared referent and all
participants are instrumentable, Design A alone is meaningfully simpler and its
mathematics are sharper. C's extra machinery buys the ability to be *wrong about whether
there is a shared referent* and find out. Whether that is worth 40% is a judgment about how
confident you are — and given three documents' worth of argument that projection hides
exactly this kind of thing, low confidence seems like the calibrated position.
