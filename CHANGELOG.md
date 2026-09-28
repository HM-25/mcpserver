# Changelog

Public summary of MCP Server releases. Full release packages are available to subscribers via [omnicom.digital](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/).

## 1.7.0
- New write tool `glpi_add_ticket_actor`: add a requester or observer to a ticket

## 1.6.0
- New write tool `glpi_remove_ticket_actor`
- `glpi_assign_ticket` now checks READ access to the ticket's entity and validates assignees the same way the GLPI UI does

## 1.5.0
- New read tool `glpi_search_groups`

## 1.4.5
- Fix: `glpi_assign_ticket` no longer removes existing requesters or observers; new optional `mode` (add or replace)

## 1.4.4
- `glpi_get_ticket` returns the ticket's entity (name and full path)

## 1.4.1 - 1.4.3
- Fixes to the 1.4.0 tooling: category candidate scoping, central-only hints, and ticket details are no longer hidden behind the category choice prompt

## 1.4.0
- Six new read tools for administration and ITIL categories: `glpi_list_entities`, `glpi_get_entity`, `glpi_get_session_context`, `glpi_search_itil_categories`, `glpi_get_itil_category`, `glpi_analyze_itil_ticket_category`

## 1.3.0
- Remediates all 17 findings from an independent external security review, including a private followup/task visibility gap and missing entity and rights checks on write actions
- User creation, group creation, group membership, and URL-based document upload ship disabled by default; admins enable each one explicitly from Setup > MCP Server
