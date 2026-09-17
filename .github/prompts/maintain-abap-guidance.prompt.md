---
name: "Maintain ABAP Guidance"
description: "Audit and update ABAP Copilot instructions and skills from Clean ABAP, the German ABAP Development Guide, SAP ABAP File Formats, and ABAP Development Tools for VS Code release information."
argument-hint: "Optional scope, release, or source to prioritize"
agent: "agent"
---
# Maintain ABAP Guidance

Audit and update this workspace's ABAP Copilot discovery path and development guidance. Honor any optional scope, release, or source supplied with the prompt invocation.

## Sources

Check the current upstream content and version history before editing:

1. SAP Clean ABAP: https://github.com/SAP/styleguides/blob/main/clean-abap/CleanABAP.md
2. ABAP Development Guide: https://github.com/1DSAG/ABAP-Leitfaden
3. SAP ABAP File Formats: https://github.com/SAP/abap-file-formats
4. Installed `SAPSE.adt-vscode` extension manifest and version history.
5. ABAP Development Tools for VS Code What's New: https://help.sap.com/docs/abap-cloud/abap-development-tools-for-visual-studio-code/what-s-new

Prefer authoritative source files, release notes, tags, commits, and the installed extension manifest over summaries or third-party commentary. Record the source version, tag, commit, extension version, or retrieval date used for each accepted update.

The ABAP Development Guide is written in German. Translate only the guidance relevant to this workspace into concise technical English. Preserve normative strength and distinctions such as MUST, SHOULD, recommendation, exception, release condition, and product limitation. When a translation is ambiguous, retain the German term in parentheses and do not strengthen the rule.

## Discovery Architecture

Preserve this separation of concerns:

- [Root Copilot instructions](../copilot-instructions.md): discovery and routing only, including the ABAP virtual filesystem, ADT MCP lifecycle operations, AFF source-of-truth, unsupported-object handling, scoped-instruction routing, and skill precedence.
- [File-specific instructions](../instructions/): concise `applyTo` routing and object/file workflow only. They may identify the applicable skills, owning object, editor or lifecycle operation, and validation path. They must not contain development guidelines, coding standards, style rules, architecture rules, security rules, testing standards, or duplicated source material.
- [Project ABAP Development Guide skill](../../.agents/skills/abap-development-guide/SKILL.md): project-specific development standards translated and curated from the ABAP Development Guide, including precedence and links to focused references.
- [Clean ABAP skill](../../.agents/skills/clean-abap/SKILL.md): general Clean ABAP standards derived from the canonical SAP guide, with links to focused references.

Project-specific guidance takes precedence over Clean ABAP. Keep this as an authority rule; do not rely on instruction loading order.

## Workflow

1. Inventory the root instructions, every `*.instructions.md`, both ABAP skills, and all skill references. Validate YAML frontmatter, relative links, names, descriptions, and discovery locations.
2. Inspect the installed `SAPSE.adt-vscode` extension version and manifest. Compare its registered languages, filename patterns, object support, AFF behavior, MCP capabilities, and release notes with the current scoped instructions.
3. Check the What's New documentation for additions, removals, renamed object types, changed file representations, lifecycle tools, backend requirements, and compatibility restrictions since the locally captured guidance.
4. Check SAP ABAP File Formats for current filename rules, extensions, object schemas, and compatibility notes. Distinguish official AFF extensions from VS Code virtual representations such as `.jsonc`.
5. Compare Clean ABAP and the ABAP Development Guide with the skill content. Add only meaningful new or changed guidance. Preserve release conditions and documented exceptions.
6. Build a rule inventory keyed by normalized meaning and source. Remove exact and semantic duplicates. Keep each standard in exactly one authoritative skill reference; use relative links and short routing statements elsewhere.
7. Resolve conflicts by documented precedence. Do not silently merge incompatible rules; preserve the higher-authority rule and note the conflict in the maintenance report.
8. Preserve support for development on every ABAP object/file type currently supported by ABAP Development Tools for VS Code. Add, update, split, or remove scoped instruction files when extension support changes.
9. Do not invent AFF representations, object support, schemas, or release capabilities. Unsupported objects must continue to route to ABAP Development Tools for Eclipse or SAP GUI.
10. Make the smallest focused edits, then validate all changed Markdown, YAML frontmatter, relative links, `applyTo` coverage, and duplicate-rule inventory.

## Required Invariants

- Development guidelines and standards exist only in the two skills and their reference files.
- Root and file-specific instructions contain no copied development standards.
- Every supported ABAP source or AFF representation has an unambiguous discovery route.
- Every scoped instruction references the applicable development skill or skills.
- The project guide's precedence over Clean ABAP remains explicit.
- AFF guidance retains https://github.com/SAP/abap-file-formats as its source of truth.
- Virtual-workspace search begins from the ABAP Explorer directory or package.
- New repository objects and lifecycle operations use the ADT MCP server when supported.
- Existing user-authored guidance is not removed unless it is duplicated, contradicted by a higher-authority source, obsolete, or moved intact to its authoritative skill location.

## Completion Report

Report:

- Sources and versions checked.
- Files changed and why.
- Supported extension/object coverage before and after.
- Duplicate or conflicting rules removed or relocated.
- German guidance translated, including any retained German terms or ambiguity.
- Validation performed and any unresolved source, backend, or extension limitations.

If no update is needed, make no edits and state that the discovery path, source versions, coverage, and duplicate audit are current.
