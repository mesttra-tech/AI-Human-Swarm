# Security Policy

## Public Repo Notice

This repository is public. Do not publish live credentials, `.env` values, private keys, cookies, OAuth material, customer data, private logs, local machine paths, internal URLs, or private operational context.

## Defensive Scope

This project accepts defensive and educational security guidance only.

Do not submit offensive exploit chains, weaponized payloads, persistence instructions, stealth techniques, obfuscated payloads, prompt-injection instructions, or commands intended to reveal or exfiltrate credentials.

## Reporting A Security Concern

If you find a security concern in this repository, open a private report or contact a maintainer directly. Do not include secret values in public issues, pull requests, comments, screenshots, or logs.

If you accidentally publish a secret:

1. Revoke or rotate it immediately.
2. Remove it from the public contribution.
3. Tell a maintainer what happened without repeating the secret value.

## Untrusted Contributions

Public pull requests from external contributors and non-maintainers are treated as untrusted until maintainer review.

Maintainer-authored contributions may be self-reviewed by the maintainer and do not require approval from another person, but they must still follow the public-safety and safe-command standards in this repository.

Repository secrets must not be exposed to forked pull requests. Workflows from first-time contributors should require maintainer approval before running.

## Safe Command Standard

Runnable commands in this project should:

- Be readable.
- Avoid printing secrets.
- Avoid opaque downloads.
- Avoid destructive behavior unless clearly marked and manually approved.
- Prefer inspection, patching, verification, and hardening steps.
