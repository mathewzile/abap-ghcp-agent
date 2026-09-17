---
name: "ABAP XSLT Source"
description: "Use when creating, editing, reviewing, or debugging ABAP XSLT and Simple Transformation source represented by *.xslt.xml files."
applyTo: "**/*.xslt.xml"
---
# ABAP XSLT Source Instructions

- Use the `abap-development-guide` skill first for project, security, and quality rules; use the `clean-abap` skill second where applicable.
- Preserve valid XML and the owning transformation's input/output contract. Treat external entities, dynamic calls, and untrusted XML as security-sensitive.
- Follow the SAP ABAP File Formats definition for XSLT objects at https://github.com/SAP/abap-file-formats/tree/main/file-formats/xslt.
- After changes, activate the transformation and run the narrowest relevant transformation tests and ATC checks.