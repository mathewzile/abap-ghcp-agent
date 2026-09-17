# Modern ABAP and Architecture

## Source scope

Based on Modern ABAP Development, pp. 68-107, especially architecture and structuring (pp. 70-76), design and development of modern SAP applications (pp. 76-86), Clean ABAP and modern language tools (pp. 87-99), and RAP (pp. 100-107).

## Guidance

- Treat architecture and structure as the foundation of maintainable SAP applications; do not begin with isolated statements or framework objects without considering boundaries.
- Use packages and package hierarchies to define responsibilities and restrict unwanted dependencies. In ABAP Cloud, use software components to enforce these boundaries.
- Prefer object-oriented design for business logic. Apply SOLID principles and use a design pattern only when its responsibilities and collaborators remain simpler than the alternative.
- Keep procedural entry points such as reports, function modules, and form routines thin; delegate behavior to testable classes where the framework allows it.
- Design for testability through clear dependencies and replaceable collaborators.
- Refactor existing applications incrementally. Avoid broad rewrites that mix behavior changes with unrelated cleanup.
- Use Clean ABAP as the code-level foundation together with the project's release and framework constraints. See the separate `clean-abap` skill for detailed rules.
- Prefer modern language tools supported by the target release; confirm syntax availability before changing older systems.
- Use ABAP Cleaner in ADT for standardized cleanup and formatting; the guide considers it essential for modern ABAP development (p. 99).
- For RAP, prefer draft handling unless a valid reason excludes it, prefer Fiori Elements over Freestyle UI where it meets the requirement, and use managed behavior unless unmanaged implementation is necessary. Do not use RAP productively on releases before 2021; expose extension points deliberately.

## Review questions

- Is the object in the correct package and are its dependencies intentional?
- Is business logic separated from framework or UI plumbing?
- Can the important behavior be tested without real external dependencies?
- Is the chosen design pattern necessary and understandable?
- Does the change preserve the intended Clean Core and RAP boundaries?
