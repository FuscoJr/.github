# Shared development workflow

Generic contribution guidance and default issue/pull request templates for repositories owned by this account.

- [Contribution workflow](CONTRIBUTING.md): task scope, findings, review, verification and concurrent work.
- [.github/ISSUE_TEMPLATE](.github/ISSUE_TEMPLATE): task and bug forms.
- [.github/PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md): review map and validation evidence.

## How inheritance works

GitHub offers these supported default files only when a target repository has no corresponding local override, including private repositories owned by the account. Existing local issue forms/config replace the complete shared issue-form set; they are not combined. Existing PR templates and local contribution guidance take precedence.

The files do not appear in other repositories' clones. Agent instructions are not inherited across repositories. Each repository must provide its own short agent entry point and local build/branch/publication details, with an explicit link to the shared guide.

Labels are not created or inherited by templates. The bug form uses the bug label; verify that it exists in each destination repository. Projects, fields, milestones, workflow automation, CI and branch protection are configured separately.

These defaults do not replace contribution requirements in repositories owned by someone else. Do not publish client data, personal details, credentials or internal project inventories here.

## Safe rollout

Review and merge the shared setup first. Then review the adopting repository's local changes and check its issue chooser and PR template. Test the effective UI in a repository with no local override; file parsing alone does not prove inheritance.

No automated merge, deployment, release publication or account configuration is introduced. The maintainer reviews and merges.
