# Security Policy

## Supported versions

The following versions of Enterprise Semantics repositories receive security updates:

| Repository family | Supported |
|-------------------|-----------|
| All repositories at or above `v0.1.0-seed` | Yes |
| Pre-release seed snapshots | Best-effort |

## Reporting a vulnerability

Please report security vulnerabilities through one of these channels:

1. **GitHub private vulnerability reporting**: open a security advisory on the affected repository using GitHub's "Report a vulnerability" button. The repository maintainer (CODEOWNERS) is notified privately.
2. **Email**: send a message to the address published in the organization's profile. Mark the subject `[SECURITY] <repo>: <short description>`.

Please **do not** open a public issue for a suspected security vulnerability.

## What to include

- A clear description of the vulnerability and its impact.
- Steps to reproduce, or a proof-of-concept.
- The affected repository, version, and (if known) commit SHA.
- Your contact details if you wish to be credited or to receive updates.

## Response timeline

| Stage | Target |
|-------|--------|
| Initial acknowledgement | within 72 hours of report |
| Triage and severity assessment | within 7 days |
| Patch released | within 30 days for high-severity issues; best-effort for lower severity |
| Public disclosure | coordinated with the reporter, after a patch is available |

## Scope

This policy applies to all repositories under the `Enterprise-Semantics` GitHub organization. It does not cover downstream repositories that consume Enterprise Semantics; those follow their own security policies.

## Out of scope

- Theoretical concerns without a reproducible exploit.
- Vulnerabilities in dependencies that have already been reported upstream and are not yet patched.
- Social-engineering attacks against maintainers.