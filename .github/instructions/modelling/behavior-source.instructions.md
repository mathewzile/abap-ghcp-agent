---
name: "RAP Behavior Source"
description: "Use when creating, editing, or reviewing RAP behavior definitions or behavior extensions represented by .abdl files."
applyTo: "**/*.abdl"
---
# RAP Behavior Source Instructions

- Use the `abap-development-guide` skill first for RAP, architecture, Clean Core, security, and testing guidance; use the `clean-abap` skill second for implementation details.
- Resolve behavior pool and related RAP names through the `abap-development-guide` naming reference; customer conventions take precedence.
- Preserve the business object's transactional contract, authorization model, locking, numbering, feature control, and validation semantics.
- Keep behavior definitions aligned with their CDS entities and behavior implementation classes.
- After changes, activate the affected RAP objects and run relevant ABAP Unit and ATC checks.