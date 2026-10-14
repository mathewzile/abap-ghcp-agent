---
name: "ABAP Source"
description: "Use when creating, editing, reviewing, or testing ABAP classes, interfaces, programs, includes, function groups, or function modules represented by .abap files."
applyTo: "**/*.abap"
---
# ABAP Source Instructions

- Use the `abap-development-guide` skill first for project rules, then the `clean-abap` skill for detailed style and ABAP Unit guidance.
- Use cloud-compliant syntax and released APIs by default; preserve explicit backend release constraints for legacy objects.
- Resolve object and variable naming through the `abap-development-guide` naming reference; customer conventions take precedence.
- Respect package boundaries, existing naming prefixes, and public contracts. Do not modify SAP standard or generated source directly.
- Add or update focused ABAP Unit tests for changed business logic. Put tests in the dedicated `testclasses` include/file when the object provides one.
- After source changes, run the narrowest available syntax check, relevant ABAP Unit tests, and ATC checks.