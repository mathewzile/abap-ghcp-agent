# Conditions, Classes, and Methods

## Conditions and control flow

- Prefer positive conditions and `IS NOT` over `NOT ... IS` when it improves readability.
- Decompose or extract complex conditions into intention-revealing variables or Boolean methods.
- Use predicative calls for Boolean methods when their semantics are unambiguous.
- Avoid empty `IF` branches. Prefer `CASE` for multiple mutually exclusive alternatives.
- Keep nesting shallow. Use guard clauses, validation methods, and early failure to keep the happy path visible.
- Prefer `RETURN` to clarify early method exits; use `CHECK` only in a method's initialization section if the team accepts its semantics. Do not use `CHECK` in loops; use `IF` with `CONTINUE`.
- Prefer simple string or built-in checks over regular expressions. Prefer basis checks such as `SEO_CLIF_CHECK_NAME` where available, and assemble complex expressions from named constants.

## Classes and objects

- Prefer objects and composition over static classes and inheritance. Static methods are mainly appropriate for stateless utilities or creation methods.
- Do not mix stateful and stateless responsibilities in one class.
- Make classes `FINAL` unless inheritance is intentional and designed. A non-interface class that consumers must mock can remain non-final until it is redesigned. Keep members `PRIVATE` by default and expose only required behavior.
- Prefer public instance methods through interfaces so dependencies can be replaced in tests.
- Use local classes for genuinely local helpers, not as containers for unrelated global functionality.
- Prefer `NEW` over `CREATE OBJECT`, except where dynamic construction requires the older form.
- For global `CREATE PRIVATE` classes, keep the `CONSTRUCTOR` public as required by ABAP syntax. Prefer named static creation methods such as `new_from_template` over optional constructor parameters.
- Do not use singletons by habit; use them only when one shared instance is a design requirement.
- For immutable value objects, read-only public data can be clearer than trivial getters; do not use `READ-ONLY` as a blanket rule for mutable state.

## Method calls and signatures

- Prefer functional calls and omit optional `RECEIVING` and `EXPORTING` keywords when the call remains clear.
- Omit `me->` for ordinary instance calls unless it resolves a name conflict. Qualify static calls through the class.
- Do not call static methods or access types through an instance. Omit the parameter name in clear single-parameter calls.
- Prefer instance methods over static methods and use interfaces for public replaceable behavior.
- Aim for fewer than three importing parameters. Split methods instead of adding many optional parameters or Boolean switches.
- Prefer one meaningful result via `RETURNING`; avoid mixing `RETURNING`, `EXPORTING`, and `CHANGING` without a strong reason.
- Returning large tables is usually appropriate; change this only with measured evidence. Name a returning parameter `result` unless a more specific name improves clarity, and use `PREFERRED PARAMETER` sparingly.
- Use `CHANGING` only when an already-populated caller variable is intentionally updated.
- Clear or overwrite non-value `EXPORTING` reference parameters. Do not clear `VALUE` or `RETURNING` parameters, and avoid interfaces where input and output can be the same variable.
- Keep each method focused on one responsibility and one abstraction level. Aim for 3-5 statements and generally fewer than 20, while allowing measured performance and framework constraints to justify exceptions.
- Validate early, fail fast, and preserve a clear happy path. Do not use exceptions for ordinary expected alternatives.
