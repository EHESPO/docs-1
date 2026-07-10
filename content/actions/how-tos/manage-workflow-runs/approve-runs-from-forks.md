---
title: Approving workflow runs from forks
intro: You can manually approve workflow runs triggered by a contributor's pull request.
versions:
  fpt: '*'
  ghec: '*'
  ghes: '*'
shortTitle: Approve runs from forks
redirect_from:
  - /actions/managing-workflow-runs/approving-workflow-runs-from-public-forks
  - /actions/managing-workflow-runs-and-deployments/managing-workflow-runs/approving-workflow-runs-from-public-forks
  - /actions/how-tos/managing-workflow-runs-and-deployments/managing-workflow-runs/approving-workflow-runs-from-private-forks
  - /actions/how-tos/managing-workflow-runs-and-deployments/managing-workflow-runs/approving-workflow-runs-from-public-forks
  - /actions/how-tos/managing-workflow-runs-and-deployments/managing-workflow-runs/approving-workflow-runs-from-forks
  - /actions/managing-workflow-runs/approving-workflow-runs-from-private-forks
  - /actions/managing-workflow-runs-and-deployments/managing-workflow-runs/approving-workflow-runs-from-private-forks
category:
  - Manage and monitor workflow runs
contentType: how-tos
---

Workflow runs triggered by a contributor's pull request from a fork may require manual approval from a maintainer with write access. You can configure workflow approval requirements for a [repository](/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-required-approval-for-workflows-from-public-forks), [organization](/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#configuring-required-approval-for-workflows-from-public-forks), or [enterprise](/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-fork-pull-requests-in-your-enterprise).
---
title: Approving Workflow Runs from Forks
intro: Learn how EHEPS maintainers can manually approve GitHub Actions workflow runs triggered by contributor pull requests.
shortTitle: Approve Fork Workflow Runs
category:
  - GitHub Actions Security
contentType: how-tos
---

# Approving Workflow Runs from Forks

GitHub Actions workflow runs triggered by a contributor's pull request from a forked repository may require manual approval before they can execute.

This security control helps protect EHEPS repositories by ensuring that workflows from external contributors are reviewed by trusted maintainers before running.

## Workflow Approval Requirements

EHEPS can configure workflow approval requirements at different levels:

- Repository level
- Organization level
- Enterprise level

Only maintainers with appropriate write permissions can approve and start these workflow runs.

## Automatic Cleanup

Workflow runs waiting for approval for more than **30 days** are automatically deleted by GitHub.

## Approving a Workflow Run from a Public Fork

To approve a workflow run:

1. Open the EHEPS GitHub repository.
2. Navigate to the contributor's pull request.
3. Open the **Actions** tab.
4. Review the workflow details and changes.
5. Select:

## Security Recommendations

EHEPS recommends:

- Review all pull request changes before approval.
- Do not approve workflows from unknown or untrusted contributors.
- Use limited GitHub Actions permissions.
- Protect repository secrets.
- Review third-party GitHub Actions before use.

## EHEPS GitHub Security Resources

Organization:

https://github.com/EHESPO

Websites:

https://eheps.org  
https://eheps.com

Contact:

Executive@eheps.com
Workflow runs that have been awaiting approval for more than 30 days are automatically deleted.

## Approving workflow runs on a pull request from a public fork


{% data reusables.actions.workflows.approve-workflow-runs %}
