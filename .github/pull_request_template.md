> **How to use this checklist.** Every checkbox is a personal attestation. The **PR author** ticks the author sections; the **human reviewer** ticks the reviewer checklist. An AI agent may draft this description, but it must **not** tick human attestation boxes. Checkboxes never replace GitHub's required formal approval (**Review changes → Approve** by a human collaborator other than the author).

## Summary

<!-- What does this pull request change, and why? One short paragraph. -->

**Jira issue:** <!-- e.g. CQP-26, or "none" -->

**Decision:** <!-- e.g. D-38, or "none" -->

**Type:** <!-- docs | feat | fix | data | eval | spike | chore -->

## Scope

- [ ] This PR covers one topic and matches its branch name (`<type>/<short-description>`).
- [ ] The official title, the Abstract, the v6 diagram and the marked blocks in `docs/` are unchanged, **or** this PR is an approved amendment with a change record and decision ID.
- [ ] The V3.1 scope is not dropped, downgraded or expanded (`AGENTS.md` rule 4).
- [ ] Nothing is described as implemented, collected, measured, submitted, registered or committee-approved unless that has been confirmed.
- [ ] No implementation, data generation or infrastructure work unless that task was explicitly authorized.

## Changed files and deliverables

<!-- List every changed file and, if this PR delivers a Jira artifact, which one. -->

## Known limitations

<!-- What is incomplete, untested or deferred? Write "none known" only if that is true. -->

## Testing and verification

<!-- What did you run or check, and what was the result? Paste the commands and a short summary of the output. Write "documentation only" if nothing could be run. -->

- [ ] I ran the relevant checks and described the results above.
- [ ] Links and file references in changed documents point to files that exist.

## Documentation

- [ ] `PROJECT_STATUS.md`, `PROJECT_EVOLUTION.md` and the indexes are updated if this PR changes status or adds a decision.
- [ ] Repository documents are in English; terms follow `AGENTS.md` §6.

## Security and data

- [ ] I checked `git status` and the full diff before committing.
- [ ] No secrets, credentials, tokens, connection strings or `.env` files.
- [ ] No voice recordings, consent forms, participant data or real personal or employee data.
- [ ] No downloaded third-party datasets, archives or backups (`AGENTS.md` §4).

## Owner merge authorization

Merging needs GitHub's required approval **and** the project owner's (`Amr-Heibaa`) explicit authorization in a pull request comment. Link that comment here when it exists; nobody, human or AI, writes it on the owner's behalf.

**Owner authorization:** <!-- link to the owner's comment, or "not yet given" -->

## AI assistance disclosure

Select **exactly one** of these two options (a factual disclosure, not an attestation):

- [ ] No AI tool was used for this PR.
- [ ] An AI tool was used, as described below.

**Tool(s):** <!-- e.g. Claude Code, Codex, ChatGPT, Copilot -->

**What the AI produced:** <!-- which files or parts -->

To be ticked by the responsible human author, never by an AI agent:

- [ ] I read and understood every AI-generated line and take responsibility for it.
- [ ] No secrets, personal data or restricted datasets were shared with the AI tool.

## Reviewer checklist (human reviewer only)

For the human reviewer, not the author and not an AI agent. Ticking these boxes does not approve the PR; the approval is GitHub's formal **Approve** review.

- [ ] I read the whole diff, not only this description.
- [ ] Facts match `PROJECT_STATUS.md` and `docs/SPECIFICATION.md`.
- [ ] Scope, security and data checks above are correct.
- [ ] I am not the author of this PR.
