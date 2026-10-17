---
name: Splunk MITRE ATT&CK Dashboard Deployment
about: Reusable checklist for configuring and validating MITRE ATT&CK dashboards in any Splunk environment.
title: "[Splunk Deployment] "
---

## Deployment Information

**Environment:**
**Splunk Version:**
**Target Application:**
**Deployment Date:**
**Status:** In Progress

## 1. Preparation

- [ ] Confirm Splunk access and required permissions
- [ ] Identify the target Splunk application
- [ ] Review existing dashboards and navigation
- [ ] Back up existing navigation XML

## 2. Dashboard Configuration

- [ ] Create or identify MITRE ATT&CK dashboards
- [ ] Validate underlying SPL searches
- [ ] Verify dashboard sharing permissions
- [ ] Record exact dashboard IDs and URLs

## 3. Navigation Configuration

- [ ] Open Settings > User Interface > Navigation menus
- [ ] Select the target application's navigation menu
- [ ] Review existing XML configuration
- [ ] Add or update the MITRE ATT&CK collection
- [ ] Reference verified dashboard URLs
- [ ] Save navigation changes

## 4. Validation

- [ ] Refresh the target Splunk application
- [ ] Confirm MITRE ATT&CK navigation appears
- [ ] Test every dashboard link
- [ ] Verify dashboard searches and visualizations
- [ ] Confirm appropriate role-based access

## 5. Documentation

- [ ] Record configuration changes
- [ ] Document errors and resolutions
- [ ] Capture evidence or screenshots
- [ ] Update SOP if a reusable improvement was found
- [ ] Mark deployment complete

## Troubleshooting Notes

**Issue:**

**Root Cause:**

**Resolution:**

## Outcome

**Deployment Status:**

**Lessons Learned:**

## Reference Documentation

- [Splunk SOP](../../Splunk/MITRE-Dashboard-SOP.md)
- [Deployment Checklist](../../Splunk/MITRE-Dashboard-Checklist.md)
- [Navigation XML Template](../../Splunk/navigation-template.xml)
