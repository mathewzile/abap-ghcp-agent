# Variable Naming

<!-- Copy to .github/customer/<profile>/naming-variables.md. Delete rows you do not need; missing kinds fall back to Clean ABAP (no prefixes). -->

| Kind | Rule | Example |
| --- | --- | --- |
| Local variable | `lv_` / `ls_` / `lt_` / `lo_` / `lr_` by type | `lv_order_id`, `lt_items` |
| Global (class attribute) | `mv_` / `ms_` / `mt_` / `mo_` | `mt_buffer` |
| Static attribute | `gv_` / `gs_` / `gt_` / `go_` | `go_instance` |
| Importing parameter | `iv_` / `is_` / `it_` / `io_` | `iv_order_id` |
| Exporting parameter | `ev_` / `es_` / `et_` / `eo_` | `et_messages` |
| Changing parameter | `cv_` / `cs_` / `ct_` / `co_` | `cs_header` |
| Returning parameter | `rv_` / `rs_` / `rt_` / `ro_` | `rv_result` |
| Field symbol | `<ls_>` / `<lt_>` / `<lv_>` | `<ls_item>` |
| Iteration variable (`FOR`, `LOOP ... INTO DATA( )`) | same as local variable | `ls_item` |
| Caught exception | `lx_` | `lx_error` |
| Local constant | `lc_` | `lc_max_items` |
| Class / interface constant | `gc_` | `gc_status_open` |
| Type definition | `ty_` (structure/elementary) / `tt_` (table) | `ty_rule`, `tt_rules` |
| Selection-screen parameter / select-option | `p_` / `s_` | `p_bukrs`, `s_vbeln` |
| Local class / test class / test double / interface | `lcl_` / `ltc_` / `ltd_` / `lif_` | `ltd_rule_repo` |

Names fixed by SAP framework signatures (e.g. exception constructor `textid`, `previous`) are exempt.
