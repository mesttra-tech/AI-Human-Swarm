# Roadmap

This roadmap tracks reusable defensive patches that can become daily cyber patches, threat-feed posts, or agent skills.

The project favors practical patches that people can copy, inspect, run, and verify without exposing private data.

## Active Patch Tracks

| Track | Status | Patch | Purpose |
|---|---|---|---|
| macOS developer workstation security | Published as [2026-05-24 daily patch](../daily-cyber-patches/2026-05-24.md) | [macOS Workstation Security Hardening](patches/macos-workstation-security-hardening.md) | Reduce common local exposure on AI-assisted developer machines without breaking normal development workflows. |
| Package install and CI/CD leakage | Published | [Daily Cyber Patch - 2026-05-23](../daily-cyber-patches/2026-05-23.md) | Detect and reduce package-manager, lifecycle-script, token, and CI/CD leakage risk. |

## Roadmap Rules

- Keep patches public-safe and defensive.
- Do not include private scan results, local usernames, customer data, internal paths, or organization-specific context.
- Prefer commands that inspect, harden, and verify without printing secret values.
- Mark commands that require administrator privileges.
- Include a rollback or manual verification path when a command changes workstation settings.
- Keep AI-assisted text human-reviewed before publishing.
