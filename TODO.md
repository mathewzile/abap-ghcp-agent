# TODO

- [ ] Detect `system_type` and `version` for the ROSA skill automatically from the ADT destination. The ADT MCP tools don't expose system type or release today, so they're asked once per destination and stored in `/memories/repo/`. That stored value has to be updated by hand after every system upgrade. See [rosa-global skill](.github/skills/rosa-global/SKILL.md#target-system).
- [ ] Add the [SAP Business Accelerator Hub MCP server](https://github.com/marianfoo/sap-mcp-servers/tree/main/packages/api-hub) once it's easier to consume. It would be used to look up released APIs, business objects, events, CDS views, and BAdIs for SAP S/4HANA (on-premise, private cloud, and public cloud). It's blocked for now because reading detailed API information requires authentication.
