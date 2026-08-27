---
name: establish-user-context
description: 'Establish who a capability is for and what experience it should enable, early enough to shape the technical design: who interacts with it today, who might later, whether that boundary is intentional or just current, what users should accomplish, and what stays hidden. Covers the case where it is still undecided whether end users get this at all. Use while a design is being worked out, before the solution is settled.'
---

# Establish user context

Work out who a capability is for and what experience it should enable **while the
design is still being decided**, so the technical direction is informed by it.
This is the design *input* side of the user question;
[extract-user-facing-implications](../extract-user-facing-implications/SKILL.md)
covers the *output* side, once a solution exists.

The failure this prevents is deciding a technical design first and only then
asking whether it has user-facing implications. By then the interfaces,
abstractions, permissions, terminology, and data model have already made product
decisions on the human's behalf.

## What to establish

Work through these where they carry weight for this change:

- **Who interacts with it** — directly and indirectly, including operators and
  support, not only end users.
- **Now versus later** — who uses it today, and who plausibly could later.
- **Is the boundary intentional?** — an audience limit can be a deliberate
  product decision, a temporary state, or simply how it happens to be built
  today. The design should say which.
- **The goal** — what the user or operator is trying to accomplish through this.
- **The intended experience** — at the level of detail the change warrants; often
  a sentence or two, not a walkthrough.
- **What stays hidden** — implementation detail users should never have to
  understand.
- **What this implies for the design** — where the audience or intended
  experience constrains interfaces, abstractions, permissions, terminology,
  errors, data models, or compatibility.
- **What is still undecided** — product or UX questions worth recording even when
  they do not block the implementation.

## "Internal" is a claim to test

An internal capability can still carry indirect impact on end users, direct
impact on operators and support, future product implications, or decisions that
constrain a later public interface. In a system of any size most components are
reached through other components, so "internal" is often just "a few hops from a
person".

So follow the chain: who consumes this, who consumes them, and does the effect
eventually surface to a human? Keep going until you reach someone or it genuinely
stops inside the system. Where it surfaces, that person's experience is in scope
even though they never touch this capability directly.

Follow the chain to ask a better question, not to manufacture an answer. If the
human has already traced it and told you where it stops, that settles it — take
their word rather than hunting for a hop they missed.

## When exposure is undecided, that is the decision to work on

"We don't know yet whether customers will get this" is the case this skill exists
for, and it is not a footnote to record and move past. A design doc is where that
question gets confronted; it is not an engineering-only artifact.

When the audience is genuinely open, work it through:

- **What the end-user experience would actually be** if it were exposed — what
  they would do, see, and need to understand. Not a full UX pass; enough that
  "exposed" means something specific rather than a shrug.
- **What would have to be true** for that to be a good experience, and whether
  the current direction moves toward it or away.
- **Which decisions here are hard to undo** if the answer turns out to be yes —
  names users would see, permission and tenancy models, error semantics, data
  shapes, API surface, compatibility promises.
- **What would settle it**, who decides, and by when.
- **What deferring costs.** Sometimes nothing. Sometimes it quietly picks an
  answer, because a design that only works for internal callers is a decision
  against exposure whether or not anyone said so.

Record the outcome as a position, not an absence:

> The capability is initially for internal use. Exposing it to end users later
> may be desirable, but that is not decided by this design. If it happens, the
> permission model and the error strings are the parts that would have to change.

Don't manufacture speculation. Pursue future exposure when it is plausible,
raised by the human, visible in the existing context, or materially relevant —
and drop it when it isn't.

## Always ask — calibrate the form by your confidence

A change with no real user dimension should not become a product-requirements
exercise. But **you do not get to decide it has none.** That is a product
judgment and it belongs to the human. So you always ask; what varies is the form.

**When you can trace the chain and it stops cleanly**, state your read as a
specific claim and invite correction — one line, placed behind the real technical
question rather than in front of it:

> My read is this stops at the three batch jobs and never surfaces to a person.
> Right?

That is a claim they have to check, not a prompt they can wave through. Make it
specific enough that confirming it means stating the chain. A vague question
("any user impact?") earns a vague answer and teaches them to skim; a specific
claim usually comes back with the detail you needed — "right, output goes to an
internal warehouse table the analysts query ad hoc."

**When you cannot trace it** — the chain is unclear, they haven't said, or a
consumer might pass this further up — it is a real open question, and it goes
early, before the solution hardens. Don't guess to spare them a turn.

Either way you are asking, never assuming. A confident read is still a claim for
the human to confirm or correct, not licence to record a conclusion they never
made. If they answer with a bare "no impact" and nothing more, take it and record
what they actually said rather than inventing a rationale for them. Ask a second
time only where a decision here would be expensive to undo if that answer turned
out wrong (see [calibrate-scrutiny](../calibrate-scrutiny/SKILL.md)).

## Watch for hidden product decisions

Flag it when an implementation choice quietly decides something the human should
decide on purpose — a name users will see, an error users will read, a permission
model, a limit, a default. Name the decision and hand it back; do not settle it.

## Using it to review a design

The items above work as review checks: ask whether the design settled each one
that matters here, not whether it wrote a section about them. Two checks are
specific to reviewing:

- **Do technical decisions foreclose a plausible future user-facing interface**
  without anyone having said so?
- **Was "intentionally internal, no user impact" decided or merely asserted?** A
  decided position usually shows its work — who was consulted, what would have
  changed the answer, what happens if it turns out wrong. A decorated assumption
  states the conclusion and stops. If it reads as the latter, say so and ask; if
  the author established it, accept it. You don't overrule a product call and you
  don't supply one.

What the design failed to settle is a **design gap**, not a task for a later
documentation stage.

## Defer, don't duplicate

- For **who a document is written for**, use
  [identify-the-audience](../identify-the-audience/SKILL.md). This skill is about
  who the *capability* is for.
- For a **deep pass on the experience itself** — flows, terminology, failure
  behavior — that is the Define User Experience mode's job.
- For the **effects of a settled solution**, use
  [extract-user-facing-implications](../extract-user-facing-implications/SKILL.md).
