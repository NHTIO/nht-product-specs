# Fallback specification structure

Prefer the current NHT Specs template. This structure is a fallback, not a second competing standard. Fill it with the requester's actual material; remove irrelevant prompts instead of fabricating answers. Keep identifiers stable during revisions.

Use the requested capability or outcome as the document title. In Outline, pass it in the separate title field, not an H1 at the beginning of the body.

**Owning project:** the project whose collection holds this canonical specification. Link related projects when relevant; do not duplicate the specification or treat links as access grants.

**Requester:** who is asking and can clarify the need.

**Current state and revision:** keep status in the document rather than moving it among collections. Distinguish an initial draft, proposed changes, and an actually agreed version. Record agreement participants/date only when known. Do not label a product-incomplete draft handoff-ready or an agreed implementation baseline.

## Problem and purpose

Describe today's situation, affected people, why it matters, and supporting evidence. Separate facts from assumptions.

## People and situations

Identify recipients, users, or other affected people and the circumstances the deliverables must support. Define unfamiliar roles or terms.

## Desired outcomes

Explain the intended improvement and how it might be assessed. Do not confuse an expected business benefit with guaranteed delivery acceptance.

## Deliverables and requirements

For each D1, D2, and subsequent deliverable, describe:

- What the requester will receive.
- Required observable behavior or contents.
- Important situations, exceptions, and limits.
- Its linked acceptance criteria.

Keep implementation design elsewhere.

## Scope and exclusions

State included and excluded work. Explain boundaries with related requests or later phases without making unapproved future commitments.

## Constraints and dependencies

Explain genuine constraints on the result and their rationale. Identify information, availability, or decisions needed, without turning the section into an engineering dependency plan. Distinguish fixed dates from preferences and unconfirmed targets.

For access dependencies, record the required access, its purpose, and the responsible contact, not passwords, keys, tokens, private keys, or redeemable secret links. Secret values belong in direct sharing to the authorized intended recipient through a dedicated application such as [NHT SecOps](https://secops.nht.io/), not in this document, its comments or attachments, ordinary chat, or the repository.

## Draft-only product questions and readiness

While drafting, record unanswered questions about what, why, scope, business rules, deliverables, or acceptance; identify the requester or decision owner when known. State **Not ready for implementation** and list these product blockers explicitly. Do not leave them for the development team to decide.

Before handoff, resolve the product questions with the requester, incorporate the answers into the requirements and acceptance criteria, and close or remove this draft-only question section from the final baseline while preserving decision history. Do not delete unresolved evidence, relabel product choices as technical, or invent answers to pass the gate.

Record the readiness assessment in the document's state/revision information. Only technical how decisions owned by the development team may remain open; link separate technical work if useful rather than filling the Product Specification with implementation decisions. A technical constraint that changes the promised result requires a requester decision before handoff.

## Acceptance criteria

Finish the specification with this section. For each AC1, AC2, and subsequent check, include the deliverable verified, conditions, action or inspection, expected result, and evidence. Cover every deliverable and its important boundary cases. Use Given/When/Then or plain statements as appropriate, and leave unagreed thresholds visible as product blockers in a draft rather than inventing numbers. Resolve all thresholds required to judge acceptance before treating the specification as handoff-ready.
