# Intent-Driven Template

This is a template project for intent-driven software delivery with [OpenSpec](https://github.com/Fission-AI/OpenSpec),
[OpenCode](https://opencode.ai/), and reusable engineering skills.

It is intended for teams that want changes to start from clear intent, move
through explicit behaviour and design artifacts, and finish with implementation
tasks that preserve the reasoning behind the work.

This template also makes OpenSpec spec-as-source capable: fenced Gherkin specs
can be extracted into acceptance tests, while workflow rules keep specification
changes and code changes separated so the OpenSpec specification remains the
source of truth.

## Walkthrough

Read the full walkthrough: [Spec-Driven Development with OpenSpec and OpenCode](https://intent-driven.dev/blog/2026/05/10/spec-driven-development-openspec-opencode/).

[![Spec-Driven Development with OpenSpec and OpenCode](https://img.youtube.com/vi/M3dp9u1wZes/maxresdefault.jpg)](https://www.youtube.com/watch?v=M3dp9u1wZes)

Read the full walkthrough: [SDD with Multi-Model Spec Review and Glossary](https://intent-driven.dev/blog/2026/06/27/sdd-adversarial-authoring-glossary/)

[![Spec-Driven Development Multi-Model Adversarial Authoring and Glossary with OpenCode and OpenSpec](https://img.youtube.com/vi/2V78VVJ1sa0/maxresdefault.jpg)](https://www.youtube.com/watch?v=2V78VVJ1sa0)

Read the full walkthrough: [Behavior-Driven Development and Spec-Driven Development with OpenSpec](https://intent-driven.dev/blog/2026/07/17/behavior-driven-development-sdd-openspec/).

[![Behavior-Driven Development and Spec-Driven Development with OpenSpec](https://img.youtube.com/vi/xoPjF-Z2Qgw/maxresdefault.jpg)](https://youtu.be/xoPjF-Z2Qgw)

## How To Use This Template

### Start A New Project From This Template

Clone this repository, open it with OpenCode, and start working from the bundled
OpenSpec configuration, commands, skills, and schema.

### Add This Template To An Existing Project

Open your existing project with OpenCode and ask it to install the template:

```text
Read and understand INSTALL_TEMPLATE.md and follow the instructions there.
```

## What This Template Uses

- OpenSpec for setup, proposal, specification, design, ADR, and task artifacts.
- Custom schemas from https://github.com/intent-driven-dev/openspec-schemas.
- A bundled local copy of the `intent-driven` custom schema from
  https://github.com/intent-driven-dev/openspec-schemas/tree/main/openspec/schemas/intent-driven
  for the full `proposal -> specs -> design -> adr -> tasks` lifecycle.
- OpenSpec git discipline so proposals land on `main` before apply, and
  implementation lands on `main` before archive.
- OpenCode skills for repeatable collaboration and implementation workflows,
  including C4 diagrams, ADR authoring, and OpenSpec lifecycle commands.
- Superpowers from https://github.com/obra/superpowers for guided practices such
  as brainstorming, planning, debugging, TDD, verification, worktrees, and
  subagent-driven parallel work.
- A `grill-me` style of rigorous design interrogation, inspired by
  https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md.
- ADRs for durable architectural decisions.
- C4 diagrams for communicating architecture boundaries and relationships.
- Fenced Gherkin requirements and scenarios for observable behaviour, with optional acceptance-test runner scaffolding.

The bundled OpenSpec schema is a local copy of the `intent-driven` schema from
https://github.com/intent-driven-dev/openspec-schemas/tree/main/openspec/schemas/intent-driven.

## Workflow

The intent-driven workflow moves through these artifacts in order:

```text
proposal -> specs -> design -> adr -> tasks
```

- `proposal` captures why the change matters.
- `specs` describe observable behaviour with fenced Gherkin scenarios.
- `design` explains the implementation approach and trade-offs.
- `adr` records durable architectural decisions.
- `tasks` turn the accepted intent, behaviour, design, and decisions into work.

## Schema

This repository includes a bundled local copy of the `intent-driven` schema at
`openspec/schemas/intent-driven/`. The upstream schema lives in
https://github.com/intent-driven-dev/openspec-schemas/tree/main/openspec/schemas/intent-driven.

To activate the schema, set this in `openspec/config.yaml`:

```yaml
schema: intent-driven
```

To validate it, run:

```bash
openspec schema validate intent-driven
```

## Skills

Standard OpenSpec lifecycle skills in `.opencode/skills/` — names are self-explanatory:
`openspec-new-change`, `openspec-propose`, `openspec-continue-change`, `openspec-explore`,
`openspec-apply-change`, `openspec-verify-change`, `openspec-sync-specs`, `openspec-archive-change`

| Skill | Location | Purpose |
|-------|----------|---------|
| `openspec-bulk-apply-change` | `.opencode/skills/` | Applies multiple active changes concurrently in isolated worktrees with parallel verification. |
| `adversarial-authoring` | `.opencode/skills/` | Runs author and reviewer agents in sequence to reduce model bias in drafts. |
| `grill-me` | `.agents/skills/` | Interrogates plans and designs with probing questions to surface hidden assumptions. |
| `c4-diagrams` | `.agents/skills/` | Visualises system architecture using C4 model levels in ASCII or Mermaid. |
| `architectural-decision-records` | `.agents/skills/` | Captures architectural decisions with rationale, tradeoffs, and supersession chains. |
| `gherkin-authoring` | `.agents/skills/` | Drafts and improves Gherkin scenarios for observable, domain-language behaviour. |
| `acceptance-test-authoring` | `.agents/skills/` | Sets up and maintains acceptance tests that extract fenced Gherkin from OpenSpec Markdown specs. |
| `bdd-zone-check` | `.agents/skills/` | Guides spec-first work and keeps specs-zone changes separate from code-zone changes. |
| `glossary` | `.agents/skills/` | Maintains business and technical terminology and companion glossary references for specification artifacts. |
| `openspec-git-discipline` | `.agents/skills/` | Enforces that proposals reach `main` before apply, and implementation merges before archive. |

The source behavior-driven template also includes Claude Code hooks for live zone enforcement. Those hooks are intentionally not copied here; `bdd-zone-check` is guidance unless an OpenCode equivalent is wired later.

The `acceptance-test-authoring` skill includes JavaScript (`cucumber-js`) and Python (`behave`) runner packs as examples. Use the pack that matches your project, adapt it to your application's startup and page-object conventions, or replace it with an equivalent runner for your preferred stack while preserving the fenced-Gherkin extraction and effective-spec behavior.

## Agents

Specialist agents used within skills, in `.opencode/agent/`:

| Agent | Purpose |
|-------|---------|
| `adversarial-author` | Writes an initial draft of a specification artifact or design document. |
| `adversarial-reviewer` | Reviews the author's draft with challenges and improvement suggestions. |
