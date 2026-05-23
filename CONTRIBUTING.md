# Contributing

Thank you for helping build a public defensive cyber-preparedness commons.

Anyone can open an issue or pull request. Approved collaborator status is invitation-only and must be granted manually by a maintainer.

## Contribution Rules

Allowed:

- Defensive analysis of public threats.
- Public-source citations and summaries.
- Copy/paste commands that inspect, patch, verify, or harden systems.
- Safe detection guidance that does not expose secrets.
- AI-assisted contributions when AI usage is disclosed.

Not allowed:

- Live secrets, credentials, tokens, private logs, customer data, internal URLs, or local machine paths.
- Offensive exploit chains, weaponized payloads, persistence mechanisms, or stealth instructions.
- Obfuscated code, base64 payloads, shortened links, or commands that download and execute remote code without review.
- Commands that print environment variables, auth files, cookies, SSH keys, shell history, or secret stores.
- Prompt-injection instructions such as asking an agent to ignore policies, exfiltrate data, or disable safety checks.
- Current-threat claims without public sources.

## Pull Request Expectations

Every pull request should:

- Explain what changed and why.
- Mark whether AI helped draft, research, or review the contribution.
- Cite public sources for current threats, vendor incidents, CVEs, package compromise, or active exploitation claims.
- Keep runnable commands defensive, inspectable, and reversible where possible.
- Avoid unsafe one-liners such as opaque downloads, `curl | bash`, or secret-printing commands.
- Confirm that no private data or company-specific context is included.

## Review Rule

If a pull request includes runnable commands, scripts, workflows, or agent instructions, a maintainer must inspect or test them before merge.

Merging a pull request does not grant approved collaborator status. Approved collaborator status remains invitation-only.
