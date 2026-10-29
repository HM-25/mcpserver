# Changelog

Public summary of MCP Server releases. Full release packages are available to subscribers via [omnicom.digital](https://www.omnicom.digital/en/our-services/methodologies-and-tools/glpi/plugins-for-glpi/). Security fixes are published as free security releases for everyone on [GitHub Releases](https://github.com/OMNICOM-Digital/mcpserver/releases); their advisories are public in [Security Advisories](https://github.com/OMNICOM-Digital/mcpserver/security/advisories).

## Support line and release convention

- **Support period:** every release is supported for five years from its release date on [GitHub Releases](https://github.com/OMNICOM-Digital/mcpserver/releases); the 1.x line runs until **2031-10-29** and moves with every release. A security release does not restart the support period of the release it fixes.
- **Feature releases** (`1.x.0`, roughly monthly): new tools and features that fit the existing permission and write-confirmation model. They stay in the 1.x line (each with its own five years of support) and are delivered to subscribers.
- **Patch releases** (`1.x.y`): fixes only, no new features.
- **Security releases:** a patch release that fixes a vulnerability, published as a GitHub Release with the fix as a patch file (and in the release notes), plus a Security Advisory. Free for everyone; it contains the patch, not the full plugin. Subscribers also get the full release through the Support Portal.
- **Tags** are the plain version number without a prefix (for example `1.8.1`), matching the version in `setup.php` and `mcpserver.xml`.
- Entries prefixed **Security:** fix a vulnerability or close a security gap.
- A new line (2.0) is opened only if the security model, authentication or intended use changes substantially; it gets its own support period, announced in advance.

## 1.8.0
- Write confirmation: every write tool now first returns a preview of exactly what it will write (targets resolved to names, before and after values for updates, a warning for destructive actions) and only writes after the person approves. On by default; admins can switch it off under Setup > MCP Server > Behavior for unattended agents
- Language check for public followups and solutions: if the text is not in the ticket requester's GLPI language, nothing is written and the person chooses whether to keep the original language or write in the requester's. On by default, switchable under Setup > MCP Server > Behavior
- Changes to both switches are recorded in the History tab
- Includes all 1.7.1 fixes
- Upgrade: run the plugin update in Setup > Plugins, clear the GLPI cache, and reconnect your AI clients

## 1.7.1
- Fix: `glpi_submit_form` no longer fails with a server error when an Item question gets an empty answer
- Unexpected errors in any tool now return a clean tool error instead of an HTTP 500
- Answers to Item questions are validated (format and item type) before the form is submitted

## 1.7.0
- New write tool `glpi_add_ticket_actor`: add a requester or observer to a ticket

## 1.6.0
- New write tool `glpi_remove_ticket_actor`
- Security: `glpi_assign_ticket` now checks that the caller has READ access to the ticket's entity before assigning
- `glpi_assign_ticket` validates assignees the same way the GLPI UI does

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
- Security: remediates all 17 findings from an independent external security review, including a private followup/task visibility gap and missing entity and rights checks on write actions
- Security: user creation, group creation, group membership, and URL-based document upload ship disabled by default; admins enable each one explicitly from Setup > MCP Server
