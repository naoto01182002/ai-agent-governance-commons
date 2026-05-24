# Public Repository Readiness Checklist

This checklist records repository-level settings and publication tasks for AI Agent Governance Commons.

Some items must be configured in the GitHub repository settings UI because they are not document changes.

## Required Before or Immediately After Public Release

| Area | Item | Recommended Setting | Status |
| --- | --- | --- | --- |
| Branch protection | Protect `main` | Require PR before merge, 1 approval, conversation resolution, no force push, no deletion | TODO: GitHub Settings |
| Branch protection | Restrict direct changes to important documents | Use `CODEOWNERS` and PR review | PARTIAL: CODEOWNERS added |
| Secret scanning | Secret scanning | Enable for repository | TODO: GitHub Settings |
| Secret scanning | Push protection | Enable if available | TODO: GitHub Settings |
| Actions | Workflow permissions | Read repository contents by default; write only when needed | TODO: GitHub Settings |
| Repository features | Wiki | Disable unless intentionally used | TODO: GitHub Settings |
| Repository features | Discussions | Enable if public discussion is desired; otherwise keep Issues for actionable work | DECIDE |
| Repository metadata | About description | Add concise English or Japanese description | TODO: GitHub UI |
| Repository metadata | Topics | Add topics such as `ai-governance`, `ai-agents`, `enterprise-ai`, `rfp`, `audit-log`, `raci`, `standard` | TODO: GitHub UI |
| Release | Public Draft tag | Create `v1.0-public-draft` tag | TODO |
| Release | GitHub Release | Publish release notes clarifying draft status and non-certification | TODO |

## Repository Files Added for Public Readiness

| File | Purpose |
| --- | --- |
| `SECURITY.md` | Defines sensitive reporting, unsafe guidance reporting, and non-scope items |
| `CONTRIBUTING.md` | Defines contribution principles and accepted change types |
| `CODE_OF_CONDUCT.md` | Defines minimum discussion behavior |
| `CODEOWNERS` | Defines review ownership for core documents |
| `.github/pull_request_template.md` | Forces change intent, impact area, and governance checks |
| `.github/ISSUE_TEMPLATE/standard_proposal.yml` | Standard or MVS change proposals |
| `.github/ISSUE_TEMPLATE/template_feedback.yml` | Feedback for RFP, design, audit, RACI, self-assessment, and A2A templates |
| `.github/ISSUE_TEMPLATE/wording_clarification.yml` | Misleading, unclear, or over-claiming wording reports |
| `.github/ISSUE_TEMPLATE/governance_risk.yml` | Governance, authority, responsibility, audit, approval, stop-right, rollback, and A2A risks |
| `.github/ISSUE_TEMPLATE/bug_report.yml` | Broken links, typos, formatting, and maintenance issues |
| `CITATION.cff` | Citation metadata for external reference |

## Suggested Branch Protection Rule

Branch name pattern:

```text
main
```

Recommended settings:

- Require a pull request before merging
- Require at least 1 approval
- Dismiss stale pull request approvals when new commits are pushed
- Require review from Code Owners
- Require conversation resolution before merging
- Require linear history if squash or rebase merge is preferred
- Do not allow force pushes
- Do not allow deletions

## Suggested Repository About Description

English:

```text
Public draft standard and practical templates for AI agent governance: authority, audit logs, RACI, human approval, stop rights, and A2A responsibility boundaries.
```

Japanese:

```text
AIエージェント導入時の権限・監査ログ・RACI・人間承認・停止権・A2A責任分界を整理する公共ドラフト標準と実務テンプレート集。
```

## Suggested Topics

```text
ai-governance
ai-agents
enterprise-ai
rfp
audit-log
raci
responsibility-boundary
standard
public-draft
```

## Suggested Release Notes

```md
# AI Agent Governance Commons v1.0 Public Draft

This is the initial public draft release of AI Agent Governance Commons.

It provides minimum explanation items and practical templates for:

- AI agent authority
- audit logs
- human approval
- stop rights
- rollback / cancellation
- RACI
- A2A responsibility boundaries
- RFP and design document usage
- self-assessment

This release does not imply certification, compliance, legal approval, safety guarantee, or external audit.
```

## Local Secret Scan Recommendation

Run a local history scan before major release announcements:

```bash
gitleaks detect --source . --verbose
```

If any real secret is found, revoke and rotate it. Removing the file alone is not enough because Git history may still contain the value.
