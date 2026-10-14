# Project guidance

- This is an SAP ABAP virtual workspace. Locate objects through the relevant ABAP directory or package in the Explorer before searching or opening their virtual files.
- Use the ADT MCP server for ABAP repository-object lifecycle operations such as creation, validation, activation, testing, and ATC checks.
- Repository objects represented in the workspace must follow SAP ABAP File Formats (AFF): https://github.com/SAP/abap-file-formats. Refer to that repository and its technical specification whenever an object's filename, extension, metadata, schema, or source representation is unclear.
- Do not invent or manually fabricate an AFF representation for an unsupported object. Use ABAP Development Tools for Eclipse or SAP GUI when the virtual file identifies the object as unsupported.
- File-specific guidance under `.github/instructions/` applies by AFF extension.
- For ABAP development or review, use the `abap-development-guide` skill first and the `clean-abap` skill second.
- Before proposing, creating, generating, or reviewing ABAP names, resolve the customer naming profile for the target ADT destination per `.github/skills/abap-development-guide/references/naming.md`.
- To identify SAP objects or APIs, determine their Clean Core level or release state, find successors, or check Clean Core compliance, use the `rosa-global` skill with the `rosa-mcp` server.