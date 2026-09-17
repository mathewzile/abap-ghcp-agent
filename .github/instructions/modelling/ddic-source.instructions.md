---
name: "ABAP Dictionary Source"
description: "Use when creating, editing, or reviewing ABAP Dictionary tables or structures represented by .ddic files."
applyTo: "**/*.ddic"
---
# ABAP Dictionary Source Instructions

- Use the `abap-development-guide` skill first for architecture, Clean Core, security, and quality rules; use the `clean-abap` skill second where applicable.
- Prefer released and reusable data elements and domains. Preserve compatibility when changing persisted tables or shared structures.
- Evaluate key design, client handling, data classification, table category, delivery behavior, and database impact before changing definitions.
- After changes, run activation-dependent checks and the narrowest relevant ATC and tests.