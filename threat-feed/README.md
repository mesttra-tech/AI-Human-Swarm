# Threat Feed

The Threat Feed is the public reading stream for AI-Human-Swarm.

It gives people one place on GitHub to follow defensive research about current cyber threats, AI-assisted attacks, package compromise, CI/CD risk, AI agents, MCP, suspicious runtime behavior, and practical readiness actions.

## What Goes Here

Threat Feed posts should be:

- Public-source-backed.
- Defensive and educational.
- Easy to read without a meeting.
- Safe to share with technical and non-technical teammates.
- Clear about what defenders can assess, patch, monitor, or ignore.
- Reusable later as social posts, newsletters, or short briefings.

Threat Feed posts must not include:

- Secrets, credentials, private logs, customer data, local paths, or private operational details.
- Offensive exploit chains, weaponized payloads, persistence instructions, stealth instructions, or obfuscated code.
- Commands that print credentials, secret stores, auth files, shell history, or cookies.
- Unreviewed opaque downloads, shortened links, or `curl | bash` style instructions.

## Feed Format

Each post should live in a dated Markdown file:

```text
threat-feed/YYYY-MM-DD-short-title.md
```

Use [TEMPLATE.md](TEMPLATE.md) for new posts.

## Relationship To Daily Cyber Patches

Daily cyber patches are operational. They focus on copy/paste assessment, remediation, and verification.

Threat Feed posts are editorial. They explain the threat, why it matters, who should care, and what safe next steps make sense.

The same research can produce both:

- A daily patch in `daily-cyber-patches/`.
- A readable post in `threat-feed/`.

## Future Social Distribution

The feed is designed to be repurposed later for channels such as Instagram, LinkedIn, newsletters, or short-form updates.

When preparing social content, keep the same safety boundary:

- Defensive only.
- Public sources only.
- No panic language.
- No secret values.
- No exploit instructions.
- No claims without sources.
