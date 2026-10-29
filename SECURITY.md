# Security Policy

This policy covers the GLPI plugin **MCP Server for GLPI** (`mcpserver`), published by OMNICOM s.r.o. ("OMNICOM") and licensed under GPL-3.0-or-later.

Full releases are distributed to subscribers via the OMNICOM Support Portal. This repository (https://github.com/OMNICOM-Digital/mcpserver) publishes the public changelog, security advisories and security releases.

MCP Server Lite (`mcpserverlite`) has its own repository and its own security and release policy.

## Supported versions

Every release of MCP Server for GLPI (GLPI 11.x) is supported with security fixes for **five years from its release date**. The release date of each version is published on the GitHub Releases page: https://github.com/OMNICOM-Digital/mcpserver/releases

A security patch release (`1.x.y`) does not restart the support period of the release it fixes.

Monthly feature releases (for example, new MCP tools that fit the existing permission and write-confirmation model) stay within the 1.x line. A new line (for example 2.0) is created only when the security model, authentication or intended use changes substantially, and its support period is announced in advance.

Which releases receive a security patch is described under "How security fixes are delivered".

The support period is stated here, in the product README and in the order form at the time of purchase.

## Reporting a vulnerability

**Please do not open public issues for security problems.**

Report privately. **We prefer GitHub private vulnerability reporting** on this repository: **https://github.com/OMNICOM-Digital/mcpserver/security/advisories/new** (or Security → Report a vulnerability), because the report stays confidential and the advisory, discussion and fix are tracked in one place.

If you cannot use GitHub, report by e-mail to **security@omnicom.digital**. Please do not include exploit details in public channels.

Please include:

- affected version and the GLPI version
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

- Security fixes are issued as **separate security releases** numbered `1.x.y` (patch releases), distinguishable from feature updates in the changelog (entries marked `Security:`).
- A security patch is issued for the **current release** and for **every earlier release that is within its five-year support period and is the latest release delivered to at least one customer**, as recorded in the OMNICOM Support Portal. Releases that are no longer the latest delivered release for any customer are superseded; users of such releases should upgrade.
- **Security fixes are free of charge and are not conditional on an active subscription.** A subscription covers new releases, support, SLA and related services; it is not required to receive a security fix for a version you already have.
- Each fix is accompanied by an advisory describing the issue, affected versions, severity, and the action users should take.
- Security releases and advisories remain available for at least **10 years** from their release or for the remainder of the support period, whichever is longer.

### Where to get security releases

GitHub Releases and Security Advisories of https://github.com/OMNICOM-Digital/mcpserver. Security releases are published there for everyone, regardless of subscription status. A security release on GitHub contains the fix as a patch file and in its release notes, not the full plugin; subscribers also receive the full release through the OMNICOM Support Portal. Advisories are also sent to the contact addresses of registered users.

## Scope

In scope: the plugin code, its MCP endpoint, authentication and authorisation logic, write-confirmation controls, and the plugin's own dependencies.

Out of scope: vulnerabilities in GLPI core itself (please report these to the GLPI project), in the AI client connecting to the plugin, or in the customer's own infrastructure and configuration, unless the plugin makes the issue materially worse.

## Known security considerations

- Deactivating a GLPI user does not revoke that user's already issued OAuth tokens (GLPI core behaviour). Revoke tokens explicitly when offboarding users.
- Write tools can be switched off individually by the GLPI administrator in the plugin's settings. Four higher-risk write tools (creating users and groups, adding users to groups, uploading documents from a URL) ship disabled by default. When "Require confirmation for writes" is enabled, every write first returns a preview and executes only on a signed confirmation token. Enable only the tools your organisation needs.

## Our commitments

- We document, triage and remediate reported vulnerabilities and track them to closure.
- We notify the competent authorities where required, including reporting actively exploited vulnerabilities and severe incidents under the EU Cyber Resilience Act (Regulation (EU) 2024/2847).
- We cooperate with market surveillance authorities on request.
- We share information about fixed vulnerabilities with affected users and, where relevant, the wider open-source community.

## Safe harbour

We will not pursue legal action against researchers who act in good faith, avoid access to or disclosure of other people's data, do not degrade services, and report to us privately and promptly under this policy.

---

*Last updated: **28 October 2026**. Contact: **security@omnicom.digital***
