# Testing, ALM, and Quality

## Source scope

Based on Software Testing with ABAP Unit, pp. 108-142, and Application Lifecycle Management, pp. 174-196.

## ABAP Unit

- Define a testing strategy that matches the system, risk, and lifecycle; use the separate `clean-abap` skill for test design and ABAP Unit mechanics.
- Apply the guide's iterative quality mindset: Code - Test - Repeat (pp. 141-142).

## ALM and quality

- Use continuous developer self-review, peer code review, and quality gates in the release process (pp. 176-183).
- Configure automated checks for developer/background runs and transport-release online checks. Use code pal for ABAP, code pal for ABAP Cloud (`/CC4A/CODE_PAL`), abapOpenChecks, and S/4HANA readiness checks where applicable.
- Keep changes traceable and align development, testing, approval, and deployment with the team's ALM process. Apply the team's documented version-control and deployment recommendation.

## Review questions

- What behavior changed, and which test protects it?
- Has the change passed local checks and the project's quality gates?
- Is the change traceable to a requirement, defect, or transport?
- Are deployment and rollback impacts understood?
- Are version-control and review records sufficient for future maintenance?
