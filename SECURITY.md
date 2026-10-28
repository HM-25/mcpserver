# Security Policy

This policy covers **MCP Server for GLPI** (`mcpserver`), developed and maintained by Omnicom, s.r.o. ("Omnicom") and licensed under GPL-3.0-or-later.

Full releases are distributed to subscribers via the Omnicom GLPI Support Portal. The public product repository, https://github.com/OMNICOM-Digital/mcpserver, publishes the public changelog, security advisories and security releases.

## Supported versions

Security support is defined per **release line**, not per individual release. All releases within a supported line receive security fixes.

| Line | GLPI | First published | Security support until |
|---|---|---|---|
| 1.x | 11.x | 09/2026 | **10/2031**\* |

\* The support end date is extended whenever a new release is published in the line, so that every release in the line is supported for at least five years from its own release date.

Monthly feature releases within a line (for example, new MCP tools that fit the existing permission and write-confirmation model) do not start a new support period. A new line (for example 2.0) is created only when the security model, authentication or intended use changes substantially, and it receives its own support period announced in advance.

The support end date is stated here and on the product page at the time of purchase or download.

## Reporting a vulnerability

**Please do not open public issues for security problems.**

Report privately by either of these channels:

- E-mail: **security@omnicom.digital**
- GitHub private vulnerability reporting on the product repository: [Report a vulnerability](https://github.com/OMNICOM-Digital/mcpserver/security/advisories/new)

Please include:

- affected version of the plugin, and the GLPI version
- a description of the issue and its impact
- steps to reproduce or a proof of concept
- whether you believe the issue is already being exploited

You do not need to be a customer to report. Reports are welcome from researchers, users and downstream integrators.

### What to expect

| Step | Target |
|---|---|
| Acknowledgement of your report | within **3** business days |
| Initial assessment and severity rating | within **10** business days |
| Fix or mitigation for confirmed issues | prioritised by severity; actively exploited vulnerabilities are handled first |
| Advisory published with the fix | on release of the fix |

We will keep you informed of progress and credit you in the advisory unless you prefer otherwise.

### Coordinated disclosure

We ask for **90** days from your report to prepare and release a fix before public disclosure. We will agree a shorter or longer period with you where the circumstances justify it (for example, active exploitation or a complex fix).

## How security fixes are delivered

- Security fixes are issued as **separate security releases** (patch releases such as `1.x.y`), distinguishable from feature updates in the changelog (entries marked `Security:`).
- Security fixes apply to **every release in the supported line**, not only the latest one.
- **Security fixes are free of charge and are not conditional on an active subscription.** A subscription covers new releases, support, SLA and related services; it is not required to receive a security fix for a version you already have.
- Each fix is accompanied by an advisory describing the issue, affected versions, severity, and the action users should take.

### Where to get security releases

Security releases are published as [GitHub Releases](https://github.com/OMNICOM-Digital/mcpserver/releases) of the product repository, together with a [Security Advisory](https://github.com/OMNICOM-Digital/mcpserver/security/advisories). They are available to everyone, regardless of subscription status. Advisories are also sent to the contact addresses of registered users.

## Scope

In scope: the plugin code, its MCP endpoint, authentication and authorisation logic, write-confirmation controls, and the plugin's own dependencies.

Out of scope: vulnerabilities in GLPI core itself (please report these to the GLPI project), in the AI client connecting to the plugin, or in the customer's own infrastructure and configuration, unless the plugin makes the issue materially worse.

## Known security considerations

- Deactivating a GLPI user does not revoke that user's already issued OAuth tokens (GLPI core behaviour). Revoke tokens explicitly when offboarding users.
- Write tools can be switched off individually by the GLPI administrator in the plugin's settings and are subject to a confirmation preview. Enable only the tools your organisation needs.

## Our commitments

- We document, triage and remediate reported vulnerabilities and track them to closure.
- We notify the competent authorities where required, including reporting actively exploited vulnerabilities and severe incidents under the EU Cyber Resilience Act (Regulation (EU) 2024/2847).
- We cooperate with market surveillance authorities on request.
- We share information about fixed vulnerabilities with affected users and, where relevant, the wider open-source community.

## Safe harbour

We will not pursue legal action against researchers who act in good faith, avoid access to or disclosure of other people's data, do not degrade services, and report to us privately and promptly under this policy.

---

*Last updated: 28 October 2026. Contact: security@omnicom.digital*
