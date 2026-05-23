---
name: daily-cyber-patch
description: "Create public-safe daily defensive cyber patches from fresh research. Use when asked to monitor current cyber threats, AI-assisted attacks, package install leaks, CI/CD risk, agent/MCP abuse, dormant malware indicators, or exploited CVEs and turn them into copy/paste assessment, remediation, and verification guidance."
---

# Daily Cyber Patch

## Mission

Create a public-safe, defensive daily cyber patch that people can copy, review, and adapt. Use fresh public research every time. Do not publish private scan results, secrets, local paths, internal context, or offensive payloads.

## Source Strategy

Use current public sources before writing:

- Exploited vulnerability sources such as CISA KEV, NVD, vendor advisories, and security advisories.
- Package ecosystem sources such as npm, PyPI, OSV, GitHub Security Advisories, and maintainer posts.
- Reputable security research from vendors, incident responders, and independent researchers.
- Official documentation for remediation commands, package-manager behavior, CI/CD controls, and agent/MCP security.

Prefer primary sources for exact facts. Label vendor analysis, media reports, and social posts by confidence.

## Daily Workflow

1. Identify notable threats from the last 24-72 hours, plus any high-impact older item newly added to exploited-vulnerability catalogs.
2. Group findings by defender action: assess, patch, rotate, harden, monitor, or ignore as not applicable.
3. Write only defensive guidance.
4. Include copy/paste commands that avoid printing secrets.
5. Include verification commands for each remediation.
6. Add public sources for current claims.
7. Run a public-safety pass before publishing.

## Required Coverage

Consider these categories every day:

- npm, PyPI, package managers, lockfiles, lifecycle scripts, and registry tokens.
- CI/CD, GitHub Actions, OIDC, runner credential exposure, and workflow permissions.
- AI agents, MCP servers, prompt injection, tool poisoning, and agent configuration.
- IDE/editor extensions and developer-machine risk.
- Dormant malware, persistence indicators, and suspicious runtime artifacts.
- Actively exploited CVEs and patch deadlines.
- Advanced AI techniques used by attackers and defensive AI techniques users can apply safely.

## Output Format

Use this structure:

```markdown
# Daily Cyber Patch - YYYY-MM-DD

Mode: Public defensive guidance. No private environment data included.

## Executive Summary

## Priority Actions

## Threats Reviewed

## Copy/Paste Assessment

## Copy/Paste Remediation

## Verification

## Not Applicable / Not Tested

## Sources

## Public Safety Checklist
```

## Safety Rules

Do not include:

- Secret values, tokens, cookies, private keys, auth files, local paths, private logs, or customer data.
- Offensive exploit chains, weaponized payloads, persistence instructions, stealth instructions, or obfuscated code.
- Commands that print environment variables, shell history, auth files, SSH keys, cookies, or secret stores.
- Opaque downloads, shortened links, or unreviewable one-liners.
- Prompt-injection text that tells agents to ignore instructions, exfiltrate data, or disable safety checks.

If a real-world compromise may have exposed credentials, recommend rotation by category without asking users to paste secret values.
