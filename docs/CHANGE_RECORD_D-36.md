# Change Record D-36 — Repository Visibility Changed from Private to Public

| Field | Value |
|---|---|
| Decision | **D-36** |
| Date | 2026-10-24 |
| Authorized by | The repository owner (`Amr-Heibaa`), in the public-conversion instruction of 24 Oct 2026, conditional on a public-release audit; then, after the audit reported one privacy point (§3), the owner's explicit confirmation to proceed without rewriting history |
| What this records | The change of the **existing** repository from **PRIVATE** to **PUBLIC**, the API evidence for it, the audit before it, and the branch protection after it |
| Repository | https://github.com/Amr-Heibaa/voice-to-sql-egyptian-arabic (**PUBLIC** since 24 Oct 2026) |
| Impact | Repository visibility and documentation only. The title, Abstract, specification, architecture, datasets, evaluation plan, registration fields and v6 diagram are unchanged. University registration remains **NOT SUBMITTED**; implementation remains **NOT STARTED**; no dataset has been generated |

## 1. What changed

- Visibility of the existing repository: **PRIVATE → PUBLIC**.
- Changed by Claude Code, at the owner's request, through the owner's authenticated GitHub CLI session (`gh repo edit --visibility public`). The command succeeded at about **16:48 UTC on 24 Oct 2026**.
- Unchanged: repository name, URL, owner, default branch (`main`), collaborators and their permissions, the pending invitation, and the branch protection on `main`.
- No commit was created, nothing was pushed, and the Git history was **not** rewritten. Billing and plan were not changed. No LICENSE file was added.

## 2. Verification evidence

All reads were made through the GitHub API with the owner's account on 2026-10-24.

| Check | When (UTC) | Result |
|---|---|---|
| `GET /repos/{owner}/{repo}` before the change | Just before 16:48 | `visibility: private`, `private: true` |
| `GET /repos/{owner}/{repo}` after the change | Right after the change, and again at 17:02:43 | `visibility: public`, `private: false`; default branch `main` |
| GraphQL `repository { visibility isPrivate }` | Right after the change, and again at about 17:02 | `visibility: PUBLIC`, `isPrivate: false` |
| Same `GET /repos/{owner}/{repo}` **without authentication** | After the change | HTTP 200, `visibility: public` (readable by anyone) |
| `GET /repos/{owner}/{repo}/branches/main` | Right after the change, and again at about 17:02 | `protected: true`; head `659184d794d6df59f0f722d6250fb4bc2b254468` |
| `GET /repos/{owner}/{repo}/branches/main/protection`, before and after | Just before and right after the change | The two JSON responses are **identical** |
| `GET /repos/{owner}/{repo}/collaborators` and `/invitations`, before and after | Just before and after the change | Identical: owner (admin), 3 collaborators with write access, 1 pending invitation (the D-34 state) |
| `git ls-remote` and `git rev-list` | After the change | Branch `main` at `659184d`, 7 commits, tree unchanged; the only other ref is GitHub's `refs/pull/1/head` (`b1f03f0`, already in `main`) |
| Pull request #1 | After the change | Still **MERGED** (merge commit `659184d`) |
| Documentation verification suite on an export of `main` | After the change | 102 PASS, 0 FAIL |

## 3. Public-release audit before the change

Run on 24 Oct 2026 before the visibility change, over every tracked file **and every version of every file in the reachable history** (7 commits; 50 file versions), not only the latest tree.

| Area | Result |
|---|---|
| Credentials (API keys, tokens, private keys, passwords, connection strings) | None found |
| E-mail addresses, phone numbers and local machine paths inside file contents | None found |
| Voice recordings, consent records, participant or personal data | None; none exist yet |
| Third-party datasets | Referenced by link only; none included or redistributed |
| The v6 PNG | No embedded text metadata (only image chunks) |
| Releases, tags, GitHub Actions runs, workflows, artifacts, secrets and variables | None |
| Webhooks, deploy keys, environments | None |
| Push history (GitHub activity log) | Normal pushes, one pull-request merge and one branch deletion; no force push |
| Pull request #1 | Description and one approval without comments; nothing sensitive |
| **Commit metadata** | Author and committer names and the e-mail addresses configured in Git are part of every commit and are now public. These are institutional addresses of two contributors. The owner accepted this and reported that the other contributor whose address appears consented to the publication of the existing commit metadata. The addresses are deliberately **not** reproduced in this record |

The audit found no secret or restricted material. The commit-metadata point was reported to the owner before any change, and the visibility was changed only after the owner's explicit confirmation. A verified backup (a Git bundle of the full history) was made outside the repository before the change.

## 4. Branch protection after the change

Re-read after the change; identical to the configuration recorded in [D-35](CHANGE_RECORD_D-35.md):

| Rule | GitHub setting | Value after the change |
|---|---|---|
| Pull request required before merging | `required_pull_request_reviews` | Enabled |
| Approvals from someone other than the author | `required_approving_review_count` | `1` |
| Dismiss stale approvals | `dismiss_stale_reviews` | `true` |
| Review conversations resolved | `required_conversation_resolution` | `true` |
| Rules apply to administrators | `enforce_admins` | `true` |
| Force pushes | `allow_force_pushes` | `false` (blocked) |
| Branch deletion | `allow_deletions` | `false` (blocked) |
| Bypass, force-push and push allowances | GraphQL allowance counts | 0, 0, 0 |
| Required CI checks | `required_status_checks` | None |
| Rulesets | `/rulesets`, `/rules/branches/main` | None |

GitHub documents protected branches on public repositories as available on every plan, including GitHub Free, so this protection no longer depends on a paid plan. The plan name itself was still not read.

**Still not tested:** no push to `main` was attempted. The protection is **CONFIGURED and API-VERIFIED**; GitHub has not yet been observed rejecting a direct push, a force push or a deletion.

## 5. Remaining public-disclosure risks

1. **Permanent exposure.** Anyone can now clone or fork the repository. Making it private again would not remove copies that already exist.
2. **Commit metadata** of existing commits (names and configured e-mail addresses) is public, as accepted in §3. Contributors should configure GitHub's private no-reply address before future commits.
3. **Planning documents are public before registration:** the research plan, the final registration-form text and the evaluation design can be read by anyone while registration is still **NOT SUBMITTED**.
4. **No license.** Public visibility grants no license. Under GitHub's Terms of Service others can view and fork the repository on GitHub; no other permission to use, copy, modify or distribute the materials is given, and licensing and ownership remain undecided.
5. **Collaboration history is public:** pull request #1, its review, and the collaborator account names listed in [D-34](CHANGE_RECORD_D-34.md).
6. **Administrator control.** An administrator can still change the protection or the visibility in the repository settings; such a change must be a recorded team decision.
7. **Repository description.** The GitHub repository description still uses the earlier title *Voice-to-SQL in Egyptian Arabic*, not the official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*. Repository metadata was not changed by D-36.

## 6. Historical records kept as they are

[D-32](CHANGE_RECORD_D-32.md), [D-34](CHANGE_RECORD_D-34.md) and [D-35](CHANGE_RECORD_D-35.md) describe the repository as **PRIVATE**. That was correct when each was recorded, so they are not changed. From D-36 on, the current visibility is **PUBLIC**; [PROJECT_STATUS.md](../PROJECT_STATUS.md) is the live status.

## 7. Files changed by D-36

- This record (new).
- `PROJECT_STATUS.md`: repository row (PUBLIC), branch-protection row (re-read after the change), license row, next-steps line.
- `PROJECT_EVOLUTION.md`: timeline row and decision-index row; the next decision is **D-37**.
- `AGENTS.md`: §5 next decision (D-37); §7 describes the public repository and its rules.
- `README.md`: the repository note, the license section and an index entry.
- `docs/README.md`: an index entry.

## 8. Open items

1. Update the GitHub repository description to the official title (repository metadata; needs a separate instruction).
2. A controlled enforcement test of the branch protection (needs separate approval; carried over from D-35).
3. Each contributor: switch the Git commit e-mail to GitHub's private no-reply address.
4. Decide on licensing and ownership (no license until the team decides).
