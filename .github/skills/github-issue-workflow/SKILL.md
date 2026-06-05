---
name: github-issue-workflow
description: 'Document commits and synchronize GitHub issues with work already done in the repo. Use when reviewing pending changes, writing well-documented commit messages, commenting on issues, closing resolved issues, updating next-step issues, and keeping repo docs and GitHub state aligned. Keywords: gh issue, commit documentation, close issue, comment issue, traceability, backlog, workflow.'
argument-hint: 'Describe the repo state or the issue range to review and synchronize.'
user-invocable: true
---

# GitHub Issue Workflow

## When to Use
- A change is already implemented or documented in the repo, but the related GitHub issue is still open.
- Commits are too generic and need a clearer message before push.
- The repo backlog and GitHub issue state have drifted apart.
- You need to leave an operational comment on the next issue before starting it.

## Goal
Keep three things aligned:
- the Git history
- the repo documentation
- the real state of GitHub issues

## Procedure
1. Verify the real repository target first.
   Run `git remote -v` and confirm owner and repo before any GitHub operation.

2. Inspect local repository state.
   Review `git status --short`, the relevant diff, and the recent commit history.

3. Inspect issue state in GitHub.
   Prefer `gh issue view <n> --repo <owner/repo> --json number,title,state,body,url`.
   In repositories where the default `gh issue view` fails because of deprecated Projects classic fields, do not use the default output.

4. Compare issue criteria with the actual repo contents.
   Confirm whether the acceptance criteria are already covered by code or docs.
   Do not treat an issue as closed only because the work exists locally.

5. Fix repo traceability if needed.
   Update docs so they clearly distinguish:
   - historical backlog items
   - resolved items
   - true pending work

6. Create a documented commit.
   Use a commit subject that states the real outcome.
   In the commit body, include:
   - what was delivered
   - which issues are affected
   - which files or documents carry the evidence

7. Push before closing issues.
   Issue comments should point to content that already exists on GitHub.

8. Comment and close only what is actually done.
   For each resolved issue, leave a comment that states:
   - what was delivered
   - where it is documented or implemented
   - why the acceptance criteria are covered
   Then close the issue.

9. Update the next issue.
   Leave a comment on the next active issue with the current starting point and dependencies already resolved.

10. Verify the final state.
   Confirm clean working tree, pushed commit, and the final state of each touched issue.

## Rules
- Never assume an issue is closed in GitHub because the repo says it is resolved.
- Never operate on GitHub until the remote has been verified.
- Prefer precise issue comments over generic closure notes.
- If a backlog section mixes resolved and pending work, fix the document before continuing.

## Outputs
A successful run should leave:
- a documented commit in Git
- pushed changes on the right remote
- closed issues for completed work
- a comment on the next issue with current context

## References
- [Templates](./references/templates.md)
