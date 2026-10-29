<p align="center">
  <img src="https://raw.githubusercontent.com/OMNICOM-Digital/mcpserver/main/oc-icon.png" alt="OMNICOM s.r.o." width="120">
</p>

# GLPI MCP Server Plugin

[![Get it at omnicom.digital](https://img.shields.io/badge/Get%20it-omnicom.digital-c2304e)](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/)
[![GPLv3 license](https://img.shields.io/badge/license-GPLv3-13A688)](LICENSE)
[![GLPI 11.0-11.9](https://img.shields.io/badge/GLPI-11.0--11.9-13A688)](https://plugins.glpi-project.org/#/plugin/mcpserver)

**The first official MCP Server plugin for GLPI.**

A GLPI plugin that exposes GLPI as an [MCP](https://modelcontextprotocol.io) (Model Context Protocol) server, so AI assistants work with tickets, the knowledge base, projects, users, groups, and the service catalog conversationally, instead of manual navigation or one-off custom integrations per client.

Built and maintained by [OMNICOM s.r.o.](https://omnicom.digital), an ITSM/ESM consultancy.

**[-> Full product page, pricing, and how to get it](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/)**

## Features

- **Tickets** - search, review, and update tickets in plain language, with full history, follow-ups, tasks, solutions, and approvals; add or remove requesters and observers, and assign tickets to groups by name
- **Knowledge base** - natural-language queries return relevant articles instead of keyword search
- **Service catalog** - conversational form completion, validated against GLPI's own configuration
- **Users and groups** - look up colleagues and manage groups from the chat interface
- **Projects** - create, update, and assign projects and tasks, with cost tracking
- **ITIL analytics** - flags data inconsistencies against ITIL best practices, including misclassified ticket types
- **ITIL categories** - search the category tree and validate that a ticket's type and category are consistent
- **Administration** - list and inspect entities, and read the current session context
- **Write confirmation** (new) - every change the AI makes is previewed first, with targets shown by name and before and after values, and is only written after you approve it
- **Language check** (new) - public followups and solutions are checked against the requester's GLPI language, and you choose whether to keep the original language or reply in theirs

## Permission tiers

Tool visibility follows GLPI's own profiles:

- **Standard / Central**: full toolset, including user/group management, ticket updates, assignments, and validations
- **Self-Service / Helpdesk**: a limited subset of own tickets, FAQ, and permitted forms

## Benefits

- Cuts the navigation burden for occasional GLPI users
- Keeps a person in the loop: nothing is written to GLPI without an explicit approval
- Surfaces GLPI's own rule errors transparently instead of failing silently
- Respects existing user permissions - no new access model required
- Runs natively inside GLPI, no external proxy

## Supported AI assistants

- Claude
- Microsoft Copilot

## Security

Version 1.3.0 remediates every finding from an independent external security review (17 findings total), including a private-followup/task visibility gap and several missing entity and rights checks on write actions. The four write tools with the broadest blast radius (user creation, group creation, group membership, and URL-based document upload) ship disabled by default; an admin opts each one back in explicitly from Setup > MCP Server.

Later releases continued the hardening: since 1.6.0, ticket assignment checks that the caller has READ access to the ticket's entity, and assignees are validated the same way the GLPI UI validates them.

Since 1.8.0, every write is two-step. The first call only returns a preview; the write happens on a second call carrying a signed confirmation token that is valid for 10 minutes, for one user, one tool, and exactly the previewed data. Any change to the data invalidates the token. Admins can switch this off under Setup > MCP Server > Behavior for unattended agents that have nobody to ask.

### Security support

Every release is supported with security fixes for **five years from the date it is published on [GitHub Releases](https://github.com/OMNICOM-Digital/mcpserver/releases)**. That publication date is the start of the support period and is never changed afterwards. See [SECURITY.md](SECURITY.md) for which releases receive a patch.

Security fixes are **free of charge for everyone** and do not depend on an active subscription. They are published as security releases on [GitHub Releases](https://github.com/OMNICOM-Digital/mcpserver/releases), with an advisory in this repository's [Security Advisories](https://github.com/OMNICOM-Digital/mcpserver/security/advisories).

To report a vulnerability, follow [SECURITY.md](SECURITY.md) or write to security@omnicom.digital. Please do not open public issues for security problems.

### Applying a security patch

A security release on GitHub contains the fix as a patch file (and in its release notes), not the full plugin. Use the patch that matches the version shown in GLPI under Setup > Plugins:

1. Back up the plugin folder: `cp -a plugins/mcpserver plugins/mcpserver.bak`
2. Check the download: `sha256sum -c SHA256SUMS --ignore-missing`
3. From inside `plugins/mcpserver`: `patch -p1 --dry-run < mcpserver-<version>.patch`, then the same without `--dry-run`
4. Clear the GLPI cache (`php bin/console cache:clear` in the GLPI root) and reconnect your AI clients

If a patch does not apply, e-mail security@omnicom.digital with your plugin version. Subscribers also receive the full security release through the OMNICOM Support Portal.

## Compatibility

- GLPI 11.0.0 - 11.9.99 (recommended: 11.0.11 or later)
- On-premise GLPI: supported and listed on the [GLPI Plugins marketplace](https://plugins.glpi-project.org/#/plugin/mcpserver). GLPI Cloud: installation is in progress.
- Since GLPI 11.0.11 the OAuth fix the plugin relies on is part of GLPI core, so no core patch is needed before installing. On GLPI 11.0.0 - 11.0.10 the patch still has to be applied first.
- Twig-based front end; no raw SQL; all front/ajax endpoints permission-checked

## Status

Version 1.8.0 (60 tools: 33 read, 27 write), live-verified end-to-end against a demo GLPI instance (Tickets, Knowledge base, Users/groups, Forms, Projects, ITIL analytics, Administration). See [CHANGELOG.md](CHANGELOG.md) for release history.

Upgrading from an earlier version: run the plugin update in Setup > Plugins, clear the GLPI cache, and reconnect your AI clients.

## Licensing

The plugin is licensed under GPL v3.0 (see [LICENSE](LICENSE)). The plugin package, including its source, is delivered to subscribers through the OMNICOM Support Portal; this repository holds the public documentation, changelog, security policy, advisories, and security releases.

A subscription covers new releases, support with SLA, and access to the OMNICOM Support Portal:

- €400/year (excl. VAT)
- Optional one-time installation assistance: €100 (excl. VAT)
- Without a renewed subscription, the last downloaded version keeps working; new feature releases, support and Support Portal access pause until renewal, but security fixes stay free on GitHub

Security fixes are not part of the subscription. See [Security support](#security-support) above and [SECURITY.md](SECURITY.md).

**[Order / subscribe via omnicom.digital ->](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/)**

## Get in touch

Using GLPI and curious about the MCP Server plugin, or want to talk ITSM tooling? Reach us at sales@omnicom.digital or via [omnicom.digital](https://omnicom.digital).

Security issues: security@omnicom.digital (see [SECURITY.md](SECURITY.md)).
