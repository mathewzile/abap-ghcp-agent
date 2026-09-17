# Variables, Tables, Strings, and Booleans

## Variables

- Prefer inline declarations at first use when scope remains clear. Do not use a variable outside the statement block where it is declared; declare it earlier if it is needed later.
- Avoid chained declarations and unnecessary upfront declaration sections.
- Choose loop targets deliberately: use field symbols for in-place manipulation when appropriate, references when references must survive the loop, and data objects when a value copy is intended.
- Avoid field symbols for generic or dynamic access when modern dereferencing and expressions are available.

## Internal tables

- Choose `STANDARD`, `SORTED`, or `HASHED` based on size, mutation frequency, access pattern, key usage, and ordering requirements.
- Avoid `DEFAULT KEY`; use an explicit key or `EMPTY KEY` when no key is needed.
- Prefer `INSERT ... INTO TABLE` unless appending to an array-like standard table is intentional.
- Use `line_exists( )` for existence checks, table expressions for keyed access, `READ TABLE` when a row is needed, and `LOOP AT ... WHERE` instead of looping everything and filtering inside.
- Avoid duplicate reads. If a row is expected, read it once and handle `cx_sy_itab_line_not_found`; use optional table expressions for genuinely optional data.

## Database access

- Follow the project convention: select only required fields, avoid `SELECT *`, database access in loops, and nested loops where a join or keyed access expresses the operation.
- Use escaped host variables in Open SQL and measure before applying performance-driven complexity.

## Strings

- Use backticks for fixed string literals where supported and use string templates with `|...|` to assemble text.
- Keep text construction readable; do not use templates for a fixed literal or long chains of concatenation for interpolated text.

## Booleans

- Use `abap_bool` with `abap_true` and `abap_false` for Boolean values.
- Use `abap_boolean` for DDIC or Dynpro fields that need a dictionary type.
- Do not use `'X'`, `space`, or `IS [NOT] INITIAL` as Boolean comparisons.
- Use `xsdbool( )` to convert a condition to `abap_bool` where appropriate.
- Prefer predicative method calls for Boolean methods when the return type has clear true/false semantics.
- Challenge Boolean attributes and input parameters when they actually represent multiple states or two different operations; use an enumeration or separate methods instead.
