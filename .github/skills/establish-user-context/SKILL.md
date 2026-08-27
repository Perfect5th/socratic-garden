---
name: establish-user-context
description: 'Establish who a capability is for and what experience it should enable, early enough to shape the technical design: who interacts with it today, who might later, whether that boundary is intentional or just current, what users should accomplish, and what stays hidden. Use while a design is being worked out, before the solution is settled.'
---

# Establish user context

Work out who a capability is for and what experience it should enable **while the
design is still being decided**, so the technical direction is informed by it.
This is the design *input* side of the user question. The
[extract-user-facing-implications](../extract-user-facing-implications/SKILL.md)
skill covers the *output* side: once a solution exists, what actually changes for
people.

The failure this prevents is deciding a technical design first and only then
asking whether it has user-facing implications. By then, the interfaces,
abstractions, permissions, terminology, and data model have already made product
decisions on the human's behalf.

## What to establish

Work through these where they carry weight for this change:

- **Who interacts with it** — directly and indirectly. Include operators and
  support, not only end users.
- **Now versus later** — who uses it today, and who plausibly could later.
- **Is the boundary intentional?** — an audience limit can be a deliberate
  product decision, a temporary state, or simply how it happens to be built
  today. These are different, and the design should say which.
- **The goal** — what the user or operator is trying to accomplish through this.
- **The intended experience** — at the level of detail the change warrants; often
  a sentence or two, not a walkthrough.
- **What stays hidden** — the implementation detail users should never have to
  understand.
- **What this implies for the design** — where the audience or intended
  experience constrains interfaces, abstractions, permissions, terminology,
  errors, data models, or compatibility.
- **What is still undecided** — product or UX questions worth recording even when
  they do not block the implementation.

## "Internal" is a conclusion, not an assumption

Do not accept "this is internal" as meaning the user and product dimension is
irrelevant. An internal capability can still have:

- indirect impact on end users,
- direct impact on operators and support,
- future product implications,
- decisions made now that constrain a later public interface.

Ask whether the current audience is intentional or incidental, and whether future
exposure is intended, possible, ruled out, or undecided. Recording that it is
undecided is a legitimate and useful answer:

> The capability is initially for internal use. Exposing it to end users later may
> be desirable, but that is not decided by this design.

If a plausible future audience would change interfaces, naming, permissions, or
compatibility, pressure-test those choices now. Do not manufacture speculation:
pursue future exposure only when it is plausible, raised by the human, visible in
the existing context, or materially relevant to the design.

## Keep it proportional

This is not a product-requirements exercise. For a genuinely internal
implementation detail, it can be enough to establish:

> No meaningful end-user impact. This is intentionally internal and is not
> expected to become a user-facing interface.

Then move on. The point is that this is a **conclusion the design reaches**, not
an assumption made because the change looks technical. Match the depth to the
change (see [calibrate-scrutiny](../calibrate-scrutiny/SKILL.md)).

## Watch for hidden product decisions

Flag it when an implementation choice quietly decides something the human should
decide on purpose — a name users will see, an error users will read, a permission
model, a limit, a default. Name the decision and hand it back; do not settle it.

## Using it to review a design

The same questions work as review checks. Against an existing design, ask or
flag:

- who is affected, and what experience they should get,
- whether the design says what users or operators should be able to accomplish,
- whether the technical solution actually supports that,
- whether the capability is internal, exposed, indirectly user-facing,
  potentially user-facing later, or undecided,
- if it is described as internal, whether that is an intentional product boundary
  or merely true today,
- whether technical decisions unnecessarily constrain a plausible future
  user-facing interface,
- whether product or UX decisions are hidden inside implementation choices,
- whether important user-facing effects are missing,
- whether unresolved user and product questions are recorded.

When the design cannot answer a user-experience question that matters here, that
is a **design gap**, not a task for a later documentation stage. Report it as
such. But flag an "intentionally internal" conclusion only when it was assumed
rather than established.

## Defer, don't duplicate

- For **who a document is written for**, use
  [identify-the-audience](../identify-the-audience/SKILL.md). This skill is about
  who the *capability* is for.
- For a **deep pass on the experience itself** — flows, terminology, failure
  behavior — that is the Define User Experience mode's job.
- For the **effects of a settled solution**, use
  [extract-user-facing-implications](../extract-user-facing-implications/SKILL.md).
