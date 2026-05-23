# Daily Cyber Patch - YYYY-MM-DD

Mode: Public defensive guidance. No private environment data included.

## Executive Summary

- <One to three bullets summarizing the highest-priority defensive actions.>

## Priority Actions

| Priority | Action | Who Should Care | Verification |
|---|---|---|---|
| High | <Patch, rotate, disable, or inspect> | <Affected users> | `<safe verification command>` |

## Threats Reviewed

| Threat | Ecosystem | Why It Matters | Confidence | Sources |
|---|---|---|---|---|
| <Threat name> | <npm/PyPI/CI/agent/CVE/etc.> | <Defensive impact> | High/Medium/Low | <Public source names/links> |

## Copy/Paste Assessment

Run only the checks that match your environment. These commands should not print secret values.

```bash
# Set this to your local workspace before running checks.
export WORKSPACE_ROOT="<WORKSPACE_ROOT>"
cd "$WORKSPACE_ROOT"
```

```bash
# Find package manifests and lockfiles.
find "$WORKSPACE_ROOT" -type f \( \
  -name package.json -o \
  -name package-lock.json -o \
  -name pnpm-lock.yaml -o \
  -name yarn.lock -o \
  -name requirements.txt -o \
  -name pyproject.toml \
\) -not -path '*/node_modules/*' -not -path '*/.venv/*' -print
```

```bash
# Review install-time package scripts without running them.
rg -n '"(preinstall|install|postinstall|prepare)"[[:space:]]*:' \
  -g 'package.json' \
  -g '!**/node_modules/**' \
  "$WORKSPACE_ROOT" || true
```

```bash
# Find registry auth configuration files without printing token values.
find "$WORKSPACE_ROOT" -name .npmrc -type f -not -path '*/node_modules/*' -print
rg --files-with-matches --hidden -i '(_authToken|NPM_TOKEN|npm_[A-Za-z0-9]{20,})' \
  -g '.npmrc' \
  -g '!**/.git/**' \
  -g '!**/node_modules/**' \
  "$WORKSPACE_ROOT" || true
```

## Copy/Paste Remediation

```bash
# Node projects with a lockfile: apply non-breaking audit fixes to the lockfile first.
npm audit
npm audit fix --package-lock-only
npm ci
npm test
npm audit --audit-level=high
```

```bash
# Investigative install mode when install-time malware is suspected.
npm ci --ignore-scripts
npm audit --audit-level=high
```

If a suspected compromise may have exposed credentials, rotate affected credentials through the proper account or secret-management UI. Do not paste secret values into issues, pull requests, logs, or chat.

## Verification

```bash
git status --short
npm test
npm audit --audit-level=high
```

## Not Applicable / Not Tested

- <List ecosystems or tools that were not assessed.>
- <List missing scanners or unavailable sources.>

## Sources

- <Source name> - <What it supports>

## Public Safety Checklist

- [ ] No secret values or private logs.
- [ ] No local machine paths.
- [ ] No customer or private operational data.
- [ ] No exploit payloads or offensive instructions.
- [ ] No commands that print credentials or secret stores.
- [ ] Current threat claims have public sources.
- [ ] AI-assisted text was reviewed by a human before publication.
