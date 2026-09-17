---
name: clean-abap
description: Apply SAP Clean ABAP style guidance when creating, reviewing, refactoring, or testing ABAP. Use this skill for names, language, design, methods, errors, comments, formatting, and ABAP Unit practices.
---

# Clean ABAP

Use SAP Clean ABAP as a style baseline, while respecting the target ABAP release, existing object style, framework constraints, generated code, legacy boundaries, and measured performance. For project-specific rules, use the separate `abap-development-guide` skill first.

## Workflow

1. Identify the object type, framework, release level, and whether the code is generated or legacy.
2. Preserve public contracts and local conventions unless the task explicitly changes them.
3. Make the smallest focused change; avoid broad cleanup of unrelated code.

## Focused references

Read only the reference needed for the task:

- [Names, language, and constants](./references/names-language-constants.md) for names, syntax, constants, variables, and compatibility.
- [Variables, tables, and strings](./references/variables-tables-strings.md) for declarations, internal tables, strings, and Boolean values.
- [Conditions, classes, and methods](./references/conditions-classes-methods.md) for control flow, classes, constructors, calls, and method design.
- [Errors, comments, and formatting](./references/errors-comments-formatting.md) for exceptions, comments, pragmas, and formatting.
- [ABAP Unit](./references/abap-unit.md) for test design, test doubles, test methods, and assertions.
- [Review checklist](./references/review-checklist.md) for a concise Clean ABAP review.

Canonical guide: https://github.com/SAP/styleguides/blob/main/clean-abap/CleanABAP.md
