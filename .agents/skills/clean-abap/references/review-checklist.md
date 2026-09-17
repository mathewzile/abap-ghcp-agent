# Clean ABAP Review Checklist

Review changed code in this order:

1. **Compatibility**: release level, framework rules, generated code, and existing local conventions.
2. **Behavior**: happy path, invalid input, missing data, authorization, concurrency, and error propagation.
3. **Design**: focused responsibility, clear names, small methods, minimal public surface, interfaces for dependencies.
4. **ABAP**: modern syntax where supported, explicit table keys, no unnecessary field symbols or duplicate reads.
5. **Database**: no avoidable `SELECT` in loops, no `SELECT *`, appropriate predicates and field list.
6. **Errors**: class-based exceptions, preserved context, no swallowed failures, no exception-driven normal flow.
7. **Tests**: focused ABAP Unit coverage for changed behavior and important boundaries.
8. **Quality**: formatter, transport impact, and performance evidence where relevant.

Report findings by severity and location. Distinguish required fixes from optional style improvements, and do not recommend broad refactoring unrelated to the change.
