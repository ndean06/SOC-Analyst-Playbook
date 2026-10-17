# SOP: Build and Maintain MITRE ATT&CK Navigation in Splunk

## Purpose
Create an environment-independent, repeatable navigation menu that groups existing Splunk dashboards by MITRE ATT&CK tactic or detection category. This SOP covers setup, verification, and troubleshooting; it does not assume dashboards or rules already exist.

## Prerequisites
- Authorized access to Splunk with permissions to create/edit dashboards and the target app's navigation configuration.
- A list of dashboards to expose, and the MITRE ATT&CK version / taxonomy you intend to use.
- Approved change process if deploying in production.

## Procedure
1. **Inventory**: Identify the target Splunk app, server/instance, Splunk version, navigation layout, dashboard names, owners, existing app context, and ATT&CK categories. Record the exact dashboard URL for each entry by opening it from the Dashboards page. Never infer an internal view ID from its title.
2. **Confirm dashboard function**: For each dashboard, ensure it loads and underlying SPL searches run against the intended data/time range. If starting with Sigma rules, validate their translated SPL and field mappings separately.
3. **Permissions**: Confirm the intended audience can read each dashboard. Use private, app-level, or global sharing according to the organization's least-privilege policy; global is NOT universally required. Only grant edit rights to authorized roles.
4. **Locate navigation configuration**: Open **Settings > User Interface > Navigation menus** (path may vary with Splunk version). Filter by the TARGET app; choose its active/default navigation configuration. Don't change a system-wide configuration unless specifically intended and approved.
5. **Back up**: Copy the existing navigation XML to version control (remove secrets, private hosts, or sensitive paths before publishing). Record date and app.
6. **Modify navigation XML**: Add a `collection` with a human-readable label and `<a href="...">` entries referencing each verified dashboard URL. Preserve required existing navigation entries. In XML text/attribute values, write ampersands as `&amp;`.
7. **Apply and refresh**: Save the XML and reload the target app. Older UI may render a top dropdown; newer UI may present an expandable sidebar collection.
8. **Validate**: Verify the collection appears, each link opens the expected dashboard, permissions work for intended users, and panels return valid results. Navigation visibility alone is not functional verification.
9. **Maintain**: On dashboard rename/move or ATT&CK taxonomy update, verify changed URLs and category mappings, update the XML, test, and commit a revised version.

## Portable XML skeleton
```xml
<nav search_view="search">
  <view name="search" default="true" />
  <collection label="MITRE ATT&amp;CK">
    <a href="/app/TARGET_APP/VERIFIED_EXECUTION_VIEW_ID">Execution</a>
    <a href="/app/TARGET_APP/VERIFIED_PERSISTENCE_VIEW_ID">Persistence</a>
  </collection>
  <!-- Preserve other required application views here. -->
</nav>
```

**Path note:** Prefer the exact working path from the dashboard URL. The `TARGET_APP` in a link reflects where that specific view resolves; it need not be identical to the app whose navigation is being edited. Some Splunk versions/deployments include a locale prefix (e.g. `/en-US/`). Validate navigation URLs in the actual environment.

## Troubleshooting
| Symptom | Checks / action |
| --- | --- |
| Collection missing | Confirm navigation belongs to target app, XML saved, collection syntax supported by version; test a single known-good link. |
| Link returns 404 | Open the dashboard from Dashboards listing and compare actual app path and internal view ID character-for-character. |
| Access denied | Review dashboard permissions and app capabilities for the affected user; do not broaden sharing by default. |
| Dashboard opens, data absent | Verify search SPL, index, time window, role search permissions and data ingestion. |
| UI differs from walkthrough | Check Splunk version; sidebar versus top navigation may be presentation only. |

## Completion criteria
- Navigation appears in the intended application.
- Every link opens the intended dashboard for authorized users.
- Dashboard searches are independently validated.
- XML backup, change record, and checklist are stored in version control.

## Optional deployment record (keep separately from this SOP)
Date | Splunk version | Instance | Target app | Navigation configuration | Dashboard inventory | ATT&CK version | Tester | Result | Change reference
