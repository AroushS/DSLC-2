# Document Design Standard

## Design principle

The final Stage 1 document must be designed for rapid review by business,
technical and governance stakeholders.

The document should not resemble a raw Markdown export or notebook summary.

The reader should be able to understand the project's Stage 1 readiness
within the first two pages.

## Information hierarchy

Prioritise information in this order:

1. overall Stage 1 readiness;
2. major blockers;
3. business purpose and value;
4. technical and validation evidence;
5. governance position;
6. detailed evidence and technical appendices.

Do not give every piece of information equal visual importance.

## Executive readiness dashboard

The first page should function as an executive readiness dashboard.

A reviewer should be able to quickly determine:

- the overall Stage 1 position;
- which major areas are complete;
- which areas require attention;
- the key action or gap for any incomplete area;
- where to navigate for further detail.

The dashboard must remain concise and should not reproduce detailed evidence.

Use consistent visual status indicators where supported by the renderer:

- green for sufficiently evidenced / complete areas;
- amber for partial, pending or clarification-required areas;
- red for outcomes that currently prevent Stage 1 progression;
- neutral styling for not-applicable areas.

Colour is a visual aid only. The written status must always remain visible.

Visual presentation must not change, override or independently calculate the governance status.

## Main body vs appendix

Keep the main body concise.

Move detailed technical information to appendices where possible.

Examples that should normally be moved to an appendix:

- long dataset/table identifiers;
- full hyperparameter lists;
- full feature lists;
- file paths;
- extensive notebook references;
- detailed evidence locations.

## Tables

Use tables only when they improve comparison or status visibility.

Avoid creating separate tables for every governance check.

Prefer one consolidated governance table.

Avoid tables where long technical identifiers cause poor wrapping or unreadable layout.

---

## Navigation and usability

The final Stage 1 document must support rapid navigation.

The document should provide:

- an executive Readiness Dashboard near the beginning of the document;
- a Table of Contents;
- navigation from the Readiness Dashboard to the relevant detailed sections;
- an Evidence Register for detailed evidence traceability.

The Readiness Dashboard should show:

- Stage 1 area;
- current status;
- the most important gap or action;
- the relevant detailed section.

Navigation is a presentation feature only.

Navigation must never:

- change a Stage 1 status;
- change a governance conclusion;
- create evidence;
- imply that a requirement is complete;
- replace evidence assessment.

If a navigation link cannot be created, retain the readable section name rather than failing document generation.

---

## Status consistency

Use only the statuses defined in `knowledge/governance_rules.md`:

- COMPLETE
- PENDING
- NOT APPLICABLE
- RISK ACCEPTED
- DRAFT

Do not introduce alternative statuses such as:

- PARTIAL;
- EVIDENCE PRESENT;
- PASS;
- FAIL;
- APPROVED.

Visual colours may be used to make status easier to understand, but colour must not create or change status.

The written governance status is always authoritative.

---

## Evidence presentation

Appendix A — Evidence Register is the authoritative location for detailed evidence traceability.

Do not repeatedly reproduce evidence locations throughout the main report.

Where useful, the main report may identify the evidence source by name, but detailed file paths and links should normally remain in the Evidence Register.

For evidence locations:

- use a clickable verified link where one is safely available;
- otherwise use a verified relative path;
- otherwise use `Location not available`.

Failure to create a hyperlink must never prevent Stage 1 document generation.

Never display a guessed or constructed evidence URL.

---

## Graceful degradation

Optional presentation features must not cause the complete Stage 1 generation to fail.

If:

- a GitHub link cannot be verified, use the verified relative path;
- no evidence location can be verified, use `Location not available`;
- an internal navigation link cannot be created, retain the readable section name;
- automatic Table of Contents page numbers are not refreshed, retain the Table of Contents and allow Microsoft Word to update it;
- PDF generation is technically unavailable, still produce the editable DOCX.

Missing presentation functionality must not alter evidence assessment or governance status.

Missing required project evidence must continue to be handled according to `knowledge/evidence_rules.md` and `knowledge/governance_rules.md`.

## Callouts

Use callout boxes sparingly for:

- critical governance gaps;
- important assumptions;
- required actions;
- major limitations.

Do not place every note inside a callout box.

## Technical charts

Where meaningful charts already exist in project evidence, consider including
a small number of decision-relevant figures such as:

- ROC curve;
- gain/lift;
- SHAP summary;
- validation comparison.

Do not include charts solely for decoration.

## Length

Aim for a concise main report.

The main Stage 1 narrative should normally be approximately 8–12 pages,
excluding appendices, depending on project complexity.

Avoid unnecessary repetition to reach or fill a page count.

## Deliverables

A complete Stage 1 generation should produce:

1. `Stage1_<ProjectName>.docx`
2. `Stage1_<ProjectName>.pdf`

The DOCX is the editable master document.

The PDF is the controlled review/distribution copy.

The user should not need to explicitly request these formats.

Do not return only a Markdown file unless document rendering is technically unavailable.