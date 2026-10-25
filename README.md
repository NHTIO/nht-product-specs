# NHT Product Specs

An agent skill for helping requesters write and maintain Product Specifications in [NHT Specs](https://specs.nht.io).

A Product Specification describes what the requester expects to receive, why it is needed, its deliverables and scope, and how acceptance is verified. It is separate from technical design and implementation planning. The skill combines that NHT standard with practical navigation and authoring through Outline's native MCP server.

## Readiness for implementation

Drafts can expose unanswered product questions. Before a spec is marked handoff-ready or an agreed implementation baseline, the requester must resolve its what, why, scope, business rules, deliverables, and acceptance criteria. The skill reports unresolved product decisions as blockers rather than asking the development team to guess. Only technical implementation decisions owned by that team may remain open, tracked separately. If a technical constraint changes the promised product result, that choice returns to the requester. Publishing a document is not approval or proof of readiness.

## Organization

Top-level collections in NHT Specs represent projects. Welcome holds shared requester guidance and the reusable template. Each request belongs in its owning project collection; cross-project work links to one canonical specification rather than duplicating it. Project collections provide a practical access boundary, but actual document sharing and permissions still need to be checked. The skill does not create collections or change access as a side effect of writing a specification.

## Install

This repository is one standalone skill. Install or copy the repository as a folder named `nht-product-specs` in your client's skill directory. Keep `SKILL.md`, `references/`, and `agents/` together. Consult your client's skill-installation documentation for its supported path and reload behavior.

If your client supports the [Agent Skills](https://agentskills.io) format, it can read the root `SKILL.md`. `agents/openai.yaml` supplies optional Codex UI metadata; the core skill does not depend on that file.

The skill does not install an MCP server, create credentials, or grant workspace access. Connect your client to `https://specs.nht.io/mcp` using your own authorized NHT Specs account. See [connection and workflow](references/specs-mcp.md) for commands and verification steps.

## Use

Ask your assistant, for example:

- “Use nht-product-specs to turn this request into a Product Specification. Ask about material gaps before treating them as requirements.”
- “Review this NHT spec for unclear deliverables and missing acceptance criteria; do not edit it yet.”
- “Assess this specification for handoff readiness and save the resulting draft in the project collection I specify.”

Codex also supports explicit invocation as `$nht-product-specs`.

The maintained standard and template live in NHT Specs. The bundled references provide a baseline when those pages cannot be read, but access to the public skill does not grant access to private specifications. No project specifications or credentials belong in this repository. Passwords, keys, tokens, and other secrets must stay out of specifications, comments, attachments, and ordinary chat as well. Share secrets directly with an authorized intended recipient through a dedicated application such as NHT's internally hosted and maintained [SecOps](https://secops.nht.io/). Record only the access requirement, purpose, and responsible contact in the specification, not the value or a redeemable secret link. MCP authentication continues to use the client's secure OAuth flow.

## Contents

- `SKILL.md`: scope, workflow, and reference routing.
- `references/nht-standard.md`: product-spec principles and review guidance.
- `references/specification-structure.md`: fallback document structure.
- `references/specs-mcp.md`: connection, discovery, and safe authoring mechanics.
- `agents/openai.yaml`: optional Codex display metadata.

The background skills supplied as examples are linked in the standard reference. This repository contains original NHT-focused guidance, not copies of those skills.
