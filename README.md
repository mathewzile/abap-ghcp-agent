# ABAP GitHub Copilot Workspace

A reusable Visual Studio Code workspace for agent-assisted SAP ABAP development with:

- Repository-wide Copilot routing in `.github/`
- File-specific ABAP File Format (AFF) instructions
- Project ABAP and Clean ABAP skills in `.github/skills/`
- A `modern-abap-developer` agent in `.github/agents/`
- Guidance for an ADT-compatible multi-root workspace

Development standards live in skills. Root and file-specific instructions provide discovery, object routing, AFF handling, and validation workflow.

## Prerequisites

Install and configure:

1. [Visual Studio Code](https://code.visualstudio.com/)
2. [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
3. [ABAP Development Tools for VS Code](https://marketplace.visualstudio.com/items?itemName=SAPSE.adt-vscode)
4. Access and development authorization for at least one supported SAP system

The SAP extension supports RFC connections for on-premise or private-cloud systems and HTTP connections for SAP BTP ABAP environment or SAP S/4HANA Cloud Public Edition. Available object types and features depend on both the extension and the connected backend release.

## Set Up The Workspace

1. Clone this repository.
2. Create `abap.code-workspace` in the repository root with the base content below.
3. Open `abap.code-workspace` in Visual Studio Code.
4. Run `ABAP: New Destination` from the Command Palette and complete the connection setup.
5. Run `ABAP: Add Destination as Folder to Workspace...` or add the required package.
6. Save the workspace when prompted.

Keep the repository root as the first entry in `abap.code-workspace`. Copilot resolves `.github/` relative to each workspace folder, so the root folder must be the one that contains `.github/`:

```jsonc
{
  "folders": [
    { "name": "ABAP Copilot Workspace", "path": "." }
  ]
}
```

Do not add `.github` itself as a workspace folder. That nests the lookup to `.github/.github/` and silently disables every instruction, skill, and agent.

Every entry after it must be a developer-defined, connected SAP destination, for example:

```jsonc
{
  "name": "<DESTINATION_ID>",
  "uri": "abap:/repotree-v1/<DESTINATION_ID>"
}
```

Workspace files are ignored by Git so every developer can maintain their own SAP destinations and layout. Do not commit credentials, tokens, or connection secrets.

## Using Copilot For ABAP

The workspace discovery path is:

1. `.github/copilot-instructions.md` routes virtual-filesystem, ADT MCP, AFF, and skill discovery.
2. `.github/instructions/` applies object and extension-specific workflow instructions.
3. `.github/skills/abap-development-guide/` supplies project development standards.
4. `.github/skills/clean-abap/` supplies general Clean ABAP guidance when it does not conflict with the project guide.

Select the `modern-abap-developer` agent in Copilot Chat for ABAP work. It adds a scope boundary, an ordered context budget so only the needed guidance is loaded, and an activation, test, and ATC validation gate.

Locate ABAP objects through the ABAP Explorer directory or package before asking Copilot to inspect or modify them. The SAP extension exposes repository objects through a virtual filesystem, so ordinary local filesystem search cannot discover every object.

Enable the ADT MCP server in the ABAP Development Tools settings when agentic object creation, activation, testing, or ATC operations are required. Use MCP lifecycle tools for supported objects rather than manually fabricating repository files.

Objects marked as unsupported by ABAP Development Tools for VS Code must be edited with ABAP Development Tools for Eclipse or SAP GUI.

## ABAP File Formats

Repository representations follow [SAP ABAP File Formats](https://github.com/SAP/abap-file-formats). The scoped instructions cover ABAP source, CDS, RAP behavior, DDIC, XSLT, metadata, and related AFF resources supported by this workspace.

## Maintaining Guidance

Run `/maintain-abap-guidance` in Copilot Chat to audit upstream Clean ABAP guidance, the ABAP Development Guide, AFF definitions, extension changes, duplicate rules, and discovery coverage.
