---
name: "Verify Naming Conventions"
description: "End-to-end dry-run test that the solution architect and ABAP developer agents resolve customer naming profiles per destination, fall back to defaults correctly, and follow the development guidelines."
argument-hint: "ADT destination ID to test against, e.g. XBB_DEV"
agent: "agent"
---
# Verify Naming Conventions

Run a repeatable, non-destructive end-to-end test of customer naming resolution defined in `.github/skills/abap-development-guide/references/naming.md`. Use the destination supplied with the prompt; if none is given, list ADT destinations and ask which one to use.

## 1. Set up the mock profile

1. If `.github/customer/systems.md` exists, copy it to `.github/customer/systems.md.bak`. Never lose real customer configuration.
2. Write `.github/customer/systems.md` containing only this row for the chosen destination: `| <destination> | DEV | zztest |`.
3. Create `.github/customer/zztest/naming-objects.md`. It is deliberately partial to test fallback:

   ```markdown
   Namespace: `Z`
   Unlisted types: default

   | Object type | Pattern | Max | Example |
   | --- | --- | --- | --- |
   | Class | `ZCL_ZT_<module>_<name>` | 30 | `ZCL_ZT_SD_PRICING` |
   | Exception class | `ZCX_ZT_<module>_<name>` | 30 | `ZCX_ZT_SD_PRICING` |
   | Interface | `ZIF_ZT_<module>_<name>` | 30 | `ZIF_ZT_SD_RULE_REPO` |
   | Database table | `ZZT<module><name>` | 16 | `ZZTSDDISC` |
   | CDS view entity | `ZZT_I_<name>` | 30 | `ZZT_I_DiscountRule` |

   Module codes: SD = Sales
   ```

4. Create `.github/customer/zztest/naming-variables.md` with Hungarian rules: locals `lv_/ls_/lt_/lo_`, attributes `mv_/ms_/mt_/mo_`, importing `iv_/is_/it_/io_`, returning `rv_/rs_/rt_/ro_`, caught exceptions `lx_`, class constants `gc_`.

## 2. Run the solution architect

Invoke the `abap-solution-architect` agent as a subagent with:

- Target project: the chosen destination.
- Requirement: a custom table of discount rules (customer group, minimum order quantity, discount percentage, validity dates); a CDS view entity exposing the rules; a reusable class returning the highest applicable discount percentage for customer group, quantity, and date (no rule returns 0, invalid input raises an exception); rule access behind an injectable interface with ABAP Unit tests. No UI.
- Non-interactive: record open decisions as numbered assumptions and continue.
- Mandatory: in the object inventory's "Naming evidence" column, state for each object whether the name comes from the customer profile or the default, citing the row. Include a "Variable naming" line in the handoff.

## 3. Run the ABAP developer

Invoke the `modern-abap-developer` agent as a subagent with the architect's work package 1 handoff and these constraints:

- DRY RUN: do not create, change, activate, or transport repository objects. ADT creation validation of names is allowed.
- Resolve naming independently from the profile files; flag any architect name that violates the profile, the defaults, or a maximum length.
- Return complete draft sources and a verification table: every object, parameter, attribute, variable, constant, type, and local class name, with the rule applied and its source.

## 4. Evaluate

Check both outputs against this list and mark each item pass or fail with evidence:

| # | Expected |
| --- | --- |
| 1 | Both agents resolve the destination to profile `zztest` from `systems.md`. |
| 2 | Class, exception class, interface, table, and CDS names follow the `zztest` patterns and maximum lengths. |
| 3 | Package, data elements, and message class use workspace defaults and are flagged "default - not in customer profile". |
| 4 | Variables, parameters, attributes, constants, and caught exceptions use the `zztest` Hungarian prefixes, not Clean ABAP. |
| 5 | Local test classes use `ltc_`, test doubles `ltd_`, other local classes `lcl_`. |
| 6 | Framework signature names (exception constructor `textid`, `previous`) remain unprefixed. |
| 7 | No customer pattern is invented by analogy for unlisted types. |
| 8 | The developer catches any architect naming error, or none exist. |
| 9 | Guidelines are followed: released APIs only, injectable seam with test double, test-first slices, `FINAL` classes, no repository objects created. |

## 5. Clean up and report

1. Delete `.github/customer/zztest/`.
2. Restore `.github/customer/systems.md` from the `.bak` copy and delete the backup; if there was no backup, delete `systems.md`.
3. Confirm with `git status --ignored .github/customer` that only the original state remains.
4. Report the evaluation table, any naming-setup gaps found, and recommended fixes. Do not apply fixes without confirmation.
