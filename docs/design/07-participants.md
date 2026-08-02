# 07 — Participants: Human and AI

**Answered:** participants are human and AI. **The distinction between systems must not be
collapsed.**

This file records what that constraint means mechanically, because "treat them as
different" is not yet a design.

---

## The failure it forbids

The tempting move is to model every participant uniformly as an instrument:
`yᵢ = πᵢ(x; θᵢ) + εᵢ`, fit `θᵢ` and `εᵢ` from history, weight accordingly. It is tidy, and
it is a category error in **both** directions:

- **Modelling a human as an instrument** converts judgment into measurement. A human's
  report carries context, stake, and standing that no `εᵢ` represents. Calibrating them
  against outcomes and down-weighting them is not observer modelling — it is deciding, by
  default, that judgment is unreliable measurement rather than a different kind of thing.
- **Modelling an AI as a person** imports standing it does not have and hides the
  correlation structure that makes it dangerous in aggregate (B4). Five AI participants
  are not five colleagues.

The non-collapse rule is therefore not politeness. It is the claim that **human and AI
participants sit in different ontologies (D11t)**, and the correct response to an
ontological difference is a bridge with named loss — never a merge.

## The asymmetries that actually bite

| | Human | AI |
|---|---|---|
| **Vantage `θ` transparency** | internally opaque, but can *report* vantage, be asked why, and revise for reasons | partly inspectable from outside (model, prompt, context, retrieval); self-report is unreliable |
| **Correlation structure (B4)** | institutional, cultural, professional — slow, legible, partially declarable | architectural — fast, invisible, near-duplicate by default |
| **`n_eff` default** | tends toward the headcount | tends toward **1** until proven otherwise |
| **Consequence-bearing** | bears outcomes in their own life; has standing | does not bear them; has no standing in the same sense |
| **Availability** | scarce, slow, interruptible | abundant, fast, cheap — which silently biases the collective toward whatever AI participants are good at |
| **Failure mode** | fatigue, motivated reasoning, deference to authority | confident fabrication, context-sensitivity mistaken for reasoning, silent correlation |
| **Revision** | changes mind for reasons and can state them | changes output with context, which may or may not be reasons |

Two of these deserve emphasis because they are load-bearing elsewhere in the design:

**`n_eff` defaults differ by kind.** The independence ledger (B4) should assume AI
participants are correlated until independence is demonstrated, and assume humans are
independent until correlation is demonstrated. Opposite priors, for good reason — AI
correlation is invisible and structural; human correlation is visible and social.

**Availability bias is a projection.** Because AI participants are cheap, the collective
will accumulate observations in whatever spaces AI participants can cheaply observe. That
is a `π` on the whole system, and it is nobody's declared blind spot. It needs to be
tracked at the collective level: *what fraction of M comes from which kind of participant,
and in which regions?*

## Mechanical consequences

1. **`kind` is a required field on every participant and every observation.** Not a label —
   a type that fusion, weighting, and authority rules dispatch on.

2. **Two ontologies, bridged, not merged.** `O_human` and `O_ai` are separate registered
   ontologies (D11t). Translations between them exist and carry named `Loss(F)`. In the
   language of Design C, *human and AI participants may be in the same A-mode region for
   some subject matter and never for others* — and which is which is discovered, not
   assumed.

3. **Blind-spot manifests are kind-specific.** An AI participant's manifest should name its
   model, context window, retrieval corpus and prompt lineage as part of `θ`. A human's
   should name role, stake, and what they have and have not seen. These are not the same
   fields, and forcing one schema on both is the collapse the rule forbids.

4. **Never average across kinds.** C1 already forbids averaging; across kinds it is worse
   than lossy, it is meaningless. Human and AI reports enter `M` as separately provenanced
   regions of the field, and their agreement is checked at the finest common refinement
   (Design B's guard), because apparent agreement across an ontology bridge is frequently
   an artifact of the bridge.

5. **Collapse authority is typed.** See `08-action.md` — this is where the distinction does
   the most work, and where it is derived by *function* (who bears the consequence, what
   gets foreclosed) rather than by status.

## What this does not claim

It does not claim humans are better observers. On many `π`, they are demonstrably worse —
slower, noisier, more biased, less able to hold detail. The distinction preserved here is
not competence. It is **standing and consequence-bearing**, which are relational properties
no amount of accuracy confers or removes.

Getting this backwards — "humans decide because humans are more reliable" — would collapse
a different and more important distinction, and would be falsified by the first measurement.

## Open

- Whether an AI participant's *refusal to collapse* constitutes a legitimate veto.
  Unresolved, and it is a values question rather than an empirical one. Recorded as
  residue, not scheduled for resolution. See `runs/001`.
- Whether `kind` is binary. Human-using-AI-assistance, AI-with-human-in-loop, and
  institutional participants are all plausibly distinct kinds. The two-value version is a
  starting compression and is expected to be wrong in the direction of too few kinds.
