# zero-point

A repository for a system of **independent participants** that communicate and interact —
designed around the idea that each participant maintains its identity through a selective
boundary, and that this same boundary is a lossy projection through which it knows
everything, including itself.

**Nothing is implemented yet.** The design is under discussion.

→ **[docs/design/](docs/design/README.md)** — premises, mechanism catalog, three candidate
architectures, and the open decisions.

## Shape of the idea

Participants are organisms *and* observers. What crosses a participant's membrane is
already compressed, so combining views is not averaging — it is preserving the information
carried in their differences. That means: no bare values on the wire, declared blind spots,
confidence discounted by observer correlation, contradiction treated as an expensive
derived judgment rather than a primitive, and every unresolved tension required to produce
something before it can be filed away.

Three candidate designs differ in what combination *means* — intersecting ambiguity sets
over a shared referent, translation between perspectives with no shared referent, or a
federation where shared-referent status is earned locally and can be revoked. See
[`05-comparison.md`](docs/design/05-comparison.md).
