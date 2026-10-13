# ABAP Unit Reference

## Design for testability

- Design production code so it can be tested automatically. Put replaceable dependencies behind interfaces and inject them through the constructor.
- Prefer dependency inversion and ABAP test doubles over setter injection, production-only test switches, or subclass-based mocks. Use test seams only as a temporary legacy workaround and remove them during modernization.
- Test public behavior and interfaces, not private implementation details. If private logic is hard to test, consider extracting a concept into its own class.
- Use `LOCAL FRIENDS` only to access a dependency-injecting constructor; never use it to alter private state or test private implementation details.
- Avoid mocking simple value objects and dependencies that the test does not use.

## Test classes and methods

- Put unit tests in the local test include of the class under test. Use separate global test classes for component, integration, or system tests.
- Name test classes and methods after their purpose and expected outcome, for example `throws_on_invalid_input` or `reads_existing_entry`.
- Structure each test as Given, When, Then. Keep the When section to one call to the code under test whenever possible.
- Keep test setup simple and explicit. Do not build a test-case framework or add teardown unless external resources require cleanup.
- Name the code under test meaningfully or `cut`, type it as an interface where practical, and extract complex calls into test helpers.
- Test public contracts through interfaces. Declare `FOR TESTING RAISING` to forward unexpected exceptions rather than catching everything and failing with a vague message.

## Test data and assertions

- Make important test data meaningful and make deliberately meaningless values obvious. Use constants when a value expresses purpose or is reused.
- Prefer a few focused assertions and the most specific assertion available from `cl_abap_unit_assert` or the project test library.
- Use `cl_abap_unit_assert`; do not use obsolete `cl_aunit_assert`.
- Assert content or a meaningful quality, not only row counts or incidental implementation details.
- Use custom assertions when they remove repeated, domain-specific assertion code.
- Use `cl_abap_unit_assert=>fail( )` when an expected exception is not raised. Test expected exception types and relevant context.
- Do not chase arbitrary coverage targets or create dummy assertions. Cover important behavior, boundaries, failures, and authorization-sensitive paths.

## Test doubles

- Use `cl_abap_testdouble` for class dependencies, `cl_function_test_environment` for function modules, and `cl_osql_test_environment` for database, CDS, or AMDP isolation where appropriate.
- Needing extensive test doubles can indicate that the production architecture needs simpler dependencies. Apply Clean ABAP rules to test code as well as production code.
