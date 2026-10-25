# Connect to and work in NHT Specs

## Connection

NHT Specs uses Outline at `https://specs.nht.io`. Its native MCP endpoint is:

`https://specs.nht.io/mcp`

Use Streamable HTTP. Outline documents OAuth as the default authentication flow. Prefer the client's secure sign-in flow. Never solicit, paste, or store passwords, API keys, tokens, private keys, or other secrets in specifications, comments, attachments, ordinary chat, skill files, or repository configuration.

If the client's existing NHT Specs/Outline connector works, reuse it. Otherwise, with the user's authorization to configure their client, use its remote-MCP setup. Examples from [Outline's official MCP guide](https://docs.getoutline.com/s/guide/doc/mcp-6j9jtENNKL), adapted to NHT's domain:

```sh
# Claude Code: add the server, then use /mcp to sign in.
claude mcp add --transport http nht-specs https://specs.nht.io/mcp

# Codex: add the remote server, then follow the client's authentication flow.
codex mcp add nht-specs --url "https://specs.nht.io/mcp"
```

For a connector UI, enter the same endpoint. Outline supports workspace-level MCP enablement and API-key authentication, but neither changing workspace settings nor generating a key is an automatic setup step. An authorized administrator handles disabled MCP; obtain required authorization before creating persistent access.

Validate connection with a harmless collection listing and fetch the Welcome guide. An endpoint responding does not prove successful OAuth or the account's write access. The setup commands above are documented configuration examples, not a claim that this skill has run them on the user's client.

For access needed by the requested work, record only the requirement, purpose, and responsible contact in the spec. If a secret must be shared, direct the user to send it directly to the authorized intended recipient using a dedicated secret-sharing application such as NHT's internally hosted and maintained [SecOps](https://secops.nht.io/). Do not put the secret or a redeemable sharing link in the spec. This does not replace MCP's client-managed OAuth authentication, authorize the assistant to transmit secrets, or establish unverified service capabilities.

## Workspace organization

- **Project = top-level collection.** Put each request's canonical specification in its owning project's collection, not a general Specifications collection.
- **Welcome** remains shared requester guidance and the reusable template. Begin with the [Welcome guide](https://specs.nht.io/doc/welcome-to-nht-specs-PCn98JmQt6); do not put project requests into the guide or template.
- Discover accessible project collections and their hierarchy, then resolve the owning project from the user's request and current context. If the project, destination, or cross-project ownership is ambiguous, ask. An absent collection may be inaccessible rather than nonexistent; do not silently create a replacement.
- Follow each project's existing organization. A project overview, specification documents, and optional supporting references are useful when needed, not a mandatory empty scaffold.
- For cross-project work, keep one canonical specification in the owning project and use authorized links from related contexts. Verify recipients can access what they need; links do not grant access and do not authorize changing it.
- Keep draft/review/agreement status as document metadata or clearly labeled content. Do not move documents among collections to express status; doing so may change access.
- Do not assume a required Monday register, GitLab backend, or mandatory approvals service.

## Project access

Treat the project collection as the normal access boundary and verify the acting account's read/write permissions for the requested operation. Use the least project access necessary. Check the intended audience and available sharing metadata before adding sensitive material; document-specific, subtree, or public sharing can broaden effective access beyond the collection's membership.

Do not infer that a collection is private merely from its name, or that visible content can be edited. A request to write a specification does not authorize creating collections, adding members, changing roles, enabling public links, or changing document sharing. If access is insufficient or the audience is uncertain, report the exact blocker and ask for an appropriate destination or authorized administrator action. Never change permissions automatically to finish the write.

## Tool discovery and reading

Tool names depend on the client and configured server alias. Use the actual server's tool descriptions and schemas, not a hard-coded ChatGPT-specific prefix. The NHT Specs connector currently exposes these logical operations:

- `list_collections`: find accessible collections; paginate using the tool's limit/offset.
- `fetch` with resource `collection`, or `list_collection_documents`: inspect a collection's published document tree. Drafts and archived documents are not included in that tree.
- `list_documents`: search existing specs by title/content; inspect likely matches before creating a duplicate.
- `fetch` with resource `document`: read current content and metadata. The same operation supports collection, template, and other documented resource types.
- `list_templates`: discover actual Outline templates, including their content. The Welcome page named “Product Specification template” is a reference document; do not assume its document ID is a `templateId`.

Refresh the target before editing. If guidance changed or the requester supplied a different current template, reconcile the difference explicitly rather than overwriting it with the bundled baseline.

## Authorized creation

Check any permission metadata returned for the destination. If it explicitly says read-only, stop the save and ask for a writable destination or administrator help; do not change permissions. If the server exposes no permission metadata, do not equate successful reads with write access. Resolve the user-authorized destination, attempt only the requested write, and report an access denial without retrying through another identity or route. Do not create a test document to probe permissions.

For `create_document`, supply a verified `collectionId` or `parentDocumentId`, a separate `title`, and the body as Markdown. Do not start the body with an H1. Use `templateId` only when it came from actual template discovery.

The current tool defaults `publish` to true. For an explicitly requested draft, set `publish: false`; do not confuse an Outline draft's storage state with human agreement. For a request to save/publish in a named collection, use the authorized state and destination. Do not change access or broaden the audience as a side effect. If the intended visibility is ambiguous, clarify before saving.

## Authorized editing

Prefer `update_document` with `editMode: "patch"`, an exact `findText` copied from the freshly fetched Markdown, and replacement `text`. This preserves unaffected rich content and comments. The first match is replaced, so include enough context to uniquely target the intended section.

Use full replacement only when a whole-document rewrite is actually requested and its formatting implications are acceptable. Do not assume the tool provides optimistic locking. Immediately before a consequential patch, fetch again and compare the target excerpt and relevant agreement metadata with the version used to prepare the edit. Reconcile changes before writing. This is a best-effort check, not an atomic lock; use any revision precondition the actual server offers. If content changed or a patch fails, fetch again and reconcile; never repeat a stale replacement blindly.

After creation or editing, fetch the document to verify the content, destination, links, and requested publication state. Return the actual URL and unresolved decisions. On an uncertain write outcome, inspect existing state before retrying to avoid duplicate documents or repeated edits.
