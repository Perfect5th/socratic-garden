---
name: establish-user-context
description: 'Establish who a capability is for and what experience it should enable, early enough to shape the technical design: who interacts with it today, who might later, whether that boundary is intentional or just current, what users should accomplish, and what stays hidden. Covers the case where it is still undecided whether end users get this at all. Use while a design is being worked out, before the solution is settled.'
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

In a system of any size, most components are reached through other components,
so "internal" is often just "a few hops from a person". Follow the chain: who
consumes this, who consumes them, and does the effect eventually surface to a
human? Keep going until you reach someone or the chain genuinely stops inside the
system. Where it surfaces, that person's experience is in scope even though they
never touch this capability directly.

## When exposure is undecided, that is the decision to work on

"We don't know yet whether customers will get this" is the case this skill exists
for. It is not a footnote to record and move past. A design doc is where that
question gets confronted — it is not an engineering-only artifact, and the
audience question rarely gets a better moment than this one.

When the audience is genuinely open, work it through:

- **What would the end-user experience actually be** if it were exposed? Enough
  to be concrete — what they would do with it, what they would see, what they
  would need to understand. Not a full UX pass; enough that "exposed" means
  something specific rather than a shrug.
- **What would have to be true** for that to be a good experience, and does the
  current direction get there or away from it?
- **Which decisions here are hard to undo** if the answer turns out to be yes —
  names users would see, permission and tenancy models, error semantics, data
  shapes, API surface, compatibility promises.
- **What would settle it**, who decides, and by when.
- **What deferring costs.** Sometimes nothing. Sometimes it quietly picks an
  answer, because a design that only works for internal callers is a decision
  against exposure whether or not anyone said so.

Then record the outcome as a real position, not an absence:

> The capability is initially for internal use. Exposing it to end users later
> may be desirable, but that is not decided by this design. If it happens, the
> permission model and the error strings are the parts that would have to change.

Do not manufacture speculation. Pursue future exposure when it is plausible,
raised by the human, visible in the existing context, or materially relevant —
and drop it when it isn't.

## Keep it proportional

This is not a product-requirements exercise. Once you have followed the chain and
## Keep it proportional — but the call is the human's

This is not a product-requirements exercise, and a change with no real user
dimension should not become one. But **you do not get to decide it has none.**
Whether a change matters to users is a product judgment, and product judgments
belong to the human.

So ask, once, at a depth the change warrants. Where you have grounds for a
candidate answer, offer it for confirmation rather than asserting it — "this
looks like it stops at the storage layer and never surfaces to anyone; is that
right?" Then take their answer and move on. One question is usually enough for a
change that genuinely has no user dimension, and that is what keeps this
proportional.

What gets recorded is the human's conclusion, not yours:

> No meaningful end-user impact. This is intentionally internal and is not
> expected to become a user-facing interface.

Never write that because the change looked technical, and never write it without
having asked. An unasked question recorded as "no impact" is the exact failure
this skill exists to prevent — and it is not available at all while the audience
is still open. Match the depth to the change (see
[calibrate-scrutiny](../calibrate-scrutiny/SKILL.md)).

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
- if exposure is undecided, whether the design says what the end-user experience
  would be, what would have to change, who decides, and what deferring costs —
  or whether it just left the question hanging,
- whether technical decisions unnecessarily constrain a plausible future
  user-facing interface,
- whether product or UX decisions are hidden inside implementation choices,
- whether important user-facing effects are missing,
- whether unresolved user and product questions are recorded.

When the design cannot answer a user-experience question that matters here, that
is a **design gap**, not a task for a later documentation stage. Report it as
such.

Where a design states "intentionally internal, no user impact", your job is to
check whether a human actually decided that — not to re-judge it. If it reads as
an assumption nobody tested, say so and ask. If the author established it, accept
it; you don't overrule a product call, and you don't supply one either.

## Defer, don't duplicate

- For **who a document is written for**, use
  [identify-the-audience](../identify-the-audience/SKILL.md). This skill is about
  who the *capability* is for.
- For a **deep pass on the experience itself** — flows, terminology, failure
  behavior — that is the Define User Experience mode's job.
- For the **effects of a settled solution**, use
  [extract-user-facing-implications](../extract-user-facing-implications/SKILL.md).
