# 08 — The Collective Acts on M

**Answered:** the collective both acts on `M` and maintains it.

That answer creates a tension sharp enough to be worth running the framework on, which is
done in full at [`runs/001-act-and-preserve.md`](runs/001-act-and-preserve.md). This file
records the mechanisms that run produced.

---

## The short version of the run

Acting appears to require collapsing the field; maintaining `M` requires not collapsing it.
The dichotomy audit (D2t) finds the `acts ∧ preserves` cell heavily occupied — immune
responses, canary deploys, hedged portfolios, every organism — so it is **not** a
contradiction. The recovered variable that distinguishes the occupants is not decisiveness
but **foreclosure**: how much the action destroys the alternatives.

## Action profile

Actions decompose the way identity did:

```
A = (V, B, L, E, K, W)
```

| | |
|---|---|
| `V` | reversibility — can it be undone, at what cost |
| `B` | blast radius — how much of the world it commits |
| `L` | latency to feedback — how fast we learn we were wrong |
| `E` | **foreclosure** — how much it removes from the space of futures |
| `K` | collapse required — how much of `M` must become single-valued |
| `W` | who bears the consequence |

The point of the decomposition: **`K` is not constant.** A 1% canary requires almost no
collapse of `M`; an irreversible migration requires a great deal. "The collective acts" is
therefore not one operation with one cost.

## M1 · Action and probe are one category `core`

C3's probes and "the collective acts" are not two subsystems:

- a **probe** is an action with `E ≈ 0`
- an **action** is a probe with consequences

One type, carrying a `(collapse cost, information yield)` pair. The system prefers, among
actions of comparable expected value, the one with the highest yield per unit of
foreclosure.

This is D2 §16 made operational — living systems survive by ignoring most detail while
preserving the distinctions that matter *for action* — because the action-relevant
projection is now indexed to the action's own reversibility.

**Practical rule:** under uncertainty, prefer the action that is also a probe. Not out of
caution, but because it is the only class of action that *increases* `M` while acting on
it.

## M2 · The residue is the fiber of the action projection `core`

An action is a projection of the field: `a = π_a(M)`. Its fiber `π_a⁻¹(a)` is everything
`M` contained that this action did not distinguish.

So the residue D5t asks us to preserve is not a separate thing to remember. It is a fiber,
and B2's blind-spot machinery already describes it. No new storage, no new concept — an
action declares its blind spot the same way a participant does.

## M3 · Three kinds of resolution `core`

Parallel to state / pattern / trajectory identity:

| | Meaning | Updates `epistemic_status`? |
|---|---|---|
| **Epistemic resolution** | the question is settled | yes — rare |
| **Operational collapse** | a course is selected; `M` unchanged | no |
| **Structural foreclosure** | the possibility is destroyed | no, and this is the problem |

The third is new and is the one the design was missing. An irreversible action does not
merely commit resources — it changes the possibility space itself. In D6's terms
`dX/dt = G(x, X)`: the state space evolves, and foreclosure deletes regions of it.

## M4 · Irreversibility is an epistemic cost `strong`

```
epistemic_cost(a) = measure of hypotheses rendered permanently untestable by a
```

Risk frameworks price expected loss. None of them price **destroyed falsifiability**. But
an action that forecloses a region of `X` removes states that no future observation can
ever reach — it shrinks the collective's possibility field permanently, and the loss is
invisible to every existing metric.

This gives "keep your options open" a justification that is epistemic rather than merely
economic, and it makes the cost schedulable: an action's `E` is a quantity the system
estimates and publishes alongside its expected value.

**Open problem, honestly:** measuring `E` at all is hard. First approximation — count the
probes that would become impossible to run after the action. Crude, but it makes the cost
visible, which is the whole point.

## M5 · Collapse authority is typed by foreclosure and consequence `core`

This is where `07-participants.md`'s non-collapse rule does the most work.

| Foreclosure `E` | Consequence-bearer `W` | Authority |
|---|---|---|
| `≈ 0` (probe-class) | any | any participant, or automatic |
| low | internal to the collective | AI participant may collapse; logged with reopening trigger |
| high | internal | human collapse authority required |
| any | **external** | human collapse authority required |
| total (structural foreclosure) | any | human authority **plus** a published epistemic-cost statement naming what is being made permanently untestable |

The rule is derived from **function, not status**: foreclosure and consequence-bearing are
coupled, and only one kind of participant currently stands in the consequence-bearing
relation. It is emphatically *not* "humans decide because humans are more reliable" — that
premise is false on most projections and would collapse the distinction it is meant to
preserve.

## M6 · Action changes the referent `strong`

D6 §11: observation is not passive — `yᵢ = πᵢ(x, oᵢ)` and `dx/dt = F(x, oᵢ, yᵢ)`.

Once the collective acts, it stops merely observing its domain and begins constituting it.
This has a specific and unwelcome consequence for Design A:

> **Intersection semantics are valid between actions, not across them.**
> `⋂ πᵢ⁻¹(yᵢ)` presumes a fixed `X`. If acting changes `X`, the fibers are indexed to an
> epoch, and observations from before an action cannot be intersected with observations
> from after it without a declared transport.

Because the answer to "does the collective act?" is yes, this is not hypothetical. Every
A-mode region needs an **epoch marker**, and observations carry the epoch they were taken
in. Cross-epoch fusion requires an explicit bridge, exactly like a cross-ontology one.

## What this adds to `M`

`M` gains a field:

```
M = { …, foreclosed }   # regions of the possibility space this collective
                        #   has permanently removed, and by which actions
```

Which is the collective's record of what it can no longer find out — the exact complement
of `unobserved_regions`, and considerably more expensive.
