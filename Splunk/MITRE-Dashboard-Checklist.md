# Reusable checklist: Splunk MITRE ATT&CK Dashboard Navigation

Copy this checklist for every deployment. Record details in a private deployment note when needed.

- [ ] Identify instance, Splunk version, target navigation app, and change authorization.
- [ ] Confirm MITRE ATT&CK version and the intended tactic/category list.
- [ ] Inventory dashboards and open each one from the Dashboards listing.
- [ ] Record each **verified full URL**, app path, and internal view ID (do not guess IDs from titles).
- [ ] Validate each dashboard and its searches before adding navigation links.
- [ ] Verify audience Read and limited Write permissions; apply least privilege.
- [ ] Locate the correct **target app** navigation (`default` or active config).
- [ ] Back up existing navigation XML and record rollback steps.
- [ ] Add/update a `<collection>` with direct `<a href>` links to verified URLs.
- [ ] Escape `&` as `&amp;` in XML; preserve needed existing views.
- [ ] Save and reload the app; confirm the collection is visible.
- [ ] Click every link and ensure it loads the correct dashboard (no 404/permission errors).
- [ ] Verify searches and panels work for the intended users.
- [ ] Capture evidence, document deviations, and commit the updated XML/checklist.
- [ ] When ATT&CK or dashboards change, review names, mappings and links again.

**Deployment outcome:** Date: ____ | Target app: ____ | ATT&CK version: ____ | Pass/Fail: ____ | Notes: ____
