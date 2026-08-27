---
name: extract-user-facing-implications
description: 'Identify how a settled or proposed change affects the people who use or operate a system: tasks, terminology, UI/API behavior, errors, setup, environment and constraints, migration, support, and docs. The downstream counterpart to establish-user-context. Use when clarifying a change, reviewing a solution, or planning documentation.'
---

# Extract user-facing implications

Given a change with a solution in view, work out how it affects the people who use
or operate the system. This is the *consequence* side of the user question: given
this design, what actually changes for people? For the *input* side — who the
capability is for and what experience should shape the design in the first place —
use [establish-user-context](../establish-user-context/SKILL.md).

Walk through each dimension and note where the change lands:

- **Tasks** — what users can now do, must do differently, or can no longer do.
- **Terminology** — new or changed names, labels, and words users encounter.
- **UI / API behavior** — visible changes to screens, commands, or endpoints.
- **Errors** — new failure messages, changed conditions, removed errors.
- **Setup / configuration** — new options, defaults, or required steps.
- **Environment / constraints** — versions, platforms, and specialized
  environments this depends on, plus security, networking, and permission
  considerations the user must account for.
- **Migration** — what existing users must do to adopt the change.
- **Support** — new questions, tickets, or troubleshooting this may cause.
- **Documentation** — which docs must change and which new docs are needed.

For each impact:

- Note the affected audience (end users, operators, developers, support, etc.).
- Distinguish confirmed impacts from suspected ones.
- List anything you cannot determine as an open question.

The point is to make the human consequences of a technical change visible before
they surprise someone. Finding none is a valid result — say so rather than
stretching for an impact.
