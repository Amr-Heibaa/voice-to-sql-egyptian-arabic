# Contributing — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic

This is the team's official workflow (D-35, approved by the student on 24 Oct 2026). It applies to every human contributor and every AI coding agent. The project rules themselves live in [AGENTS.md](AGENTS.md); this file only describes **how** changes reach `main`.

> **Current stage:** planning documentation only. Implementation is **NOT STARTED** and university registration is **NOT SUBMITTED** ([PROJECT_STATUS.md](PROJECT_STATUS.md)). Do not start coding, generating data or creating infrastructure unless that task has been explicitly authorized.

## 1. The workflow

```text
Feature branch  ->  Pull Request  ->  Human code review  ->  Merge into main
```

1. **Start from the latest `main`:** `git switch main`, `git pull`, then `git switch -c <type>/<short-description>`.
2. **Work on your feature branch only.** Keep each branch to one topic, and keep it short-lived.
3. **Open a pull request** against `main`. Open it as a **draft** while work is in progress, and fill in the [pull request template](.github/pull_request_template.md) completely.
4. **Mark it ready for review** and request a reviewer.
5. **A human reviewer other than the author approves** it, and every review conversation is resolved.
6. **Merge** with *Squash and merge*, then delete the feature branch.

## 2. Rules for `main`

| Rule | How it is enforced |
|---|---|
| No direct pushes to `main`; every change arrives through a pull request | GitHub branch protection (D-35) |
| At least **one approval** from a reviewer **other than the PR author** | GitHub branch protection (GitHub never counts an author's own approval) |
| Approvals are dismissed when new commits are pushed; the PR must be re-approved | GitHub branch protection |
| All review conversations must be resolved before merging | GitHub branch protection |
| No force pushes, no deletion of `main` | GitHub branch protection |
| While the protection is configured, the rules apply to administrators too, with no bypass allowances | GitHub branch protection (`enforce_admins`) |
| No force pushes to shared feature branches either; never rewrite published history | Team rule ([AGENTS.md](AGENTS.md#7-git-and-github)) |
| Required CI checks | **None yet.** They will be added only once a working CI pipeline exists |

The configuration and its verification evidence are in [docs/CHANGE_RECORD_D-35.md](docs/CHANGE_RECORD_D-35.md). The settings were read back through the GitHub API; a real direct-push enforcement test has **not** been performed yet. If `main` ever accepts a direct push, stop and tell the repository owner (`Amr-Heibaa`).

Branch protection is a repository setting. It binds administrators only while it is configured: an administrator (today, the owner) can still change or remove it in the repository settings. Any such change is a team decision recorded with a decision ID, never a way around a review.

If no reviewer is available, **wait**. There is no emergency bypass, and the owner's own pull requests need another collaborator's approval too.

## 3. Branch names

Use `<type>/<short-kebab-description>`, and add the decision ID when there is one:

| Type | Use for | Example |
|---|---|---|
| `docs` | Documentation, status and change records | `docs/d-35-team-workflow` |
| `feat` | New functionality (only once implementation is authorized) | `feat/sales-bir-schema` |
| `fix` | Corrections to existing content or code | `fix/broken-dataset-link` |
| `data` | Synthetic-data generators and dataset tooling (never real data) | `data/synthetic-hr-generator` |
| `eval` | Evaluation harness and analysis | `eval/p2-p4-runner` |
| `spike` | Time-boxed experiments that may be thrown away | `spike/asr-egyptian-arabic` |
| `chore` | Repository maintenance | `chore/update-gitignore` |

Keep names lowercase, use hyphens, and do not include personal data.

## 4. Commits

- Write the subject in the imperative mood, at most about 72 characters (for example `Record D-35: branch protection and team workflow`).
- In the body, say what changed and why, and name the decision (`D-xx`) when there is one.
- Check `git status` and `git diff --staged` before every commit. Never commit anything listed in [AGENTS.md §4](AGENTS.md#4-what-must-never-be-committed).
- To bring your branch up to date, merge `main` into it. Do not rebase a branch that is already pushed.

## 5. Pull requests

- Keep pull requests small and focused on one topic.
- Fill in every section of the template, including the **AI assistance disclosure**.
- Changes to the canonical documents in `docs/` follow the change protocol in [AGENTS.md §5](AGENTS.md#5-change-protocol): proposal first, explicit approval, a change record and a decision ID.
- The PR description must not claim anything is implemented, collected, measured, submitted or approved unless that has been confirmed.

## 6. Code review

**Reviewer**

- Read the whole diff, not only the description. For documentation, check facts against [PROJECT_STATUS.md](PROJECT_STATUS.md) and [docs/SPECIFICATION.md](docs/SPECIFICATION.md).
- Check scope: the official title, the Abstract, the v6 diagram and the marked blocks in `docs/` are unchanged unless the PR is an approved amendment with a change record.
- Check security and data: no secrets, credentials, recordings, participant data, real personal data or third-party datasets.
- Use **Request changes** for anything that must be fixed, and **Comment** for suggestions.
- Aim to respond within 48 hours. If you cannot, say so on the PR so the author can ask someone else.

**Author**

- Reply to every comment, push fixes as new commits and resolve each conversation once it is settled.
- After new commits, ask for a fresh approval (stale approvals are dismissed automatically).
- Merge only after approval, with all conversations resolved.

**Owner sign-off (manual team rule, not enforced by GitHub).** Protected project-governance documentation means the marked blocks in `docs/`, [AGENTS.md](AGENTS.md), [CLAUDE.md](CLAUDE.md), this file and `.github/`.

- **PR authored by another team member** that changes protected project-governance documentation: the repository owner (`Amr-Heibaa`) must review and approve it, by team policy.
- **PR authored by the owner:** the owner's authorization is established by that authorship and the owner's explicit decision. The required GitHub approval must still come from **another human collaborator**.
- **No self-approval:** an author can never satisfy the required GitHub approval by approving their own PR.
- This is a manual team rule. It is **not** an enforced CODEOWNERS requirement; the repository has no CODEOWNERS file.

## 7. AI coding agents

AI agents (Claude Code, Codex, ChatGPT, Copilot and others) are welcome as assistants. **The human who opens the pull request is responsible for every line in it, whether a person or an AI wrote it.**

1. Agents follow [AGENTS.md](AGENTS.md) and [CLAUDE.md](CLAUDE.md). An agent works only on a feature branch, never pushes to `main`, never force-pushes and never rewrites published history.
2. Agent output is a draft. The author reads and understands the whole diff before asking for review, and must be able to explain it.
3. **An agent never approves or merges a pull request.** AI review comments are advisory; the required approval must come from a human collaborator other than the author.
4. An agent acting through your GitHub account acts as you: a pull request it opens is yours, and you are its author for review purposes.
5. Disclose AI assistance in the pull request template: which tool, and which parts it produced.
6. Never paste secrets, credentials, recordings, participant data, real personal data or restricted third-party datasets (for example AMBROSIA, Casablanca or AraSpider content) into an AI tool.
7. Agents do not change [AGENTS.md](AGENTS.md), [CLAUDE.md](CLAUDE.md), this file, `.github/`, repository settings or collaborator permissions unless a human explicitly asked for that specific change.
8. Agents must not invent results, approvals, dataset counts or test evidence (AGENTS.md rule 10).

## 8. Questions

Ask in the pull request or the team channel. If two current documents disagree, stop and report the conflict instead of choosing silently ([AGENTS.md §1](AGENTS.md#1-read-first-in-this-order)).
