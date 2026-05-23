# Security Policy

## Supported Versions

Only the latest release receives security fixes.

| Version | Supported |
|---|---|
| latest (`v1`) | ✅ |
| older tags | ❌ |

## Reporting a Vulnerability

**Do not open a public GitHub issue for security vulnerabilities.**

Use one of:

1. **[GitHub private security advisory](https://github.com/GregoireF/addlicense-action/security/advisories/new)** _(preferred)_ — coordinated disclosure without public exposure.
2. **Email** — [gfavreau.wrprojects@gmail.com](mailto:gfavreau.wrprojects@gmail.com) with subject `[SECURITY] addlicense-action`.

Please include:

- A clear description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (optional)

**Response SLA:** acknowledgement within 48 h · triage within 7 days · fix timeline within 14 days for confirmed issues.

## Supply-Chain Controls

| Control | Trigger |
|---|---|
| All action `uses:` pinned to commit SHA | Every workflow run |
| Dependabot (GitHub Actions + npm) | Weekly |
| `CODEOWNERS` review required on all PRs | Every pull request |
