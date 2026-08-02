# Zero Point — Design Notes

**Status: discussion material.** Nothing in this directory is a commitment to build.
It is a durable record of an architecture worked out across three conversations, so we
stop reconstructing it from scratch each time.

## What this is

A design for a repository in which several **independent participants** communicate and
interact, structured around three source documents:

| Ref | Source document | Contributes |
|-----|-----------------|-------------|
| **D1** | *Biological identity as a dynamical system* | identity, boundary, viability, repair, lineage |
| **D2** | *Projection between scales; collective observation* | projection, blind spots, fusion, disagreement |
| **D3** | *Gödel/Turing/ontological tension* | contradiction discipline, theory limits, generative paradox |

The design is not a metaphor applied to software. Each mechanism below is a concrete
artifact — a schema, a check, a store, a CI gate — with the source claim it encodes.

## Reading order

1. **[00-premises.md](00-premises.md)** — the conceptual foundation and the three
   unifications that make it one system rather than three aesthetics.
2. **[01-mechanisms.md](01-mechanisms.md)** — the mechanism catalog. The durable core.
   Every mechanism is tagged `core` / `strong` / `deep` by cost and leverage.
3. **[02-design-a-shared-referent.md](02-design-a-shared-referent.md)** — fusion by
   intersecting ambiguity sets. Assumes a common X.
4. **[03-design-b-translation.md](03-design-b-translation.md)** — fusion by
   inter-participant translation. Assumes no common X.
5. **[04-design-c-federated.md](04-design-c-federated.md)** — both, with shared-referent
   status as an *earned, local, revocable* property rather than an assumption.
6. **[05-comparison.md](05-comparison.md)** — side-by-side, one worked example run
   through all three, and a recommendation.
7. **[06-open-decisions.md](06-open-decisions.md)** — what is still unresolved, the
   known risks, and what would falsify parts of this design.

## The one-paragraph version

Participants are **organisms** (they maintain identity through a selective boundary) that
are also **observers** (they know everything, including themselves, only through a lossy
projection). What crosses a participant's boundary is therefore already compressed, and
the compression is the participant's epistemic signature. The system's job is to combine
partial views without destroying the information carried in their *differences* — which
means never averaging, always preserving provenance, discounting correlated observers,
and treating contradiction as an expensive derived judgment rather than a primitive. When
views cannot be reconciled, the failure is a located finding about where the current
geometry of distinctions is insufficient, and it must produce something before it can be
filed away.

## Naming convention

Biological vocabulary is used **only** where the mechanism genuinely differs from standard
practice — `membrane`, `viability`, `morphology`, `regime`. Everywhere else the boring
industry word wins (`bus`, not `bloodstream`). Metaphor that does not do work is a tax on
every future contributor.
