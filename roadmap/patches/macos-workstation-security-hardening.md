# macOS Workstation Security Hardening

Mode: Public defensive guidance. No private environment data included.

This patch helps developers reduce common macOS workstation exposure while preserving normal AI-assisted development, Git, SSH, local tools, and package-management workflows.

## Executive Summary

- Enable the macOS application firewall and stealth mode.
- Disable unused Remote Management, legacy VNC compatibility, and insecure Remote Management compatibility settings.
- Review local services bound to all network interfaces, especially development servers.
- Install focused defensive scanners for secrets, dependencies, containers, and source-code checks.
- Keep workstation scan results private; publish only generic guidance.

## Who Should Use This

- Developers using AI coding agents, MCP tools, package managers, and local repositories.
- Maintainers who run public open-source work from a personal workstation.
- Teams that want a safe, repeatable local hardening routine without publishing private scan output.

## Copy/Paste Assessment

Run these checks in Terminal. They should not print secret values.

```bash
# Set this to the workspace you want to inspect.
export WORKSPACE_ROOT="<WORKSPACE_ROOT>"
```

```bash
# macOS version.
sw_vers
```

```bash
# Firewall and stealth mode.
/usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
/usr/libexec/ApplicationFirewall/socketfilterfw --getstealthmode
```

```bash
# Gatekeeper and System Integrity Protection.
spctl --status
csrutil status
```

```bash
# FileVault. If this fails because of local policy or volume layout, verify manually in System Settings.
fdesetup status || true
```

```bash
# Remote access state.
launchctl print system/com.apple.screensharing 2>/dev/null | rg 'state =|job state|service name|active =' || true
defaults read /Library/Preferences/com.apple.RemoteManagement 2>/dev/null || true
```

```bash
# Listening TCP services. Review anything bound to *, 0.0.0.0, or [::].
lsof -nP -iTCP -sTCP:LISTEN
```

```bash
# Launch agents and daemons. Review unknown or unnecessary entries.
find "$HOME/Library/LaunchAgents" /Library/LaunchAgents /Library/LaunchDaemons \
  -maxdepth 1 -type f -name '*.plist' -print 2>/dev/null | sort
```

```bash
# GitHub CLI auth posture. This masks token values.
gh auth status || true
```

```bash
# SSH agent public fingerprints only. This does not print private keys.
ssh-add -l || true
```

```bash
# AI agent and MCP config locations. Review paths before enabling tools.
find "$WORKSPACE_ROOT" -maxdepth 6 \( \
  -name '.mcp.json' \
  -o -name 'mcp.json' \
  -o -name '*mcp*.json' \
  -o -path '*/.claude/settings.json' \
\) -print 2>/dev/null | sort
```

```bash
# Scanner availability.
for tool in rg jq gitleaks trufflehog osv-scanner semgrep trivy pip-audit; do
  if command -v "$tool" >/dev/null 2>&1; then
    printf 'installed: %s -> %s\n' "$tool" "$(command -v "$tool")"
  else
    printf 'missing: %s\n' "$tool"
  fi
done
```

## Copy/Paste Remediation

Read each command before running it. Commands with `sudo` require administrator privileges.

```bash
# Enable the macOS application firewall.
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on
```

```bash
# Enable stealth mode so the Mac does not respond to unsolicited probes.
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode on
```

```bash
# Stop and deactivate Apple Remote Desktop / Remote Management if you do not need it.
# Skip this if your device is managed and remote management is required by policy.
sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate -stop
```

```bash
# Disable legacy VNC and insecure compatibility settings.
# Skip this if your device-management team explicitly requires these settings.
sudo defaults write /Library/Preferences/com.apple.RemoteManagement VNCLegacyConnectionsEnabled -bool false
sudo defaults write /Library/Preferences/com.apple.RemoteManagement allowInsecureDH -bool false
```

```bash
# Stop an accidental local development server after reviewing the listener list.
# Replace the example number with the specific process ID from lsof.
# DEV_SERVER_PID="12345"
# kill "$DEV_SERVER_PID"
```

```bash
# Install focused defensive scanners with Homebrew.
brew install ripgrep jq gitleaks trufflehog osv-scanner semgrep trivy pip-audit
```

```bash
# If Homebrew reports that /opt/homebrew is not writable, repair ownership first.
# Read the exact paths in the Homebrew error before running this.
sudo chown -R "$USER" /opt/homebrew
chmod -R u+w /opt/homebrew
```

## Private Local Scan

Run these locally and do not paste raw output into public issues or pull requests.

```bash
# Secret scan with redaction.
gitleaks detect --source "$WORKSPACE_ROOT" --redact --no-banner
```

```bash
# Verified secret findings only. Summarize detector and file path without printing secret values.
if command -v jq >/dev/null 2>&1; then
  trufflehog filesystem --no-update --json "$WORKSPACE_ROOT" 2>/dev/null \
    | jq -r '
        select(.Verified == true or .verified == true)
        | [
            (.DetectorName // .detector_name // "unknown-detector"),
            (.SourceMetadata.Data.Filesystem.file // .SourceMetadata.Data.Git.file // "unknown-path")
          ]
        | @tsv
      '
else
  echo "Install jq before summarizing TruffleHog JSON safely."
fi
```

```bash
# Dependency and misconfiguration checks.
osv-scanner scan source -r "$WORKSPACE_ROOT" || true
trivy fs --scanners vuln,misconfig "$WORKSPACE_ROOT" || true

# This Semgrep command fetches public rules from the Semgrep registry.
# Skip it for repositories where registry-based rule fetches are not allowed.
semgrep scan --metrics=off --config p/secrets "$WORKSPACE_ROOT" || true
```

```bash
# Python dependency audit when requirements.txt or pyproject.toml exists.
find "$WORKSPACE_ROOT" -name requirements.txt -not -path '*/.venv/*' -print
pip-audit -r requirements.txt || true
```

## Verification

```bash
/usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
/usr/libexec/ApplicationFirewall/socketfilterfw --getstealthmode
```

```bash
launchctl print system/com.apple.screensharing 2>/dev/null | rg 'state =|job state|service name|active =' || true
defaults read /Library/Preferences/com.apple.RemoteManagement 2>/dev/null || true
```

```bash
lsof -nP -iTCP -sTCP:LISTEN
```

```bash
for tool in rg jq gitleaks trufflehog osv-scanner semgrep trivy pip-audit; do
  "$tool" --version 2>/dev/null || "$tool" version 2>/dev/null || true
done
```

## Expected Findings

- Firewall should report enabled.
- Stealth mode should report on.
- Remote Management should be stopped unless required by policy.
- Legacy VNC and insecure Remote Management compatibility should be disabled or absent.
- Development servers should bind to `127.0.0.1` unless there is a clear reason to expose them on the local network.
- Scanner output should be reviewed locally and summarized publicly only as generic guidance.

## Not Applicable / Not Tested

- This patch does not prove that a workstation is compromise-free.
- This patch does not replace mobile-device-management, endpoint detection, backups, or identity controls.
- Some commands may be restricted by organization-managed devices or macOS privacy controls.
- Do not disable required VPN, endpoint-security, backup, or management agents without explicit approval from the device owner or administrator.

## Public Safety Checklist

- [x] No secret values or private logs.
- [x] No local machine paths tied to a specific person or organization.
- [x] No customer or private operational data.
- [x] No exploit payloads or offensive instructions.
- [x] No commands that print credentials, private keys, cookies, shell history, or secret stores.
- [x] AI-assisted text was reviewed before publication.
