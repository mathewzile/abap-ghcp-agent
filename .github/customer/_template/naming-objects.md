# Repository Object Naming

<!-- Copy to .github/customer/<profile>/naming-objects.md. Rows are prefilled with workspace defaults: adapt every row you use so one package does not mix customer and default styles. -->

Namespace: `Z` <!-- or a registered namespace such as /ACME/ -->
Unlisted types: default <!-- default = use workspace default and flag it; ask = ask the user -->
ATC naming check variant: <!-- optional, e.g. Z_NAMING; authoritative when set -->
Source: <!-- optional, e.g. customer development guideline v2.1 -->

| Object type | Pattern | Max | Example |
| --- | --- | --- | --- |
| Package | `Z<module>_<name>` | 30 | `ZSD_ORDER` |
| Class | `ZCL_<module>_<name>` | 30 | `ZCL_SD_ORDER_PRICING` |
| Exception class | `ZCX_<module>_<name>` | 30 | `ZCX_SD_ORDER` |
| Interface | `ZIF_<module>_<name>` | 30 | `ZIF_SD_ORDER_REPOSITORY` |
| Program | `Z<module>_<name>` | 40 | `ZSD_ORDER_CLEANUP` |
| Function group | `Z<module>_<name>` | 26 | `ZSD_ORDER` |
| Function module | `Z_<module>_<name>` | 30 | `Z_SD_ORDER_READ` |
| Database table | `Z<module><name>` | 16 | `ZSDORDER` |
| Structure | `ZS_<module>_<name>` | 30 | `ZS_SD_ORDER` |
| Table type | `ZTT_<module>_<name>` | 30 | `ZTT_SD_ORDER` |
| Data element / domain | `Z<module>_<name>` | 30 | `ZSD_ORDER_STATUS` |
| CDS interface view | `ZI_<module>_<name>` | 30 | `ZI_SD_SalesOrder` |
| CDS RAP root view | `ZR_<module>_<name>` | 30 | `ZR_SD_SalesOrder` |
| CDS projection view | `ZC_<module>_<name>` | 30 | `ZC_SD_SalesOrder` |
| Behavior definition | Same as the root entity | 30 | `ZR_SD_SalesOrder` |
| Behavior pool | `ZBP_<root entity without leading Z>` | 30 | `ZBP_R_SD_SalesOrder` |
| Service definition (Fiori UI) | `ZUI_<module>_<name>` | 30 | `ZUI_SD_SalesOrder` |
| Service definition (Web API) | `ZAPI_<module>_<name>` | 30 | `ZAPI_SD_SalesOrder` |
| Service definition (InA) | `ZIA_<module>_<name>` | 30 | `ZIA_SD_SalesOrder` |
| Service definition (SQL) | `ZSQL_<module>_<name>` | 30 | `ZSQL_SD_SalesOrder` |
| Service binding (OData UI) | `ZUI_<module>_<name>_O2` / `_O4` | 26 | `ZUI_SD_SalesOrder_O4` |
| Service binding (OData Web API) | `ZAPI_<module>_<name>_O2` / `_O4` | 26 | `ZAPI_SD_SalesOrder_O4` |
| Service binding (InA) | `ZIA_<module>_<name>` | 26 | `ZIA_SD_SalesOrder` |
| Service binding (SQL) | `ZSQL_<module>_<name>` | 26 | `ZSQL_SD_SalesOrder` |
| Message class | `Z<module>_<name>` | 20 | `ZSD_ORDER` |
| Authorization object | `Z<module><name>` | 10 | `ZSDORDER` |

Module codes: <!-- e.g. SD = Sales, MM = Materials Management, FI = Finance -->

<!-- Service binding max is 26: keep OData service definition names at 23 or fewer characters so the _O2/_O4 suffix fits. -->
