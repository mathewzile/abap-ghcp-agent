# Errors, Comments, and Formatting

## Error handling

- Prefer class-based exceptions over return codes for exceptional situations. Do not allow failures to be silently ignored when a legacy API returns status values.
- Use exceptions for errors, not normal alternatives such as an optional lookup that legitimately finds nothing.
- Use checked exceptions for manageable failures that callers can reasonably handle; use unchecked categories only for failures callers cannot usefully recover from.
- Use `CX_DYNAMIC_CHECK` only for avoidable failures a caller consciously controls, and use `RAISE SHORTDUMP` only for totally unrecoverable situations or programming errors.
- Prefer `RAISE EXCEPTION NEW` where supported. Wrap foreign exceptions at component boundaries so callers depend on your error abstraction, while preserving the original exception as `previous`.
- Define abstract application exception superclasses where application-wide handling or common behavior is needed. Keep exception interfaces understandable and use subclasses for distinguishable failures.
- Make message references discoverable with `MESSAGE ... INTO DATA(message) ##NEEDED` when the text is not otherwise consumed.

## Comments and documentation

- Express intent through names, structure, and methods before adding comments.
- Comments explain why, constraints, compatibility decisions, or non-obvious behavior; they do not narrate the next statement.
- Use methods to separate conceptual steps instead of banner comments and long procedural blocks.
- Use quote comments before the statement they describe. Delete commented-out code and manual version-history markers; source control preserves history.
- Use `"` comments, not `*`; do not add method-signature or end-of-block comments. Keep design explanations in design documents rather than source code.
- Add an owner or identifier to `FIXME`, `TODO`, or `XXX` comments when they are genuinely necessary.
- Use ABAP Doc for public APIs and avoid duplicating message text in comments.
- Prefer ATC pragmas over obsolete pseudo-comments when suppressing a justified finding.

## Formatting

- Follow the team's ABAP Formatter settings and format before activation.
- Use one statement per line and a reasonable line length, commonly 120 characters.
- Optimize for reading and debugging. Use at most one blank line between concepts; do not align type clauses, but align assignments only when they target the same object.
- Keep parameters behind the call, indent multiline parameters consistently, and close brackets at the line end where the local formatter supports it.
- Indent inline declarations like method calls and use the team's tab indentation.
- Avoid chained assignments and gratuitous whitespace. Preserve surrounding formatting when editing legacy code unless formatting is part of the task.
