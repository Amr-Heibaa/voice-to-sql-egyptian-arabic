# Change Record D-35 — Branch Protection on `main` and Team Workflow

| Field | Value |
|---|---|
| Decision | **D-35** |
| Date | 2026-10-24 |
| Authorized by | The student, in two D-35 instructions (24 Oct 2026): (1) configure protection on `main` if the GitHub plan supports it; (2) approval of the proposed team workflow and of this documentation pull request |
| What this records | (a) The branch protection configured on `main` and the API evidence that GitHub stores it; (b) the team workflow in [CONTRIBUTING.md](../CONTRIBUTING.md) and the pull request template `.github/pull_request_template.md` |
| Repository | https://github.com/Amr-Heibaa/voice-to-sql-egyptian-arabic (**PRIVATE**) |
| Protection status | **CONFIGURED and API-VERIFIED.** A real enforcement test (an attempted direct push, force push or deletion that GitHub rejects) **has NOT been performed** |
| Impact | Repository workflow and documentation only. The title, Abstract, specification, architecture, datasets, evaluation plan and v6 diagram are unchanged. University registration remains **NOT SUBMITTED**; implementation remains **NOT STARTED** |

## 1. Branch protection configuration

The protection was applied by Claude Code, at the student's request, through the repository owner's authenticated GitHub CLI session (account `Amr-Heibaa`). It uses GitHub's classic branch protection on the branch `main`; no repository rulesets exist.

- Request: `PUT /repos/Amr-Heibaa/voice-to-sql-egyptian-arabic/branches/main/protection`
- Response: **HTTP 200 OK**, 2026-10-24 14:33:55 UTC (response `Date` header)
- Before the change (read the same day): `main` reported `protected: false`, branch protection returned `404 Branch not protected`, and the rulesets list was empty.

| Requested rule | GitHub setting | Effective value |
|---|---|---|
| Require a pull request before merging | `required_pull_request_reviews` present | Enabled |
| At least one approval from someone other than the PR author | `required_approving_review_count` | `1` (GitHub never counts the author's own approval) |
| Dismiss stale approvals after new commits | `dismiss_stale_reviews` | `true` |
| Require resolution of review conversations | `required_conversation_resolution` | `true` |
| Prevent direct pushes | Pull request required for everyone, including administrators | Enabled; no push allowances |
| Block force pushes | `allow_force_pushes` | `false` |
| Block branch deletion | `allow_deletions` | `false` |
| Disable admin bypass | `enforce_admins` | `true`; bypass allowances: 0 |
| Do not require CI checks yet | `required_status_checks` | None |

Left disabled because they were not requested: code-owner reviews, approval of the most recent push by someone else (`require_last_push_approval`), signed commits, linear history, branch lock and fork syncing. Push restrictions by user or team exist only for organization repositories and are not needed here.

## 2. Verification evidence

All reads below were made through the GitHub API with the owner's account on 2026-10-24.

| Check | Time (UTC) | Result |
|---|---|---|
| `GET /repos/{owner}/{repo}` | 14:44:26 | `visibility: private`, `private: true` |
| `GET /repos/{owner}/{repo}/branches/main` | ≈14:34 (right after the change) and 14:44:26 | `protected: true`; head `540eb50fb61de5b42414c006b6341c45b5aa06d7` |
| `GET /repos/{owner}/{repo}/branches/main/protection` | ≈14:34 (right after the change) and 14:44:26 | Every value in the table in §1 |
| GraphQL `repository.branchProtectionRules` | ≈14:34 (right after the change) and 14:44:26 | Exactly 1 rule, pattern `main`: `isAdminEnforced: true`, `requiresApprovingReviews: true`, `requiredApprovingReviewCount: 1`, `dismissesStaleReviews: true`, `requiresConversationResolution: true`, `allowsForcePushes: false`, `allowsDeletions: false`, `requiresStatusChecks: false`; bypass pull request, bypass force push and push allowances all 0 |
| `GET /repos/{owner}/{repo}/rulesets` and `/rules/branches/main` | ≈14:34 (right after the change) and 14:44:26 | Empty: no rulesets apply |

**GitHub plan.** The plan name could not be read, because the CLI token has no `user` scope. GitHub documents protected branches on private repositories as a feature of paid plans (GitHub Pro, Team or Enterprise). GitHub accepted and stored this rule, so the capability is available on this account. No billing, plan or visibility setting was changed.

**Not yet verified.** No push to `main` was attempted, so GitHub has not yet been observed rejecting a direct push, a force push or a deletion. "API-verified" means GitHub stores and reports these settings; it does not mean their enforcement was tested. A controlled enforcement test needs the student's separate approval and must not risk changing `main`.

## 3. Consequences

- Nobody, including the owner, can push directly to `main`. Every change, including this record, reaches `main` through a pull request approved by a collaborator other than its author.
- Reviewers available today with write access: `sayeddabdou`, `selimmmm7` and `abdallahjr111`. `GeorgeBassem-dev` has a pending invitation (D-34) and can review once it is accepted.
- An approval is dismissed when new commits are pushed, so the final version of a pull request is always the version that was approved.

## 4. Team workflow

Approved by the student on 24 Oct 2026 and documented in:

- [CONTRIBUTING.md](../CONTRIBUTING.md): feature branch → pull request → human code review → merge; branch names; commits; review duties; rules for AI coding agents (the human author is responsible for all AI-generated content, and an agent never approves or merges).
- `.github/pull_request_template.md`: checklists for scope, testing, documentation, security and data, AI assistance disclosure, and the reviewer.

## 5. Not changed

- Collaborators, permissions and invitations (the state recorded in D-34 was re-read at 14:44 UTC and is unchanged).
- Repository visibility (still private), billing and plan.
- Every canonical document in `docs/` (specification, architecture, dataset strategy, evaluation plan, registration fields) and every marked block; the Abstract; the v6 diagram.
- Registration status (**NOT SUBMITTED**) and implementation status (**NOT STARTED**).

## 6. Files changed by D-35

- `CONTRIBUTING.md` (new).
- `.github/pull_request_template.md` (new).
- This record (new).
- `PROJECT_STATUS.md`: a new branch-protection row and the next-steps line.
- `PROJECT_EVOLUTION.md`: timeline row, decision-index row; the next decision is **D-36**.
- `AGENTS.md`: §7 now points to the protected-branch workflow; next decision number (D-36).
- `README.md` and `docs/README.md`: index entries.

## 7. Open items

1. A controlled enforcement test of the protection (needs separate approval).
2. Optional extra rules: `require_last_push_approval`, a CODEOWNERS file so the owner sign-off in CONTRIBUTING.md §6 is enforced, squash-only merging, and automatic deletion of merged branches.
3. Confirming the GitHub plan name from the account's billing page.
