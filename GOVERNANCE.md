# Governance

AI-Human-Swarm is a public, defensive, community-maintained project.

The project is open to contributions, but trust is explicit and limited. External and non-maintainer contributions are treated as untrusted until maintainer review.

## Roles

### Maintainer

Maintainers can:

- Review and merge pull requests.
- Self-review and publish maintainer-authored contributions without approval from another person.
- Invite approved collaborators.
- Manage releases and project direction.
- Configure repository settings.
- Remove unsafe or off-scope content.

Initial maintainer: `@gmaiera`.

### Approved Collaborator

Approved collaborators are manually invited by a maintainer.

Approved collaborators may:

- Help triage issues.
- Review pull requests.
- Suggest daily patch improvements.
- Help validate defensive guidance.

Approved collaborators may not push directly to `main`, access repository secrets, or publish changes without maintainer review unless a maintainer explicitly changes their role later.

### External Contributor

External contributors may:

- Open issues.
- Open pull requests.
- Suggest sources, patches, templates, and review improvements.

External contributors do not receive collaborator status automatically. Merging a pull request does not grant collaborator status.

## Trust Model

The project accepts contributions, not implicit trust.

Repeated safe contributions may lead to an invitation, but approved collaborator status is always a manual maintainer decision.

Maintainer-authored contributions still need to satisfy the public-safety rules, but maintainer self-review is sufficient for publication.

## Decision Rules

- Defensive scope wins over speed.
- Public safety wins over completeness.
- Source-backed guidance wins over unsourced claims.
- Reviewable commands win over clever one-liners.
- Maintainers may close or edit contributions that introduce safety, privacy, legal, or trust risks.
