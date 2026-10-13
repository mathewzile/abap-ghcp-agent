# Names, Language, and Constants

## Names

- Use descriptive, pronounceable names that convey meaning and use solution-domain or business-domain terminology.
- Prefer consistent `snake_case` for local names, interfaces, methods, and variables where project conventions allow it.
- Use nouns or noun phrases for classes and interfaces; use verbs or verb phrases for methods. Boolean methods commonly start with `is_`, `has_`, or `can_`.
- Prefer plural names for collections and use one term consistently for one concept.
- Avoid unnecessary abbreviations, noise words such as `data`, `info`, and `object`, and names that obscure ABAP built-in functions.
- Avoid Hungarian notation and technical prefixes for variables and parameters in new code. In legacy objects, do not mix old and modern naming styles within one development object.
- Follow the project's repository-object naming convention, including required module prefixes such as `ZCL_PM_AUFTRAG`; avoid non-descriptive object names such as `ZCL_DATA` or `ZCL_FORMULAR3`.
- Use design-pattern names only when the class really implements that pattern.

## Language

- Prefer object orientation over procedural code. Keep reports, function modules, and framework exits thin and delegate business logic to classes.
- Prefer functional and expression-oriented syntax where it improves readability: inline declarations, `NEW`, `VALUE`, `COND`, `SWITCH`, table expressions, and string templates.
- Avoid obsolete language elements when the supported release permits a modern equivalent. Use escaped host variables in Open SQL.
- Check the lowest supported ABAP release before using newer syntax. Clean code rules for names, structure, and comments still apply to older releases.
- Do not optimize based on fear. Measure real bottlenecks, especially database time, before sacrificing clarity.

## Constants and enumerations

- Replace meaningful magic numbers and coded literals with descriptive constants or enumerations.
- Name constants for their meaning, not merely their value or type.
- Prefer ABAP enumerations where the release supports them. Otherwise group related constants and keep unrelated constants separate.
- Do not introduce constants that merely repeat an already self-explanatory literal.

## Newer language features

- Use `FINAL( variable )` for immutable local values where the target release is 7.57 or higher.
