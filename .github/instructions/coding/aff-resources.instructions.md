---
name: "ABAP File Format Resources"
description: "Use when editing AFF text resources, CSN models, or form resources represented by .properties, .csn, or .xdp files."
applyTo: "**/*.*.properties,**/*.csn,**/*.xdp"
---
# AFF Resource Instructions

- Apply these rules only when the file belongs to an ABAP repository object's AFF representation.
- Use the `abap-development-guide` skill first and the `clean-abap` skill second for development guidance associated with the represented object.
- Follow the SAP ABAP File Formats specification at https://github.com/SAP/abap-file-formats and preserve the owning object's filename, content-type, and language suffix conventions.
- Preserve UTF-8 without BOM, LF line endings, and a final newline. Keep generated or binary-compatible resource structures intact.
- Validate and activate the complete owning repository object after changing a resource file.