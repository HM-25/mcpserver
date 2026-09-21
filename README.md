# GLPI MCP Server Plugin

A GLPI plugin that exposes GLPI as an [MCP](https://modelcontextprotocol.io) (Model Context Protocol) server, so AI assistants work with tickets, the knowledge base, projects, users, groups, and the service catalog conversationally, instead of manual navigation or one-off custom integrations per client.

Built and maintained by [Omnicom, s.r.o.](https://omnicom.digital), an ITSM/ESM consultancy based in Bratislava, Slovakia. Full product page: [omnicom.digital - GLPI plugins](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/).

## Features

- **Tickets** - search, review, and update tickets in plain language, with full history, follow-ups, tasks, solutions, and approvals
- **Knowledge base** - natural-language queries return relevant articles instead of keyword search
- **Service catalog** - conversational form completion, validated against GLPI's own configuration
- **Users and groups** - look up colleagues and manage groups from the chat interface
- **Projects** - create, update, and assign projects and tasks, with cost tracking
- **ITIL analytics** (new) - flags data inconsistencies against ITIL best practices, including misclassified ticket types

## Permission tiers

Tool visibility follows GLPI's own profiles:

- **Standard / Central** — full toolset, including user/group management, ticket updates, assignments, and validations
- **Self-Service / Helpdesk** — a limited subset: own tickets, FAQ, and permitted forms

## Benefits

- Cuts the navigation burden for occasional GLPI users
- Surfaces GLPI's own rule errors transparently instead of failing silently
- Respects existing user permissions - no new access model required
- Runs natively inside GLPI, no external proxy

## Supported AI assistants

- Claude
- Microsoft Copilot

## Compatibility

- GLPI 11.0.0 - 11.9.99 (current production: 11.0.5)
- Currently on-premise only. OAuth login needs a small, temporary GLPI core patch that can't be applied on Cloud instances; Cloud distribution through the GLPI Marketplace private-plugin mechanism is planned once that's fixed upstream (already reported to Teclib).
- Twig-based front end; no raw SQL; all front/ajax endpoints permission-checked

## Status

Version 1.2.3, live-verified end-to-end against a demo GLPI instance (Tickets, Knowledge base, Users/groups, Forms, Projects, ITIL analytics).

## Licensing

Source is open (GPL v3.0 - see [LICENSE](LICENSE)). A subscription covers access to current releases, updates, and the Omnicom GLPI Support Portal:

- €400/year (excl. VAT)
- Optional one-time installation assistance: €100 (excl. VAT)
- Without a renewed subscription, the last downloaded version keeps working, but there are no further releases or support portal access until renewal

## Get in touch

Using GLPI and curious about the MCP Server plugin, or want to talk ITSM tooling? Reach us at sales@omnicom.sk or via [omnicom.digital](https://omnicom.digital).
