---
name: "ABAP File Format Metadata"
description: "Use when inspecting or editing AFF JSON metadata or the .jsonc virtual representation exposed by ABAP Development Tools for VS Code."
applyTo: "**/*.json,**/*.jsonc"
---
# AFF Metadata Instructions

- Apply these rules only when the file represents an ABAP repository object. Do not treat unrelated JSON configuration as AFF.
- Use the `abap-development-guide` skill first and the `clean-abap` skill second for development guidance associated with the represented object.
- Follow the SAP ABAP File Formats schemas and naming specification at https://github.com/SAP/abap-file-formats. Preserve the object type, schema structure, and source/metadata split.
- Treat `.jsonc` files as the VS Code extension's virtual representation; do not assume `.jsonc` is an official portable AFF extension.
- Do not invent content for unsupported objects or remove an unsupported-object marker. Use ADT for Eclipse or SAP GUI when the virtual file says the object is unsupported.
- Use the ADT MCP server for supported object creation and lifecycle operations instead of manually fabricating metadata files.