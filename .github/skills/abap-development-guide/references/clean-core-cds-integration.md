# Clean Core, CDS, and Integration

## Source scope

Based on Clean Core, pp. 32-52; Core Data Services, pp. 53-67; and Integration, pp. 220-225.

## Clean Core and extensions

- Prefer SAP standard processes and supported extension options over direct modifications to SAP code.
- Never copy SAP code as a starting point for customer development; use released APIs, extension points, side-by-side or in-app extensibility, and documented modification options as appropriate.
- Use the Clean Core Level Concept when choosing an API: Level A is ABAP Cloud; Level B is classic ABAP allowed under Clean Core; Level C is SAP-internal or conditionally permitted; Level D has no usable API and must not be used. Prefer C1-released APIs for ABAP Cloud.
- If a needed API is not released, isolate it behind a wrapper and submit an SAP influence request where appropriate.
- Reports are not part of ABAP Cloud. Use a Fiori/RAP application for interactive scenarios or an Application Job for background processing.
- Prefer current replacements for legacy technologies: application log APIs such as `CL_BALI_OBJECT_HANDLER` over `SLG0`/`SLG1`, `CL_BCS_MAIL_MESSAGE` over `CL_BCS`, RAP over BOPF, and Business Configuration over `SM30` maintenance where the target supports them.
- Evaluate the transformation path, technology, organization, process, and add-on implications before selecting an extension approach.
- Keep customer code and dependencies structured so future S/4HANA, ABAP Cloud, and SAP upgrades remain manageable.
- Treat Clean Core as an architectural concern distinct from Clean ABAP: Clean ABAP improves code quality; Clean Core governs how solutions extend and interact with SAP standard.

## CDS

- Use the appropriate CDS view type and VDM layer for the consumption scenario.
- Apply naming conventions, annotations, associations, access control, and extensibility rules consistently with the model.
- Prefer view entities and supported modeling options when available in the target release.
- Treat CDS access control as part of the data-access security design, not as a substitute for every business authorization check.
- Keep projection, consumption, analytical, and interface responsibilities distinct.

## Integration

- Select integration technologies such as IDoc, RFC, SOAP, OData, HTTP, or events based on the business and lifecycle requirements.
- Prefer stable, released interfaces and explicit contracts at system boundaries.
- Consider future development, existing legacy technology, sustainable architecture, and Clean Core when handling borderline cases (pp. 223-224).
- Validate authentication, authorization, input, error handling, retries, monitoring, and data volume for every integration boundary.
