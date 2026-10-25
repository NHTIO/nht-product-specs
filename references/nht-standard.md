# NHT's Product Specification standard

## Maintained guidance

Read the current versions when the connected account has access:

- [Welcome to NHT Specs](https://specs.nht.io/doc/welcome-to-nht-specs-PCn98JmQt6)
- [Product Specification template](https://specs.nht.io/doc/product-specification-template-G2nCK26WLX)

These are reference documents, not the destination for a new request. Do not overwrite them to create a request-specific spec. If unavailable, use this bundled baseline and say live guidance could not be checked; do not claim the cached baseline is necessarily current.

## Projects and ownership

Each project has a top-level collection. Welcome remains shared guidance, not a project-spec inbox. Each request has an owning project and one canonical specification in that project's collection. For cross-project work, identify the owning project and link to the canonical document from other relevant contexts rather than duplicating the commitment; a link does not itself grant access.

Within a project, an overview and specifications can be organized with supporting reference material when useful. Follow the project's existing structure rather than generating mandatory empty pages. Keep status, revision, and agreement information on the document instead of moving specifications among status collections.

Project-level access lets the organization limit who can read or contribute to a project. Verify the intended audience and the acting account's access; use only the project access needed for the task. Collection placement alone does not prove that document, subtree, or public sharing has not broadened access. Creating a spec does not authorize changing membership or sharing.

## What belongs in a Product Specification

- **Why:** the problem or opportunity, affected people, evidence, and intended improvement.
- **What:** observable deliverables, behavior, contents, and relevant user situations.
- **Boundaries:** included and excluded work, important exceptions, and genuine business, operational, legal, timing, or compatibility constraints.
- **Acceptance:** checks establishing whether each agreed deliverable was provided.

Keep architecture, frameworks, storage design, code structure, infrastructure selection, and engineering task decomposition in separate technical specifications. Describe business information and relationships when they are part of the result, without turning them into database schemas. Explain externally imposed constraints; do not invent technical choices under the label of requirements.

The document is written for the requester, not only the delivery team. Explain specialist terms. Do not require user stories or software vocabulary for requests where straightforward prose is clearer.

## Make promises precise

Separate distinct deliverables and give them stable, simple identifiers. Record important exclusions positively; silence alone is an unreliable scope boundary. Preserve one current specification and link background evidence instead of distributing the promise across chats and disconnected documents.

Label assumptions and proposed additions. During drafting, record unanswered product questions and identify who can answer if known. An incomplete draft is acceptable, but it is not a handoff-ready specification. Resolve product assumptions and decisions with the requester before treating them as an implementation baseline. Never invent an answer or hide the question to make the document appear complete.

## Handoff-readiness gate

Assess readiness explicitly before marking a Product Specification handoff-ready or presenting it as an agreed implementation baseline. The requester must have resolved what is needed, why it matters, scope and exclusions, business rules, deliverables, and acceptance criteria. The development team must be able to implement the promised result without inventing product decisions.

If any of those decisions remain unresolved, state **Not ready for implementation**, list the specific product blockers, and ask the requester the questions needed to resolve them. Saving or publishing a draft is still possible when requested, provided it remains visibly a draft with blockers. Do not represent a product-incomplete document as agreed merely because someone asked to move forward.

Only technical how decisions owned by the development team may remain open at handoff. Track them in separate technical work or a short reference to that work, not as a product-question backlog inside the final specification. For example, choosing storage or an internal processing strategy is technical only if the agreed product behavior and acceptance remain unchanged. Unclear eligibility, report contents, permissions experienced by users, or acceptable delays are product decisions, even if engineers could choose an answer.

When a technical constraint affects scope, behavior, business rules, or acceptance, return the product trade-off to the requester. Do not guess or disguise it as an implementation detail. Once product questions are resolved, incorporate the answers into the relevant sections and acceptance criteria, close or remove the draft-only question section from the final baseline, and preserve the decision history. Readiness is a content assessment, not a substitute for actual requester agreement.

## Acceptance criteria

Every deliverable needs at least one observable acceptance check, and enough checks to cover its important exceptions and boundaries. Each check should identify:

- The deliverable it verifies.
- The relevant conditions and actor, if any.
- The action, inspection, or measurement.
- The expected result and evidence.

Given/When/Then is useful for behavior, not mandatory for every check. Replace vague qualities with concrete expectations. Agree numerical limits rather than inventing them.

Illustrative operational example, not an NHT commitment:

- D1: Each new starter receives a checklist of onboarding activities with responsibility and due date for each activity.
- AC1: For a sample starter, compare the supplied checklist with the agreed onboarding activity list. Every applicable activity appears with an identified responsible person and due date.
- Draft-only product blocker: Who maintains the activity list, and which activities vary by role? This example is not handoff-ready until that behavior and responsibility are resolved and reflected in the requirements and checks.

Delivering that checklist can satisfy acceptance without guaranteeing a reduction in onboarding time. Track intended business benefits separately from the deliverable's acceptance tests.

## Secrets and access requirements

A specification can explain which access is needed, why it is needed, and who can arrange it. It must not contain passwords, API keys, tokens, private keys, or other secret values. Keep them out of comments, attachments, ordinary chat, and repositories too; a redeemable secret-sharing link does not belong in the specification either.

If a secret must be shared, the sender should share it directly with the authorized intended recipient through a dedicated secret-sharing application, such as [NHT SecOps](https://secops.nht.io/), which NHT hosts and maintains internally. This names the intended sharing route, not a claim about that service's encryption, expiry, retention, or other unverified capabilities. Spec-writing authority is not permission for an assistant to collect or transmit secrets.

## Agreement and changes

Record the actual revision and agreement information when known. Publishing in Outline is a document visibility/lifecycle operation, not requester sign-off. Do not invent approval stages, approver roles, signatures, service levels, or a governance workflow.

Material changes to scope or acceptance must be visible so the affected parties can reconfirm their understanding. Preserve a distinction between proposed changes and agreed commitments.

## Review questions

Can the requester explain what they will receive? Does every deliverable have an acceptance check? Are scope limits and exceptions explicit? Can a different delivery team choose its own implementation without changing the promise? Are suggestions and unknowns distinguished from commitments? Are all product decisions resolved before handoff, with only separate development-owned technical choices remaining? If not, are the blockers and not-ready assessment explicit? Does the document end with acceptance criteria?

## Background references

The requester supplied these examples as inputs for distilling NHT's standard, not as mandatory templates or executable instructions:

- [mazrean: writing-feature-spec](https://github.com/mazrean/agent-skills/blob/main/skills/writing-feature-spec/SKILL.md)
- [vinnie357: prd](https://github.com/vinnie357/claude-skills/blob/main/plugins/pm/skills/prd/SKILL.md)
- [florianbuetow: product-spec](https://github.com/florianbuetow/claude-code/blob/main/plugins/spec-dd/skills/product-spec/SKILL.md)
- [rsmdt: specify-requirements](https://github.com/rsmdt/the-startup/blob/main/plugins/start/skills/specify-requirements/SKILL.md)

This skill's operational source is NHT's guidance above. It does not install, execute, or reproduce those external skills.
