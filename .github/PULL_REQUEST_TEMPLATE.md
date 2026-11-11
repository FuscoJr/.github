## What and why

Link Refs #N, or Closes #N only when the whole issue is fulfilled. Describe the problem and the observable result.

## Scope, decisions and reuse

Explain the main decisions, existing code/tests/tools reused, and why any new code or dependency is needed. State exclusions and any scope decision agreed with the maintainer.

## Review map and impact

Point to the important changed files or sections and explain what to inspect. Highlight changes to authentication, permissions, data, dependencies, CI or deployment where present. Keep the diff small enough to review; split unrelated work.

## Verification evidence

| Behaviour or requirement | Check / command | Actual result | Limit or pending check |
|---|---|---|---|
| | | | |

For a bug fix, state how the check detected the original failure and passed after the fix, or explain why that evidence is unavailable. Identify relevant existing checks run and checks not run. An unrelated green CI run does not validate this change. Documentation-only changes need appropriate content/form/reference checks.

## Related findings and handoff

Link existing issues, necessary sub-issues and independent Backlog findings. State blockers, remaining work and the next action. Recording a finding does not authorise implementing it.

Record the implementation owner, task branch, integration base and workspace/worktree label (no personal absolute paths in public records).

## Maintainer review

- [ ] Scope, acceptance and important decisions understood.
- [ ] Relevant diff and verification evidence reviewed, including limitations.
- [ ] Data/security/publication impact considered where applicable.
- [ ] Outstanding findings and required human QA resolved or explicitly accepted.

The maintainer performs the merge. Agents must not merge or enable auto-merge.
