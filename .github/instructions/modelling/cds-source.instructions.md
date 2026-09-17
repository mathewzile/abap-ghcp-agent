---
name: "ABAP CDS Source"
description: "Use when creating, editing, or reviewing ABAP CDS data definitions, metadata extensions, entity extensions, types, aspects, access controls, entity buffers, or service definitions represented by .acds files."
applyTo: "**/*.acds"
---
# ABAP CDS Source Instructions

- Use the `abap-development-guide` skill first, especially its Clean Core, CDS, integration, and security guidance; use the `clean-abap` skill second where applicable.
- Use released CDS entities and annotations, preserve layering and package boundaries, and avoid direct dependencies on unreleased implementation objects.
- Keep authorization, data volume, association cardinality, and database performance explicit in the design.
- After changes, run the narrowest available syntax and activation checks, relevant tests, and ATC checks.