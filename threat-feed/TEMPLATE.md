# Threat Feed - YYYY-MM-DD - <Short Title>

Mode: Public defensive briefing. No private environment data included.

## Quick Take

- <One to three plain-language bullets summarizing what happened and why defenders should care.>

## What Happened

<Explain the public threat, incident, research, vulnerability, or defensive trend. Keep it clear and source-backed.>

## Why It Matters

<Explain the operational, security, supply-chain, AI-agent, infrastructure, or business-readiness implications.>

## Who Should Pay Attention

- <Example: teams using npm packages with install scripts.>
- <Example: teams running CI/CD with broad repository tokens.>
- <Example: companies connecting AI agents to internal tools.>

## Defensive Actions

| Action | Why | Verification |
|---|---|---|
| <Assess, patch, rotate, harden, monitor, or document> | <Reason> | `<safe verification command or review step>` |

## Copy/Paste Checks

These commands should not print secret values. Run only the checks that match your environment.

```bash
export WORKSPACE_ROOT="<WORKSPACE_ROOT>"
cd "$WORKSPACE_ROOT"
```

```bash
# Example: list package manifests and lockfiles.
find "$WORKSPACE_ROOT" -type f \( \
  -name package.json -o \
  -name package-lock.json -o \
  -name pnpm-lock.yaml -o \
  -name yarn.lock -o \
  -name requirements.txt -o \
  -name pyproject.toml \
\) -not -path '*/node_modules/*' -not -path '*/.venv/*' -print
```

## AI Resiliency Angle

<Explain what this teaches about AI-connected workflows, MCP/tool permissions, monitoring, human approval, cyber readiness, or infrastructure operations.>

## Sources

- <Source name> - <What it supports>

## Social Draft

Use this only after human review.

```text
<Short defensive summary suitable for a social post. No fear bait, no exploit steps, no private details.>
```

## Public Safety Checklist

- [ ] No secret values or private logs.
- [ ] No local machine paths.
- [ ] No customer or private operational data.
- [ ] No exploit payloads or offensive instructions.
- [ ] No commands that print credentials or secret stores.
- [ ] Current threat claims have public sources.
- [ ] Social draft is defensive and source-backed.
