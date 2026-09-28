# GitHub authorship, privacy, and staged releases

**Verified connector capability on 24 Sep:** linked GitHub can list `ihatecodingaaa`'s existing private repos. There is no demonstrated repo-creation action in the available connector. Have Lucas create a new private repo through his authenticated local `gh` CLI or GitHub UI; no collaborator invites are needed for ChatGPT/Claude to use his own authorization, but new repo must be visible to ChatGPT connector. Existing repositories are NOT to be repurposed.

## One-time **owner-run** creation (only after Lucas approves the intended repo name)

PowerShell in `C:\Users\lucas\Projects\dark-factory` **after extracting only approved docs**:

```powershell
# Verify current owner first, don't paste secrets in chat
gh auth status
# Have Claude *inspect* git author identity; configure with Lucas's verified GitHub email
git config --global --get user.name
git config --global --get user.email
# Only if directory is not already a git repository
git init -b main
git add README.md CLAUDE.md competition docs experiments mandates operations ux .gitignore
git diff --cached --check
git commit -m "docs: establish pre-kickoff research and mandate baseline"
gh repo create ihatecodingaaa/outcome-factory --private --source . --remote origin --push
# Verify remote owner and visibility in the GitHub UI; verify ChatGPT connector sees it.
```

**No AI co-author trailer:** forbid `Co-authored-by:` and `Signed-off-by:` trailers from agent templates unless Lucas explicitly requests otherwise. Validate `git log -1 --format=full` and `.mailmap` if later used. Git author metadata is distinct from disclosing AI assistance to hackathon judges; report that accurately.

**Commit identities:** Lucas's own commits use his verified identity. Seat commits use the seat's own identity, set per commit as `CLAUDE.md` and `operations/BAND_RUNBOOK.md` specify, e.g. `git -c user.name="developer-x7jj (agent seat)" -c user.email="developer-x7jj@seats.dark-factory.invalid" commit …`; the organizer guide likewise says to configure Git names and emails for each seat. Never rewrite seat commits to change their authorship.

**No secrets:** `.gitignore` includes `.env*`, credentials and research transcripts with secrets. Example `.env.example` may contain placeholders only. Commit scans and `git diff --cached --check` before every push. Do not store any AWS/Nebius promo code, BAND invite token, account number or password in repo.

## Amazon

Private GitHub repo allowed, but grant **required six Amazon GitHub reviewers and Devpost** access near submission, check accepted invitations before closing; seven-day invitations expire. Judge-only read access to source is a tournament obligation, **not** a Git co-author. Use official Amazon FAQ for exact current roster. Preserve a frozen tag and demo accessibility through the judging period.

## Nebius

Current rules require public, fully runnable, licensed code. Maintain canonical private development repo and create a separate **sanitized but complete** public submission repo/mirror from a frozen release, including exact source, license, test assets and setup. Check rights/licensing of dependencies and demo media. Sanitization cannot remove required functionality. If source cannot be released, don't claim Nebius eligibility.
