# Shared contribution workflow

## Purpose and ownership

This is the shared workflow for repositories that adopt it. Issues and repository files are the durable record; chats help explain and carry out the work. Read the target repository's local instructions for architecture, branch strategy, verification commands and publication boundaries.

The maintainer chooses priorities, approves acceptance criteria and architectural decisions, reviews the result and performs merges. Codex or Claude may investigate, implement the agreed scope, run checks and open a pull request. Agents must never merge pull requests or enable auto-merge.

## Before work starts

1. Read the target repository's README, local contribution/agent instructions and this shared guide. Do not assume instructions from another repository apply unchanged.
2. Confirm the repository, working directory, branch, current commit and local changes. Preserve unrelated work.
3. Read the issue, linked decisions, dependencies and existing tests. Do not assume a chat describes the current state.
4. Agree on the outcome, scope, exclusions, acceptance criteria and verification approach. Record unresolved decisions in the issue.
5. Choose one implementation owner and record the issue, task branch, integration base and workspace/worktree label. Coordinate overlap before concurrent work.

Keep planning proportional to the task. For small tasks, a concise issue or PR description is sufficient; reuse and link information already recorded rather than repeating it in another checklist, form or status document. This does not remove the need for clear scope, suitable verification or maintainer review.

Tests and CI can be part of the delegated task; the maintainer does not have to write every test before implementation. Check the intended behaviour with the maintainer when it is unclear.

## Findings and sub-issues

The maintainer may draft an issue directly or ask an agent to turn an objective into a proposed issue. Agree the outcome and scope before implementation; the maintainer does not have to prescribe every implementation step.

When work reveals another concern, search existing issues and code first:
- Necessary within the agreed task: document it and address it within scope. Ask before depending on a significant scope expansion or unresolved decision.
- Separable work required for the same larger outcome: use a sub-issue with its own acceptance criteria.
- Independent defect or improvement: create or propose a linked Backlog issue within the authorised repository/planning scope, rather than making it a child solely because it was discovered here.
- Existing issue: link or update it instead of creating a duplicate.

Record evidence, impact and whether the finding blocks the current task. Do not present speculative improvements as confirmed defects. Creating or linking an issue does not authorise its implementation. Record a blocker and seek a decision when the current task cannot continue within its agreed scope. Keep sensitive security details out of public reports.

## Issues and Projects

Use a task for a defined outcome and a bug report for an observed defect. Keep titles descriptive; commit prefixes such as feat: or fix: are not required in issue titles.

| Status | Meaning |
|---|---|
| Backlog | Recorded work that needs prioritisation, a decision or more detail. |
| Ready | Scope and acceptance are clear enough to begin; dependencies are understood. |
| In Progress | Work has started and remains active, even if another task is the current session's focus. |
| In Review | A concrete result is ready for maintainer review or required validation. |
| Done | Work is completed and its acceptance criteria are fulfilled. |
| Cancelled | Work was explicitly abandoned or declined; retain the issue and its recorded reason, and close it as not planned. |

The Review column, where present, has the same meaning as In Review. A started task may remain In Progress across sessions. Record its next step and blockers rather than pretending it is complete or moving it back solely because it is not today's focus. Select a small focus for each session; avoid two implementers editing the same task.

Keep Cancelled items visible in a dedicated Project column for future reference. Record the cancellation reason in the issue, with a replacement issue link when relevant, rather than duplicating it in a separate document. Work deferred for later stays in Backlog. If cancelled work is resumed, reopen the issue, reassess its scope and acceptance criteria, and select the appropriate status. Ready indicates planning readiness, not permission for an agent to start independently.

Use bug, documentation, enhancement and maintenance for type; add security where relevant. Labels are repository metadata and are not inherited with these templates; check they exist before relying on automatic form labels. Use a Project field for priority when needed; do not duplicate every status as a label. Security findings must not expose credentials or private client data in public issues.

A milestone groups work for an agreed, concrete delivery. It is not a release and needs no invented deadline. Publish a release only for an explicitly approved, validated version. No automated releases, deployments or merges are introduced by this guide.

## Branches, worktrees and ownership

Follow the target repository's documented integration base and merge strategy. Use a short-lived task branch such as type/issue-number-short-description; this applies to maintainer and agents alike. Do not commit directly to its protected/integration or production branch. A permanent dev branch is optional and must serve the repository's documented integration or publication needs.

Before editing, record the issue, implementation owner, task branch, workspace/worktree and integration base in the issue or PR. Do not publish personal absolute paths; use a workspace label or relative path in public records.

A branch is a line of changes. A worktree is another working directory of the same repository with its own checkout and index; it shares repository data and refs. It is not a security boundary, backup or automatic conflict prevention.

- Simultaneous implementers need separate branches and worktrees/checkouts. Do not share a working directory or task branch while editing.
- Check the current commit, base and local changes before starting or handing off. Do not switch/reset another implementer's workspace.
- Check for overlapping files or dependencies. Coordinate order or split ownership before editing shared areas.
- Use a separate worktree for concurrent work; ordinary single-task work does not require creating one mechanically.
- Preserve uncommitted work. Never remove a worktree or delete a branch before checking its pending work and obtaining the required cleanup authorization.

Inspect the diff and stage only task files. Use focused English commits with an issue reference. Push the task branch and open a PR against the agreed integration branch. Use a draft while work or required validation is pending.

## Pull request review

Keep each PR focused and small enough to understand. Split unrelated changes and defer optional refactors rather than asking the maintainer to approve an unreviewable diff.

The PR must explain the problem and observable result, scope, decisions and reuse, a short map of the important changed files, verification evidence, unresolved findings and risks/publication effects. The review map directs attention to important changes; it does not replace reading the relevant diff.

Use Closes #N only when the PR fulfils the whole issue; otherwise use Refs #N and state what remains. Link the PR from the issue and keep its Project item current rather than creating duplicate tracking cards.

Review authentication, permissions, secrets/data handling, dependencies, CI and deployment changes with particular care. Agent explanations and a second agent's review can help; neither is independent proof of correctness. Ask for clarification or split the change if it cannot be understood sufficiently for a merge decision.

The maintainer reviews and merges using the repository's agreed strategy. Agents never merge or enable auto-merge. Before integrating another task, reassess the combined changes and run relevant checks; separate worktrees do not remove this need.

Do not delete branches/worktrees, rewrite shared history, change visibility, archive repositories or touch external services without the required explicit authorization.

## Verification and review

Verification is proportional to behaviour, risk and the type of change. Before adding code, tests or tooling, inspect the existing implementation, test suite and commands. Reuse or extend suitable checks and established tools rather than duplicating them. New dependencies or layers need a concrete benefit that outweighs their maintenance cost.

For each relevant behaviour change:
1. State the expected outcome and failure modes from the issue, not just the current implementation.
2. Decide what must be checked: normal behaviour, relevant boundaries, invalid input, error paths and integrations. Prioritise cases by impact; do not add a test for every implementation detail.
3. Extend an existing test when appropriate, or add a focused test for the uncovered risk.
4. Demonstrate that the check detects the intended failure. For a bug, prefer reproducing it on the unfixed version and passing on the fix; if that cannot be done, explain the limitation and the evidence used.
5. Run the relevant existing checks as well, and record actual results and checks not run.

Keep tests aligned with changes in requirements, interfaces and discovered regressions. Update or remove obsolete/duplicated checks when justified; do not weaken assertions or delete a failing test just to obtain a green run. A simple independent expected result is stronger than repeating the implementation in the test. Add or improve CI when repeatability belongs to the task; do not add a new tool if existing checks already meet the need.

Documentation-only work needs content, references, scope and diff checks. UI, accessibility, integration and security behaviour may require additional manual or specialised validation. Pursue the smallest maintainable solution that gives useful evidence, not a test count or coverage percentage.

A green check only proves the configured checks passed. It is not proof of correctness or absence of silent failures, and unrelated checks do not validate the changed files. Do not claim compilation proves UI behaviour, an automated review replaces human acceptance, or an instruction file enforces a security boundary.

Read the target repository's instructions for available checks. Do not invent commands, install a framework or assume the same CI applies across repositories. Record missing checks as limitations or agreed follow-up work.

Before merging, the maintainer checks acceptance, relevant checks and actual results, unresolved review comments, scope and any deployment effect. Repository rules may not enforce these conventions; do not claim they do.

## Session handoff

Update the issue or PR when there is meaningful progress, a blocker or a handoff. Record:
- What is complete and the issue, owner, task branch/PR, integration base and workspace/worktree label.
- Checks run and their results; unverified requirements.
- Open decisions, blockers and the next concrete action.

Keep durable technical decisions in the repository and link them. Do not copy transcripts or create parallel status documents. Use fictitious data in examples and screenshots.

## After review

The maintainer merges; then verify the default-branch result, issue closure and Project state. Set Done only for completed work. Work explicitly abandoned or declined belongs in Cancelled, with the reason recorded in the issue and closure as not planned; this does not mean its criteria passed. Do not check off unfinished criteria. Check that Project automation does not move every closed issue to Done regardless of its closure reason. Clean up task branches only with authorization.

## Adoption and limits

GitHub uses the supported default contribution files and issue/PR templates from this account's public .github repository when a target repository has no corresponding local override. A local ISSUE_TEMPLATE directory with valid forms/config replaces the shared issue-template set; templates are not merged automatically. Local PR templates also take precedence.

These default files are not copied into clones. AGENTS.md is not an account-wide inherited instruction file. Each active repository needs a short local entry point that tells agents to read its local rules and this shared guide. Read linked guidance explicitly; GitHub UI inheritance does not load it into an agent session.

For offline work, use an accessible, maintainer-approved copy and record its revision; do not silently use a stale chat summary. If required guidance is unavailable, resolve access before editing. Changes to shared guidance are reviewed through PRs; repository-specific commands and exceptions remain local.

Instruction files do not enforce permissions or branch protection. Apply relevant repository rules and meaningful checks where available. Projects organise issues but do not grant implementation permission or automatically configure labels, milestones, CI or branch rules. Repositories owned by other accounts follow their own contributor requirements.

## Personal agent settings

User-level preferences may reinforce the basic agreements on each approved machine/runtime. They are not installed by this repository and do not automatically reach remote sessions or other contributors. Keep them brief, avoid private data and follow repository-specific rules. Do not use personal defaults to override another project's security, ownership or publication boundaries.
