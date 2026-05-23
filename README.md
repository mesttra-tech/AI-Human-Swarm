# AI-Human-Swarm

AI-Human-Swarm is a public, defensive, community-maintained project for AI-assisted cyber preparedness.

The goal is simple: help humans use AI to prepare against AI-assisted threats without publishing private data, offensive payloads, or unsafe copy/paste instructions.

## What This Project Produces

- Daily public cyber patches with current defensive guidance.
- Copy/paste assessment, remediation, and verification steps.
- A reusable `daily-cyber-patch` skill for coding agents.
- Contribution rules for safe, source-backed, AI-assisted collaboration.

## Daily Cyber Patches

Daily patches live in:

```text
daily-cyber-patches/
```

Each patch should be public-safe and defensive. It may cover:

- Package install leaks and supply-chain compromise.
- npm, PyPI, package managers, lockfiles, lifecycle scripts, and registry tokens.
- CI/CD, GitHub Actions, OIDC, runners, and credential exposure.
- AI agents, MCP servers, prompt injection, and tool poisoning.
- IDE/editor extensions and local developer-machine risk.
- Dormant malware or persistence indicators.
- Actively exploited CVEs and practical hardening steps.
- Defensive AI techniques that help people detect, verify, and respond.

## Collaboration Model

Anyone can open issues and pull requests. Approved collaborator status is invitation-only.

People from any organization may participate with personal GitHub accounts, as long as contributions follow the public-safety rules.

Pull requests are welcome, but all incoming content is treated as untrusted until reviewed. Merging a pull request does not grant collaborator status, maintainer rights, direct push access, or secret access.

## **mesttra** AI Resiliency Plan

AI-Human-Swarm is hosted under the `mesttra-tech` GitHub organization. The central project is the [**mesttra** AI Resiliency Plan](docs/mesttra-briefing.md): a defensive operating model for helping companies connect AI agents and MCP-enabled workflows while monitoring cyber readiness, infrastructure operations, dependency risk, automation governance, and AI adoption maturity.

Companies can express interest without scheduling a call first by opening an **AI Resiliency Plan interest** issue. The issue form asks for public company context, company website, approximate size, contact role, decision role, AI goals, maturity, risk areas, systems involved, timeline, and preferred next step.

## Safety Line

This project is defensive and educational only.

Do not publish secrets, private logs, customer data, local machine paths, internal URLs, offensive exploit chains, obfuscated payloads, shortened links, or commands that print or exfiltrate credentials.

Read [CONTRIBUTING.md](CONTRIBUTING.md), [GOVERNANCE.md](GOVERNANCE.md), and [SECURITY.md](SECURITY.md) before contributing.
