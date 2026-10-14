---
name: abap-development-guide
description: Apply the project ABAP Development Guide when developing, reviewing, testing, securing, naming, or deploying SAP ABAP. Use this skill for project-specific rules and customer naming conventions; it takes precedence over general Clean ABAP guidance.
---

# Project ABAP Development Guide

This skill represents the project-specific development standard. Use it before `clean-abap` whenever the task concerns this workspace.

## Authority and precedence

1. Explicit project instructions, object-specific conventions, and customer naming conventions resolved through [Naming conventions](./references/naming.md).
2. The project ABAP Development Guide supplied as `SAP-Guide-ABAP-English-Version.pdf`.
3. SAP framework and release constraints.
4. SAP Clean ABAP guidance.
5. General coding preferences.

When two rules conflict, follow the higher-priority source and mention the conflict in a review. Apply guide statements according to their wording; preserve release conditions and documented exceptions.

## How to use this skill

- Identify the object type: class, interface, report, function module, CDS, RAP behavior, service, authorization object, or configuration.
- Confirm the target ABAP release and whether the object is standard, generated, customer-owned, or an extension.
- Read only the relevant topic reference under `references/`.

## Topic references

- [Naming conventions](./references/naming.md) resolves customer naming profiles per ADT destination and supplies default object names.
- [Guide overview](./references/guide-overview.md) maps the guide's chapters and the intended development lifecycle.
- [Modern ABAP and architecture](./references/modern-abap-and-architecture.md) covers the Modern ABAP, package, OO, Clean ABAP, and RAP chapters.
- [Testing, ALM, and quality](./references/testing-alm-and-quality.md) covers ABAP Unit, quality assurance, ALM, version control, and release gates.
- [Security](./references/security.md) covers secure development, common vulnerabilities, authorization, and ATC.
- [Clean Core, CDS, and integration](./references/clean-core-cds-integration.md) covers Clean Core, CDS, integration, and extension boundaries.
- [UI and documentation](./references/ui-and-documentation.md) covers Fiori/UI direction and documentation standards.
- [AI and open source](./references/ai-and-open-source.md) covers the guide's AI and open-source development topics.
