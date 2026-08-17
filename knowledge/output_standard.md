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

## Executive summary behaviour

The first two pages should communicate:

- what the project does;
- whether the technical work is ready;
- whether governance is complete;
- whether sign-off can proceed;
- the most important outstanding actions.

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

## Status presentation

Use consistent status wording:

- COMPLETE
- PENDING
- NOT APPLICABLE
- RISK ACCEPTED
- DRAFT

Where supported by the rendering system, status may also be presented with
consistent visual indicators.

Text status must always remain visible; do not rely on colour alone.

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