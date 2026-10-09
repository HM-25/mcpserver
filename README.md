<p align="center">
  <img src="https://raw.githubusercontent.com/OMNICOM-Digital/mcpserver/main/oc-icon.png" width="120" alt="Omnicom, s.r.o." />
</p>

<h1 align="center">GLPI MCP Server Plugin</h1>

<p align="center">
  <a href="https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/"><img src="https://img.shields.io/badge/Get%20it-omnicom.digital-c2304e" alt="Get it at omnicom.digital" /></a>
  <img src="https://img.shields.io/badge/license-GPLv3-13A688" alt="GPLv3 license" />
  <img src="https://img.shields.io/badge/GLPI-11.0--11.9-13A688" alt="GLPI 11.0-11.9" />
</p>

**The first official MCP Server plugin for GLPI.**

A GLPI plugin that exposes GLPI as an [MCP](https://modelcontextprotocol.io) (Model Context Protocol) server, so AI assistants work with tickets, the knowledge base, projects, users, groups, and the service catalog conversationally, instead of manual navigation or one-off custom integrations per client.

Built and maintained by [Omnicom, s.r.o.](https://omnicom.digital), an ITSM/ESM consultancy.

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

Version 1.3.0 remediates every finding from an independent external security review (17 findings total), including a private-followup/task visibility gap and several missing entity and rights checks on write actions. The four write tools with the broadest blast radius (user creation, group creation, group membership, and URL-based document upload) now ship disabled by default; an admin opts each one back in explicitly from Setup > MCP Server.

Later releases continued the hardening: since 1.6.0, ticket assignment checks that the caller has READ access to the ticket's entity, and assignees are validated the same way the GLPI UI validates them.

Since 1.8.0, every write is two-step. The first call only returns a preview; the write happens on a second call carrying a signed confirmation token that is valid for 10 minutes, for one user, one tool, and exactly the previewed data. Any change to the data invalidates the token. Admins can switch this off under Setup > MCP Server > Behavior for unattended agents that have nobody to ask.

## Compatibility

- GLPI 11.0.0 - 11.9.99 (recommended: 11.0.11 or later)
- Works for on-premise and GLPI Cloud instances alike. Since GLPI 11.0.11 the OAuth fix the plugin relies on is part of GLPI core, so no core patch is needed before installing. On GLPI 11.0.0 - 11.0.10 the patch still has to be applied first. A streamlined GLPI Marketplace listing for Cloud installs is in progress.
- Twig-based front end; no raw SQL; all front/ajax endpoints permission-checked

## Status

Version 1.8.0 (60 tools: 33 read, 27 write), live-verified end-to-end against a demo GLPI instance (Tickets, Knowledge base, Users/groups, Forms, Projects, ITIL analytics, Administration). See [CHANGELOG.md](CHANGELOG.md) for release history.

Upgrading from an earlier version: run the plugin update in Setup > Plugins, clear the GLPI cache, and reconnect your AI clients.

## Licensing

Source is open (GPL v3.0 - see [LICENSE](LICENSE)). A subscription covers access to current releases, updates, and the Omnicom GLPI Support Portal:

- €400/year (excl. VAT)
- Optional one-time installation assistance: €100 (excl. VAT)
- Without a renewed subscription, the last downloaded version keeps working, but there are no further releases or support portal access until renewal

**[Order / subscribe via omnicom.digital ->](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/)**

## Get in touch

Using GLPI and curious about the MCP Server plugin, or want to talk ITSM tooling? Reach us at sales@omnicom.sk or via [omnicom.digital](https://omnicom.digital).
