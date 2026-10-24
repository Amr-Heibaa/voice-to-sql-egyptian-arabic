# Change Record D-34 — GitHub Collaborator Status Recorded

| Field | Value |
|---|---|
| Decision | **D-34** |
| Date | 2026-10-24 |
| Authorized by | The student, in the D-34 instruction (24 Oct 2026), after Claude reported that the live collaborator list no longer matched "owner only" |
| What this records | The repository's **actual** collaborator and invitation state, read from the GitHub API on 24 Oct 2026 at 14:27 UTC. Nothing was changed on GitHub: no invitation was sent, accepted, revoked or edited, and no permission was modified |
| Repository | https://github.com/Amr-Heibaa/voice-to-sql-egyptian-arabic (**PRIVATE**) |
| Impact | Documentation only. The title, Abstract, scope, datasets, architecture and evaluation documents are unchanged. University registration remains **NOT SUBMITTED** |

## Collaborator status (as read from GitHub, 24 Oct 2026, 14:27 UTC)

**Active collaborators: 1 owner + 3 with write access**

| GitHub account | Status | Role |
|---|---|---|
| `Amr-Heibaa` | Repository owner | admin |
| `sayeddabdou` | Active collaborator | write |
| `selimmmm7` | Active collaborator | write |
| `abdallahjr111` | Active collaborator | write |

**Pending invitation: 1 (not yet accepted, so no access yet)**

| GitHub account | Status | Permission offered | Invited by | Created |
|---|---|---|---|---|
| `GeorgeBassem-dev` | Invitation pending, not expired | write | `Amr-Heibaa` | 2026-10-23 20:58:20 UTC |

All invitations were sent from the owner account `Amr-Heibaa`, outside Claude's actions. The dates on which the three active collaborators accepted are not available from the collaborator API, so they are not recorded here.

## Relationship to D-32 (history preserved)

[CHANGE_RECORD_D-32.md](CHANGE_RECORD_D-32.md) states "owner only; no invitations". That was **accurate when it was verified**: the D-32 checks ran just before the D-32 commit `d1ee34e` (2026-10-23 20:50:59 UTC), and the only invitation with a known timestamp was created later, at 20:58:20 UTC. D-32 is left unchanged as a historical record; this record supersedes it for the **current** collaborator status only.

## Files changed by D-34

- `PROJECT_STATUS.md`: GitHub repository row, a new collaborator row and the next-steps line.
- `PROJECT_EVOLUTION.md`: timeline row, decision-index row; the next decision is **D-35**.
- `AGENTS.md`: next decision number (D-35).
- `README.md` and `docs/README.md`: index entries for this record.
- This record.

No canonical document block (specification, architecture, dataset strategy, evaluation plan, registration fields) was edited.
