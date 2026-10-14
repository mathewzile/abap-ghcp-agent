# TODO

- [ ] Detect `system_type` and `version` for the ROSA skill automatically from the ADT destination. The ADT MCP tools don't expose system type or release today, so they're asked once per destination and stored in `/memories/repo/`. That stored value has to be updated by hand after every system upgrade. See [rosa-global skill](.github/skills/rosa-global/SKILL.md#target-system).
