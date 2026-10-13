# ABAP Security

## Source scope

Based on Security, pp. 226-253: common vulnerabilities (pp. 229-230), threats (pp. 232-235), secure development (pp. 236-242), secure reviews and automated testing (pp. 242-243), examples (pp. 244-247), and ABAP Test Cockpit/security checks (pp. 248-253). Screen Personas is covered separately on pp. 254-261.

## Required security posture

- Consider security from the beginning of development, not only during incident response or final review.
- Validate external and user-controlled input before using it in database statements, dynamic programming, file paths, commands, or output.
- Use fixed table and field names. Never build a dynamic `WHERE` condition from user input; implement allowed choices through a whitelist such as `CASE`.
- Avoid `CLIENT SPECIFIED`, `EXEC SQL`, and cross-client access unless the design explicitly requires them and the risk is controlled.
- Encode output appropriately to prevent cross-site scripting in SAP web applications.
- Perform authorization checks at the correct business boundary. Do not rely on UI restrictions alone, and protect against insecure direct object access and authorization bypass.
- Do not execute `MODIFY` without verifying authorization. Check `sy-subrc` immediately after `AUTHORITY-CHECK` and never use dummy authorization values such as `ACTVT = ' '`.
- Treat dynamic programming, generic module calls, `CALL 'SYSTEM'`, ABAP command execution, and similar mechanisms as high-risk. Avoid them where possible and strictly constrain and validate any unavoidable use.
- Protect client/data separation and secure file access, including path traversal prevention.
- Include security-focused code review, automated security testing, ATC checks, Code Vulnerability Analyzer checks, and the project's security checklist in the development process.

## Review questions

- Can an untrusted caller influence a query, object key, file path, command, or generated code?
- Is authorization checked for the actual business operation and object, not merely for the screen or endpoint?
- Are errors and logs free of sensitive data?
- Does ATC or the project's security tooling cover this object and deployment target?
