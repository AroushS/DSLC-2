# Evidence Rules

## Core rule

Always review all available project evidence before asking the user for information.

Do not ask questions where the answer can reasonably be verified from supplied evidence.

The agent's role is to locate, assess and trace evidence before generating Stage 1 documentation.

---

## Evidence source priority

Use the most authoritative source for the type of information being assessed.

### Business information

Prefer:

1. Use Case Shaping / approved business documentation
2. Solution Design
3. README
4. Explicit user clarification

Use these sources for information such as:

- business problem
- scope
- expected value
- stakeholders
- Product Owner / business ownership
- success criteria

Do not derive business ownership or approval from technical implementation evidence.

---

### Technical implementation

Prefer:

1. Training / feature engineering / scoring notebooks
2. Production code or pipeline configuration
3. Technical design documentation
4. README
5. Explicit user clarification

Use these sources for information such as:

- datasets
- features
- preprocessing
- model type
- training approach
- scoring approach
- technical dependencies
- production implementation

For determining what was actually implemented, direct implementation evidence should normally be preferred over summary documentation.

---

### Validation

Prefer:

1. Validation notebook
2. Training notebook containing explicit validation evidence
3. Modelling report
4. Explicit user clarification

Use these sources for information such as:

- holdout validation
- out-of-time validation
- cross-validation
- final validation metrics
- reproducibility checks
- scoring verification

Do not treat training performance alone as validation evidence.

---

### Governance

Use only explicit governance evidence.

Examples include:

- approval records
- AI Inventory reference
- Data Governance approval
- sign-off records
- governance questionnaires
- risk acceptance records
- formal review evidence

Never infer governance completion from technical work.

Never infer approval because a model exists, has good performance or is already in production.

---

## Example

To determine model type:

1. Check the training notebook.
2. Check implementation code or the model pipeline.
3. Check the validation notebook where relevant.
4. Check the README.
5. Ask the user only if the model type is still unclear.

Do not ask the user for information already supported by project evidence.

---

## Missing evidence

If required information cannot be verified:

1. identify exactly what information or evidence is missing;
2. record which relevant evidence sources were checked;
3. determine the appropriate status using `knowledge/governance_rules.md`;
4. explain what evidence or clarification would resolve the gap.

Do not automatically assume that missing evidence always means PENDING.

For conditional requirements, the governance rules may determine that the item is NOT APPLICABLE where the condition genuinely does not apply.

---

## Conflicting evidence

If sources disagree:

1. identify the conflict;
2. do not silently merge contradictory information;
3. prefer direct implementation evidence for what was actually built;
4. prefer formal approved documentation for ownership, governance and approvals;
5. ask the user where ambiguity remains.

Record unresolved material conflicts in the generated Stage 1 draft.

---

## Evidence traceability

For every major Stage 1 requirement, the agent should be able to identify:

- the evidence source used;
- what that evidence demonstrates;
- whether the evidence is sufficient;
- what remains missing, if anything.

This evidence assessment should be completed before the final Stage 1 document is written.

---

## Reference material

Reference examples and templates are never project evidence.

They may be used only for:

- structure
- style
- terminology
- expected level of detail

Never copy project-specific facts from reference material.

---

## General evidence rules

Never:

- invent evidence;
- invent metrics;
- invent owners;
- invent approvals;
- estimate missing project values;
- treat general Data Science knowledge as project evidence.

When evidence is uncertain, make the uncertainty visible rather than hiding it.