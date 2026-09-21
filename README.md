# GLPI MCP Server Plugin

A GLPI plugin that exposes GLPI as an [MCP](https://modelcontextprotocol.io) (Model Context Protocol) server, so AI assistants such as Microsoft Copilot and Claude can work directly with tickets, the knowledge base, users, groups, and the service catalog through a standard tool interface, instead of one-off custom integrations per client.

Built and maintained by [Omnicom, s.r.o.](https://omnicom.digital), an ITSM/ESM consultancy based in Bratislava, Slovakia.

## What it does

The plugin registers a set of MCP tools against a running GLPI instance, covering:

- Tickets: list, search, get details, timeline, create, update, follow-ups, tasks, solutions, assignment, linking, validation approval
- Documents: upload by base64 or by URL
- Users and groups: management
- Knowledge base: browse, search, create/read/update/delete
- GLPI Forms (service catalog): schema retrieval and submission

## Permission tiers

Tool visibility follows GLPI's own profiles:

- **Standard / Central** — full toolset, including user/group management, ticket updates, assignments, and validations
- **Self-Service / Helpdesk** — a limited subset: own tickets, FAQ, and permitted forms

## Compatibility

- GLPI 11.0.0 - 11.9.99 (current production: 11.0.5)
- PHP, Twig-based front end
- No raw SQL; all front/ajax endpoints permission-checked

## Status

Version 1.2.3, live-verified end-to-end against a demo GLPI instance (Tickets, Knowledge base, Users/groups, Forms, Projects, ITIL analytics).

## License

GNU General Public License v3.0 - see [LICENSE](LICENSE).

## Get in touch

Using GLPI and curious about the MCP Server plugin, or want to talk ITSM tooling? Reach us at sales@omnicom.sk or via [omnicom.digital](https://omnicom.digital).
