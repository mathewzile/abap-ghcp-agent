---
name: "Update ROSA Skill"
description: "Sync the MCP-adapted rosa-global skill with the upstream ROSA skill and the current rosa-mcp tool definitions."
argument-hint: "Optional upstream commit or tag to sync to"
agent: "agent"
---
# Update ROSA Skill

Update [the rosa-global skill](../skills/rosa-global/SKILL.md) so it reflects the current upstream ROSA guidance, adapted for the `rosa-mcp` server. Honor any commit or tag supplied with the prompt invocation; otherwise use `main`.

## Sources

1. Upstream skill: https://github.com/ClementRingot/ROSA/blob/main/skills/rosa-global/SKILL.md and its commit history.
2. ROSA repository README and MCP server source: https://github.com/ClementRingot/ROSA
3. The live `rosa-mcp` tool definitions (names, descriptions, parameters, enums, defaults) as exposed in this session, configured in [.mcp.json](../../.mcp.json).

## Workflow

1. Read the current local skill and note the upstream commit it records.
2. Fetch the upstream skill and diff it against that commit. If nothing changed upstream and the `rosa-mcp` tool definitions still match the local skill, make no edits.
3. Map every upstream REST endpoint to its `rosa-mcp` tool. Flag any endpoint without a tool, and any tool not covered by the skill.
4. Carry over changes to Clean Core levels, system types, parameters, states, search strategy, result interpretation, object types, and error handling.
5. Apply these adaptation rules:
   - Reference `rosa-mcp` tool names, never REST paths, base URLs, query strings, CORS, or HTTP status codes.
   - Use parameter names, enums, and defaults from the live tool definitions; where they differ from upstream, the tool definitions win.
   - Omit raw JSON request/response examples; describe the fields to read instead.
   - Keep the **Target System** section (ask per destination, record in `/memories/repo/`) unchanged unless the tools gain a way to detect the system type.
   - Keep frontmatter `name: rosa-global` and a description that covers Clean Core level, release state, successor, and compliance lookups.
6. Update the recorded upstream commit hash in the skill.
7. Confirm [copilot-instructions.md](../copilot-instructions.md) still routes Clean Core object identification to the skill.

## Completion Report

Report the upstream commit synced to, tool-definition changes found, sections changed, and any endpoint/tool mismatches left unresolved.
