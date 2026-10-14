---
name: rosa-global
description: "Query the SAP Cloudification Repository through the rosa-mcp server to identify released SAP objects, Clean Core levels (A/B/C/D), release states, successors, and Clean Core compliance. Use when selecting SAP APIs, checking whether an object is released or deprecated, finding replacements (e.g. MARA -> I_PRODUCT), or assessing custom code for Clean Core."
---
# ROSA — Released Objects Search Assistant

Adapted for MCP from upstream [ClementRingot/ROSA `skills/rosa-global/SKILL.md`](https://github.com/ClementRingot/ROSA/blob/main/skills/rosa-global/SKILL.md) (commit `e97177e`). Use the `rosa-mcp` server tools; do not call the ROSA REST API directly. The `abap-docs-mcp` server exposes tools with similar names; prefer `rosa-mcp`.

## Target System

Every tool call needs the correct `system_type` and, for `private_cloud` or `on_premise`, `version`. The tool default (`public_cloud`) returns only Level A objects and gives wrong answers for other system types.

1. Identify the ADT destination in use (from the workspace folder or `abap_list_destinations`).
2. Check `/memories/repo/` for a recorded `system_type` and `version` for that destination.
3. If none is recorded, ask the user before calling any ROSA tool:
   - `system_type`: `public_cloud` (S/4HANA Cloud Public Edition), `btp` (BTP ABAP Environment), `private_cloud` (S/4HANA Cloud Private Edition), or `on_premise`.
   - `version` (only for `private_cloud`/`on_premise`): `latest` or a release such as `2023_3` (= 2023 FPS03/SP03). Use `sap_list_versions` to offer valid values.
4. Record the answer in `/memories/repo/` as `<DESTINATION>: system_type=<value>, version=<value>`.

## Clean Core Levels

`clean_core_level` is a cumulative maximum:

| Level | Includes | Meaning |
|---|---|---|
| A | Released APIs | ABAP Cloud, upgrade-safe |
| B | + Classic APIs | Upgrade-stable; acceptable for private cloud / on-premise with governance |
| C | + Internal / stable objects | Manageable risk; consult changelog |
| D | + noAPI objects | Not Clean Core; remediate |

`public_cloud` and `btp` only contain Level A. Default to Level A unless the user or project allows a higher level.

## Tools

| Need | Tool | Key parameters |
|---|---|---|
| Find objects by name or business concept | `sap_search_objects` | `query`, `object_type`, `app_component`, `state`, `clean_core_level`, `limit`, `offset` |
| Details of one known object | `sap_get_object_details` | `object_type`, `object_name`, `clean_core_level` |
| Replacement for a deprecated or unreleased object | `sap_find_successor` | `object_name`, `object_type` |
| Compliance of a list of objects | `sap_check_clean_core_compliance` | `object_names` (comma-separated, optional `TYPE:` prefix), `target_level` (`A` or `B`) |
| Available object types and counts | `sap_list_object_types` | — |
| Repository statistics | `sap_get_statistics` | — |
| Available PCE / on-premise versions | `sap_list_versions` | — |

Pass `system_type` and `version` from [Target System](#target-system) on every call that accepts them.

## Search Strategy

1. **Exact SAP name** (e.g. `MARA`, `CL_GUI_ALV_GRID`, `I_PurchaseOrderItemAPI01`): use `sap_get_object_details` with the correct type, or `sap_search_objects` with the name as `query`.
2. **Business concept** (e.g. "purchase order", "billing document"): use `sap_search_objects` with separate, singular words, 2–3 words maximum. Abbreviations are expanded automatically. Narrow with `object_type` or `app_component` (e.g. `MM-PUR`) instead of adding words.
3. **Successor or replacement**: use `sap_find_successor`.
4. **List of objects used in custom code**: use `sap_check_clean_core_compliance`.

## Interpreting Results

- `cleanCoreLevel` is the most important field. `A` is safe for ABAP Cloud; `B` is classic and acceptable for private cloud / on-premise; `C`/`D` should be avoided.
- `state`: `released` is best; `deprecated` means use the successor; `classicAPI` is Level B; `stable`/`notToBeReleased` are Level C; `noAPI` is Level D.
- `successor`: when present, always name it as the recommended replacement.
- `relevance` (0–100): rank search results by it.
- `assessment.message`: human-readable status; quote it directly.
- `found: false`: the object is not in the repository (typically Level C/D for the selected target). Suggest released alternatives via `sap_search_objects`.
- Compliance results: report `complianceRate`, and list every `non_compliant` and `not_found` entry with its successor when available.

## Common Object Types

`DDLS` (CDS view, most released APIs), `CLAS`, `INTF`, `TABL`, `BDEF`, `SRVD`, `SRVB`, `FUNC`/`FUGR` (BAPIs and function modules), `DTEL`, `DOMA`, `SUSO`. Use `sap_list_object_types` for the full list.

## Error Handling

- No results: broaden the query, remove filters, or raise `clean_core_level` only if the target allows it.
- Unknown object type: use the valid types returned in the error or from `sap_list_object_types`.
- Server error: retry once, then inform the user.
