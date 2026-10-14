# Naming Conventions

Customer naming conventions take precedence over every default in this workspace, including Clean ABAP.

## Resolution

Resolve naming before proposing names, creating or generating objects, or reviewing names.

1. **Identify the target system.** Use the ADT destination ID: the workspace folder segment after `abap:/repotree-v1/` of the edited file, or the destination passed to ADT MCP creation and generator tools. If neither identifies one system, ask the user.
2. **Look up the profile.** Read `.github/customer/systems.md` by its exact path. Customer files are gitignored, so workspace search tools may skip them.
   - Destination not listed, or file missing: use the defaults below and state "No customer naming convention maintained for `<destination>`; defaults applied."
   - Destination listed more than once: stop and ask the user.
   - Role other than `DEV`: warn before creating or changing repository objects.
3. **Apply rules per kind and per object type.** Read `.github/customer/<profile>/naming-objects.md` and `naming-variables.md`. A customer rule wins for each type it defines. If the profile names an ATC naming check variant, that variant is authoritative.
4. **Handle unlisted types** according to the profile's `Unlisted types` setting:
   - `default` (also when the setting is absent): use the default and label the name "default - not in customer profile" in proposals and reviews.
   - `ask`: ask the user before using any name for that type.
   Never invent a customer pattern by analogy with other profile rows.
5. **Framework signatures win.** Names fixed by an SAP framework or a redefined/implemented signature (for example `textid` and `previous` in exception constructors, RAP handler parameters, BAdI interface parameters) keep their given names.
6. **Preserve legacy style.** When changing an existing object, follow the style already used in it; never mix naming styles within one object.
7. **Do not guess.** If the module, namespace, or business term required by a pattern is unknown, ask the user or use an explicit placeholder such as `<module>`.
8. **Validate.** Run the ADT creation validation before creating an object to catch length and namespace errors. It does not cover every type (for example packages, data elements, domains, message classes); check those manually against the pattern and maximum length.

Never use naming evidence or profiles from another destination.

## Default variable naming

Use the Clean ABAP names rules in `clean-abap/references/names-language-constants.md`: descriptive `snake_case`, no Hungarian notation or technical prefixes.

## Default repository object naming

Use `Z` (or `Y` where the project uses it) followed by the type prefix and a descriptive name. When a registered namespace is configured, it replaces `Z`: `/NS/CL_ORDER`, not `Z/NS/CL_ORDER`. Maximum lengths include the namespace.

| Object type | Pattern | Max | Example |
| --- | --- | --- | --- |
| Package | `Z<area>_<name>` | 30 | `ZSD_ORDER` |
| Class | `ZCL_<name>` | 30 | `ZCL_SD_ORDER_PRICING` |
| Exception class | `ZCX_<name>` | 30 | `ZCX_SD_ORDER` |
| Interface | `ZIF_<name>` | 30 | `ZIF_SD_ORDER_REPOSITORY` |
| Program | `Z<name>` | 40 | `ZSD_ORDER_CLEANUP` |
| Function group | `Z<name>` | 26 | `ZSD_ORDER` |
| Function module | `Z_<name>` | 30 | `Z_SD_ORDER_READ` |
| Database table | `Z<name>` | 16 | `ZSD_ORDER` |
| Draft table | `Z<name>_D` | 16 | `ZSD_ORDER_D` |
| Structure | `ZS_<name>` | 30 | `ZS_SD_ORDER` |
| Table type | `ZTT_<name>` | 30 | `ZTT_SD_ORDER` |
| Data element / domain | `Z<name>` | 30 | `ZSD_ORDER_STATUS` |
| CDS basic/interface view | `ZI_<name>` | 30 | `ZI_SalesOrder` |
| CDS RAP root/restricted view | `ZR_<name>` | 30 | `ZR_SalesOrder` |
| CDS projection/consumption view | `ZC_<name>` | 30 | `ZC_SalesOrder` |
| CDS value help | `ZI_<name>_VH` | 30 | `ZI_OrderStatus_VH` |
| CDS abstract entity | `ZA_<name>` | 30 | `ZA_OrderCancelParam` |
| Metadata extension / access control | Same as the CDS entity | 30 | `ZC_SalesOrder` |
| Behavior definition | Same as the root entity | 30 | `ZR_SalesOrder` |
| Behavior pool | `ZBP_<root entity>` | 30 | `ZBP_R_SalesOrder` |
| Service definition | `ZUI_<name>` (UI) / `ZAPI_<name>` (API) | 30 | `ZUI_SalesOrder` |
| Service binding | `<service definition>_O4` / `_O2` / `_V4` / `_V2` | 26 | `ZUI_SalesOrder_O4` |
| Message class | `Z<name>` | 20 | `ZSD_ORDER` |
| Lock object | `EZ<table>` | 16 | `EZSD_ORDER` |
| Authorization object | `Z<name>` | 10 | `ZSD_ORDER` |
| Transformation | `Z<name>` | 40 | `ZSD_ORDER_TO_JSON` |

Within classes, local classes use `lcl_`, local test classes `ltc_`, local test doubles `ltd_`, and local interfaces `lif_` unless the customer defines otherwise.
