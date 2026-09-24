<p align="center">
  <img src="https://raw.githubusercontent.com/OMNICOM-Digital/mcpserver/main/oc-icon.png" width="120" alt="Omnicom, s.r.o." />
</p>

<h1 align="center">GLPI MCP Server Plugin</h1>

<p align="center">
  <a href="https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/"><img src="https://img.shields.io/badge/Get%20it-omnicom.digital-c2304e" alt="Get it at omnicom.digital" /></a>
  <img src="https://img.shields.io/badge/license-GPLv3-13A688" alt="GPLv3 license" />
  <img src="https://img.shields.io/badge/GLPI-11.0--11.9-13A688" alt="GLPI 11.0-11.9" />
</p>

A GLPI plugin that exposes GLPI as an [MCP](https://modelcontextprotocol.io) (Model Context Protocol) server, so AI assistants work with tickets, the knowledge base, projects, users, groups, and the service catalog conversationally, instead of manual navigation or one-off custom integrations per client.

Built and maintained by [Omnicom, s.r.o.](https://omnicom.digital), an ITSM/ESM consultancy.

**[-> Full product page, pricing, and how to get it](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/)**

## Features

- **Tickets** - search, review, and update tickets in plain language, with full history, follow-ups, tasks, solutions, and approvals
- **Knowledge base** - natural-language queries return relevant articles instead of keyword search
- **Service catalog** - conversational form completion, validated against GLPI's own configuration
- **Users and groups** - look up colleagues and manage groups from the chat interface
- **Projects** - create, update, and assign projects and tasks, with cost tracking
- **ITIL analytics** (new) - flags data inconsistencies against ITIL best practices, including misclassified ticket types

## Permission tiers

Tool visibility follows GLPI's own profiles:

- **Standard / Central**: full toolset, including user/group management, ticket updates, assignments, and validations
- **Self-Service / Helpdesk**: a limited subset of own tickets, FAQ, and permitted forms

## Benefits

- Cuts the navigation burden for occasional GLPI users
- Surfaces GLPI's own rule errors transparently instead of failing silently
- Respects existing user permissions - no new access model required
- Runs natively inside GLPI, no external proxy

## Supported AI assistants

- Claude
- Microsoft Copilot

## Security

Version 1.3.0 remediates every finding from an independent external security review (17 findings total), including a private-followup/task visibility gap and several missing entity and rights checks on write actions. The four write tools with the broadest blast radius — user creation, group creation, group membership, and URL-based document upload — now ship disabled by default; an admin opts each one back in explicitly from Setup > MCP Server.

## Compatibility

- GLPI 11.0.0 - 11.9.99 (current production: 11.0.5)
- Works for on-premise and GLPI Cloud instances alike. A small, temporary GLPI core OAuth fix is still pending upstream (already reported to Teclib); a streamlined GLPI Marketplace listing for Cloud installs is in progress.
- Twig-based front end; no raw SQL; all front/ajax endpoints permission-checked

## Status

Version 1.3.0, live-verified end-to-end against a demo GLPI instance (Tickets, Knowledge base, Users/groups, Forms, Projects, ITIL analytics).

## Licensing

Source is open (GPL v3.0 - see [LICENSE](LICENSE)). A subscription covers access to current releases, updates, and the Omnicom GLPI Support Portal:

- €400/year (excl. VAT)
- Optional one-time installation assistance: €100 (excl. VAT)
- Without a renewed subscription, the last downloaded version keeps working, but there are no further releases or support portal access until renewal

**[Order / subscribe via omnicom.digital ->](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/)**

## Get in touch

Using GLPI and curious about the MCP Server plugin, or want to talk ITSM tooling? Reach us at sales@omnicom.sk or via [omnicom.digital](https://omnicom.digital).
