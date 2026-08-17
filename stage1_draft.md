# Stage 1 – Proof of Value

## Document Information

| Field | Value |
|---|---|
| Project / Use Case | Scaled Data Propensity to Call Model |
| Stage | Stage 1 – Proof of Value |
| Document Status | DRAFT |
| Date Generated | 12 August 2026 |
| Business / Product Owner | Alex Morgan – Broadband Service Experience / Service Checker (assumed placeholder — confirmation required) |
| Technical Owner | Sam Taylor – Data Science / Decisioning Models team (assumed placeholder — confirmation required) |
| Executive Sponsor | Jamie Roberts – Head of Broadband Customer Experience (assumed placeholder — confirmation required) |
| Stage Gate / Accountable Owner | PENDING — not confirmed from available evidence |
| DSLC Version | 2.0 |

---

# 1. Stage 1 Readiness

## Overall Readiness

NOT READY FOR SIGN-OFF

The technical development, feature engineering and validation work are substantially evidenced. The model is in active production within MLPod and a validation notebook demonstrates out-of-sample scoring performance. A Use Case Shaping document provides business context, stakeholder teams, owner placeholders and an epic reference; however, owner names are marked as assumed placeholders in that document and require human confirmation. Several mandatory governance requirements remain outstanding: AI Inventory registration, Data Governance approval and all three required sign-offs (Technical, Business and Final Stage 1). Stage 1 cannot proceed to sign-off until ownership is confirmed and these governance items are addressed.

## Readiness Summary

| Area | Status | Summary |
|---|---|---|
| Business / Use Case | Evidence Present | A Use Case Shaping document provides business problem, decision context, stakeholder teams, scope, success measures, owner placeholders and an epic reference. Owner names are marked as assumed placeholders and require human confirmation. |
| Data Readiness | Partial Evidence | Data sources and features are well documented in notebooks and README. Formal Data Governance approval and a formal Solution Design document have not been evidenced. |
| Technical Development | Evidence Present | LightGBM model trained, evaluated and in production. Preprocessing pipeline, feature selection and hyperparameters are fully documented in the training notebook. Multiple model versions developed and evidenced. |
| Validation | Evidence Present | A dedicated validation notebook exists and demonstrates out-of-sample scoring performance with standard classification metrics and ROC AUC. Five weeks of out-of-time validation is referenced in the README. |
| Governance | Pending | AI Inventory Registration, Data Governance approval, Business Review, Technical Review and all sign-offs are PENDING. No explicit approval evidence found in available artefacts. |
| Final Sign-off | Pending | Cannot be confirmed until all applicable governance items are complete and explicit approval evidence exists. |

## Priority Blockers

1. **Owner confirmation required.** Business/Product Owner (Alex Morgan – assumed placeholder), Technical Owner (Sam Taylor – assumed placeholder) and Executive Sponsor (Jamie Roberts – assumed placeholder) have been identified in the Use Case Shaping document but are marked as assumed placeholders. Human confirmation of each owner is required before sign-off can proceed.
2. **AI Inventory Registration absent.** No registration reference or ID found in any evidence source. The model is in production without confirmed registration.
3. **Business Review not evidenced.** No business review record, approval decision or review outcome was found in any available artefact. The Use Case Shaping document does not constitute a Business Review.
4. **Technical Review not evidenced.** No technical review record was found in available artefacts. Completed notebooks and production deployment do not constitute technical review.
5. **Data Governance approval not evidenced.** Multiple BigQuery datasets are used in training and scoring. No formal governance approval or Data Steward confirmation has been found.

## Project Summary

The Scaled Data Propensity to Call Model predicts the probability that a Hub4 broadband customer will contact Sky in the following week, combining Scaled Data telemetry health indicators with customer attributes, WHIX performance data and historical contact patterns. The model's probability outputs support proactive and targeted customer interventions by Broadband/Service Checker teams, Customer Service and Operations, allowing teams to prioritise the highest-risk customers for proactive treatment. The technical development is substantially complete: a LightGBM classifier has been built, evaluated on held-out test data, validated against an external out-of-sample dataset and is actively deployed in MLPod for weekly scoring. A Use Case Shaping document has been completed providing business context, owner placeholders and an epic reference; owner confirmation, AI Inventory registration, Data Governance approval and all required sign-offs remain outstanding before Stage 1 sign-off can proceed.

---

# 2. Business & Use Case

## Business Problem

The introduction of Scaled Data for Service Checker provides a richer view of the in-home health and broadband performance of Hub4 customers. A proportion of these customers experience degraded broadband or Wi-Fi quality and subsequently contact Sky agents. Identifying these customers in advance allows proactive treatment before they call, reducing reactive contact volume and improving customer experience.

This is a highly imbalanced binary classification problem: approximately 0.25% of Hub4 customers in the scoring population call within any given week.

## Decision Supported

The model supports prioritisation and filtering decisions: it ranks Hub4 customers by their predicted probability of calling in the next week. Teams or downstream systems can then apply a threshold or decile-based filter to identify cohorts for proactive treatment. The model's probability scores — rather than binary class labels — are the primary decision-support output, as class-label predictions were found to be unreliable under severe class imbalance.

Analysis of the most predictive features and SHAP importance values also provides a secondary use: identifying cohorts of customers in poor broadband health who may benefit from targeted interventions.

## Scope

### In Scope

- UK Hub4 broadband customers with available Scaled Data; IHH and BBH RAG/MOT status features.
- Hub telemetry, WHIX, PRISM and Customer Weekly Base features.
- Historical reactive call data as the target signal.
- Weekly propensity scoring and out-of-time validation.
- Analysis of SHAP feature importance and cohort identification.

### Out of Scope

- Customers without suitable Hub4 Scaled Data coverage (approximately 35% of Hub4 base).
- Real-time scoring: assessed and confirmed impractical given current data infrastructure.
- Non-broadband use cases.
- Direct automated customer treatment decisions.
- Prediction of specific contact reasons or resolution outcomes.
- Major upstream source-system changes.

## Expected Business Value

Reduce avoidable inbound service calls and associated service costs; improve targeting of proactive support; improve customer broadband experience by identifying likely issues earlier. The Use Case Shaping document confirms the following value areas: reduction in avoidable inbound service calls, improved targeting of proactive customer support and improved customer broadband experience through earlier issue identification.

Specific quantified benefit estimates are not available from the evidence provided. Benefit realisation depends on the treatments applied and the teams using the model output.

## Success Measures

**Technical success measures (from Use Case Shaping document and training notebook):**

- Useful out-of-time ROC AUC score confirming discrimination between callers and non-callers.
- Lift and gain across propensity deciles, enabling identification of highest-risk cohorts.
- High-propensity cohorts can be identified and selected for proactive treatment.
- Stable performance maintained across multiple out-of-time validation weeks (five weeks referenced in README).

**Business success measures (from Use Case Shaping document — not yet measurable):**

- Reduction in avoidable calls among treated customers versus a control group.
- Improved targeting efficiency in proactive treatment campaigns.

Specific numeric targets and acceptable performance thresholds have not been confirmed.

## End Users & Stakeholders

The Use Case Shaping document identifies the following end users and stakeholders:

- **End users:** Broadband / Service Checker teams, Customer Service, Operations, and teams running proactive customer treatments or campaigns.
- **Key stakeholders:** Service Checker team; Broadband Operations; Customer Service / Contact Centre; Proactive Treatment / Campaign teams; MLPod / model deployment team.

These are sourced from the Use Case Shaping document. Individual stakeholder names have not been confirmed beyond the owner placeholders listed in the Ownership & Delivery table.

## Ownership & Delivery

| Role / Item | Confirmed Information | Status |
|---|---|---|
| Business / Product Owner | Alex Morgan – Broadband Service Experience / Service Checker | Assumed placeholder — confirmation required |
| Technical Owner | Sam Taylor – Data Science / Decisioning Models team | Assumed placeholder — confirmation required |
| Executive Sponsor | Jamie Roberts – Head of Broadband Customer Experience | Assumed placeholder — confirmation required |
| Stage Gate / Accountable Owner | Not confirmed from available evidence | PENDING — confirm governance owner |
| Delivery Epic / Milestone | DSLC-CALL-001 – Scaled Data Propensity to Call | Assumed placeholder — verify epic reference |

Governance review and sign-off status is recorded in Section 7.

---

# 3. Data Readiness

## Data Overview

The model draws from five broad data domains:

- **Service Checker Scaled Data** — In-home health (IHH) and broadband health (BBH) RAG and MOT telemetry status indicators across multiple time windows, providing the core differentiating signals.
- **Hub Telemetry** — Hub-level reboot counts and device identifiers; also provides the scoring customer base.
- **WHIX Performance** — Average WHIX (Wi-Fi Health Index) scores for the week prior to assessment.
- **Customer Attributes** — Demographic, subscription, tenure and product data from PRISM and Customer Weekly Base.
- **Historical Contact Data** — Flags indicating whether the customer made a call in the prior 90 days.

Full physical dataset and table identifiers are listed in Appendix B.

## Data Suitability

The training dataset covers Hub4 customers for whom Scaled Data is available: approximately 65% of the Hub4 broadband base. This is an acknowledged constraint; approximately 35% of Hub4 customers cannot be scored using this model due to the absence of Scaled Data telemetry.

The target variable (`call_in_period_flag`) is available from historical contact data and is confirmed to be present in the training dataset. The class distribution is severely imbalanced at approximately 0.25% positive class (callers). The training dataset for model version 3 covered 27 June 2025 to 7 November 2025, producing approximately 1.9 million records after applying Scaled Data feature availability criteria to the full Hub4 base of approximately 3.5 million.

## Data Quality

The training notebook implements missing value analysis and removal as a documented preprocessing step. Columns with more than 25% missing values are excluded. Remaining missing values in numerical features are imputed using median imputation; remaining missing values in categorical features are imputed using most-frequent imputation, each fitted on training data only.

No evidence of explicit duplicate-record detection or broader data validity assessment has been identified from the available artefacts. The README notes that the training base table SQL script requires repointing to MLPod-hosted tables before any future retrain.

## Data Governance

No formal Data Governance approval or Data Steward review has been identified in the available artefacts. The datasets used are documented (see Appendix B), and the data appears to have been used under existing project access arrangements, but an explicit governance confirmation has not been found. Technical access to datasets does not constitute governance approval.

See Section 7 for the current Data Governance status.

## Deployment / Operational Data Considerations

The model is actively deployed in MLPod and scores on a weekly basis (Fridays). The scoring notebook connects to a production BigQuery scoring table maintained under the MLPod environment. The README confirms that data source tables were repointed from the original analytics project to MLPod-hosted equivalents after migration.

The SQL scripts directory contains `scoring.sql` (production dataset construction), `training_base_table.sql` (training data — requires repointing to MLPod tables for future retraining) and `validation.sql` (historical validation base).

---

# 4. Exploratory Analysis

## Analysis Performed

Exploratory analysis was conducted as part of the training notebook rather than as a standalone EDA artefact. The following analysis is evidenced from the training notebook:

- Dataset shape and record count.
- Date range of the scoring/check timestamp (`check_ts`).
- Class balance assessment: caller and non-caller counts and percentage breakdown.
- Missing value percentage calculation across all features, with programmatic column removal.
- Feature cross-correlation analysis used for feature selection.
- Feature correlation with the target variable.
- Top-feature histograms produced in the scoring notebook.

## Key Findings

| Finding | Why It Matters |
|---|---|
| Approximately 0.25% positive class (callers) | Severe class imbalance requires `is_unbalance=True` in the model and places the primary emphasis on probability outputs rather than binary predictions |
| Scaled Data available for approximately 65% of Hub4 base | Creates a meaningful coverage gap; approximately 35% of customers cannot be scored |
| Multiple time windows for telemetry features (time_of_call through prev_1wk) | Customers react to poor broadband health at different speeds; multiple windows capture both immediate and delayed calling behaviour |
| Cross-correlation analysis removed redundant features | Prevents multicollinearity from distorting feature importances; ensures the most target-relevant feature is retained in each correlated pair |
| Most predictive features include unreliable Wi-Fi duration, system reboots, WHIX score, prior contact history and tenure indicators | Confirms the expected signal: customers with observable in-home health issues and prior contact history are most likely to call |

## Data / Target Distribution

The target variable is severely imbalanced at approximately 0.25% positive class. This was addressed in the modelling approach through the `is_unbalance=True` LightGBM parameter. Sampling techniques (SMOTE, ADASYN, RandomOverSampler, RandomUnderSampler) were explored but not applied to the final model — the corresponding code is present and commented out in the training notebook, demonstrating that these approaches were considered.

## Implications

The severe class imbalance was the primary analytical challenge and shaped the modelling approach: binary class label predictions are unreliable and probability outputs are recommended as the primary model output. The 65% Scaled Data coverage constraint shapes the model's scope and means it cannot replace a full-population targeting solution.

The cross-correlation analysis shaped the final feature set: highly correlated pairs were pruned, retaining the feature with the stronger correlation to the target.

## Evidence Gap

A standalone EDA artefact (separate from the training notebook) is not evidenced. EDA findings are embedded within the training notebook. This should be confirmed as acceptable under the applicable DSLC process.

---

# 5. Feature Engineering

## Approach

Features were engineered across three broad categories:

1. **Scaled Data telemetry indicators** — RAG (Red/Amber/Green) and MOT status checks for IHH (In-Home Health) and BBH (Broadband Health) domains, calculated across seven time windows. Three measures were calculated for each status and window: duration (time spent in that status), count (number of status occurrences) and a binary any-flag (whether the status occurred at all).

2. **Customer and subscription attributes** — categorical features including age band, broadband type, tenure band, contract status, speed band, status code and household affluence; numerical features including tenure months, current offer amount and active product flags.

3. **Historical contact and performance indicators** — flags for calls in the prior 90 days, average WHIX score over the prior week, reboot counts.

## Key Feature Decisions

| Decision | Detail |
|---|---|
| Missing value imputation | Numerical: median. Categorical: most-frequent. Applied via SimpleImputer fitted on training data and applied to test and scoring data. |
| High-missingness column removal | Columns with more than 25% missing values removed before imputation. |
| One Hot Encoding | Applied to all 8 categorical features using OneHotEncoder with handle_unknown='ignore'. |
| Scaling | RobustScaler applied to numerical features post-OHE. Selected for outlier resistance, expected in telemetry data. Fitted on training data only. |
| Cross-correlation feature selection | Post-OHE feature pairs with correlation above 0.5 were identified. For each pair, the feature with the lower absolute correlation with the target was removed. |
| Multi-time-window approach | All telemetry features calculated across time_of_call, prev_3hr, prev_6hr, prev_12hr, prev_24hr, prev_48hr and prev_1wk windows. |

## Quality & Leakage Considerations

The preprocessing pipeline is reproducible: all components are serialised to pickle files (`scoring_pkl_files_3/`) and loaded consistently in production scoring. Transformations applied in production match those applied during training.

Target leakage is an acknowledged consideration. All time-window features represent the customer state at or before the point of assessment, not after the call event. A formal documented leakage audit has not been identified from the available evidence. This should be confirmed as part of the technical review.

## Rationale

The three-measure approach (any, duration, count) for RAG/MOT statuses was adopted because different patterns of poor health — such as a single extended outage versus frequent brief interruptions — may both drive calling behaviour but are only distinguishable when multiple measures are available. The multi-time-window design reflects that customers vary in how quickly they react to poor experience. The cross-correlation selection step prevents redundant features from inflating model complexity and distorting SHAP-based feature importance outputs.

Full pre- and post-processing feature lists are in Appendix C.

---

# 6. Model Development & Validation

## Model Overview

| Item | Detail |
|---|---|
| Problem type | Binary classification (caller / non-caller) |
| Final selected model | LightGBM (Light Gradient-Boosting Machine) classifier, version 3 |
| Primary output | Propensity probability score (0–1); binary class label also available |
| Training period | 27 June 2025 to 7 November 2025 |
| Scoring frequency | Weekly (Fridays) |
| Approximate training records | ~1.9 million Hub4 customers with Scaled Data |

## Model Development

Three model iterations are documented:

| Version | Key Change | Notes |
|---|---|---|
| v1 | Original model. OOT validation within notebook. Calibration using validation split. Train/test: 19 Jun – 02 Oct 2025. | First production-ready version. |
| v2 | Retrained with extended training period. Calibration performed using test set. | Calibration on test set identified as not best practice. |
| v3 | Calibration removed. Otherwise same as v2. Train/test: 27 Jun – 07 Nov 2025. Currently in production. | Selected version. Pickle files in scoring_pkl_files_3. |

Note: The training notebook contains the internal heading "v5 RETRAIN" while the README refers to the same file as v3. The README is used as the primary naming reference. This naming discrepancy should be confirmed with the project team.

The LightGBM algorithm was selected for its speed, ability to handle the high post-OHE feature count, native support for imbalanced datasets and interpretability via SHAP values. Sampling techniques were explored but not applied to the final model.

## Performance Summary

Quantitative performance results are computed at runtime in the training and validation notebooks. The following measures are evidenced as having been calculated:

| Measure | Evidence Source | Interpretation | Business Relevance |
|---|---|---|---|
| Train and test ROC AUC | Training notebook | Discrimination between callers and non-callers in train and test sets | Primary model quality indicator |
| Accuracy, Precision, Recall, F1 (test set) | Training notebook | Classification performance at 0.5 threshold | Limited direct utility given class imbalance |
| Confusion matrix (train and test) | Training notebook | Shows false positive and false negative volumes | Contextualises classification errors |
| Gain and Lift (test set) | Training notebook | Improvement over random targeting by decile | Direct indicator of targeting efficiency |
| ROC AUC (validation) | Validation notebook | Out-of-sample discrimination | Confirms hold-out generalisation |
| SHAP feature importances | Training notebook | Which features most influence predictions | Supports cohort analysis and intervention design |

Specific numeric results have not been extracted from notebook runtime outputs and are not presented here to avoid misrepresenting values that may have changed between runs. The README confirms that five weeks of out-of-time validation results are documented in the `validation_notebooks` folder, with v3 performing best after MLPod repointing. Human review should confirm acceptable performance thresholds.

## Validation

The dedicated validation notebook (`call_model_scoring_with_validation_2026_02_04`) provides out-of-sample validation evidence. The approach:

1. Score the production scoring dataset using the full fitted preprocessing pipeline and trained model.
2. Merge scored output with a separate validation BigQuery table containing actual `call_in_period_flag` labels for the same period.
3. Calculate accuracy, precision, recall, F1, confusion matrix and ROC AUC against ground-truth labels.
4. Assess propensity score distribution.

This validates the end-to-end scoring pipeline, not just the training evaluation, and confirms the model generalises to an unseen production dataset. The notebook is dated 04 February 2026, confirming post-training validation was performed in a production context.

The README additionally references a `validation_notebooks` folder containing five weeks of out-of-time validation, confirming that performance was monitored across multiple time periods.

## Business Interpretation

The model's primary output is the propensity probability score. Teams should prioritise the top deciles (highest-scoring customers) for proactive treatment, using the gain/lift charts to understand expected improvement over random targeting. Binary class labels at the default 0.5 threshold are not recommended as the primary decision tool under severe class imbalance.

SHAP analysis identifies which features contribute most to individual predictions, supporting interpretation and secondary use cases such as cohort identification for targeted intervention.

## Key Limitations

| Limitation | Detail |
|---|---|
| Scaled Data coverage gap | Approximately 35% of Hub4 customers do not have Scaled Data and cannot be scored. |
| Severe class imbalance | Positive class is approximately 0.25% of the population. Class-label predictions are unreliable; probability scores are the recommended primary output. |
| Real-time scoring not implemented | Weekly batch scoring was the implemented approach. Real-time scoring was assessed and confirmed impractical. |
| Training base table requires repointing | The training data SQL script requires updating to MLPod-hosted tables before any future retrain. |
| Formal target leakage audit not evidenced | A documented leakage audit report has not been identified from available evidence. |

None of these limitations carry confirmed human risk decisions. See Section 7 for governance items including AI Inventory registration and ownership confirmation.

Full hyperparameters and feature lists are in Appendix C.

---

# 7. Governance & Sign-off

This is the single authoritative governance status section in this document. Other sections reference Section 7 and do not reproduce governance status, reason or action detail.

| Governance Requirement | Status | Evidence / Gap | Required Action |
|---|---|---|---|
| Business Review | PENDING | A Use Case Shaping document has been completed capturing business context, scope, owner placeholders and success measures. However, this document does not constitute a formal Business Review: no named business reviewer, explicit review outcome or approval decision has been recorded. | Conduct a formal Business Review with a named business reviewer. Record the review outcome, approval decision and date. |
| Technical Review | PENDING | No technical review record or reviewer name found in available evidence. Completed notebooks and production deployment do not constitute technical review. | Confirm whether formal technical review is required under the applicable DSLC process. Obtain and record the technical review outcome with a named reviewer. |
| AI Inventory Registration | PENDING | No AI Inventory registration reference or ID found in any evidence source. The model is in production in MLPod but registration has not been confirmed. | Register the model in the organisation's AI Inventory. Record the registration reference and owner in this document. |
| Data Governance | PENDING | Multiple BigQuery datasets are used in training and scoring. No formal Data Governance approval or Data Steward review has been evidenced. Technical access to datasets does not constitute governance approval. | Obtain and document formal Data Governance confirmation for all datasets used in training and production scoring. |
| Deployment / Model Handover | PENDING | The model is deployed in MLPod. A scoring notebook, pickle files and SQL scripts are available. The Use Case Shaping document identifies the MLPod / model deployment team as a key stakeholder. No formal handover record, named deployment contact or written handover confirmation has been identified from available evidence. | Confirm the named deployment contact within the MLPod team. Produce and record a formal handover document. |
| Technical Sign-off | PENDING | No technical sign-off evidence found. Production deployment does not constitute technical sign-off. | Obtain explicit technical sign-off from the confirmed Technical Owner once the technical review is complete. |
| Business Sign-off | PENDING | No business sign-off evidence found. Business value does not constitute business sign-off. | Obtain explicit business sign-off from the confirmed Business/Product Owner once the business review is complete. |
| Final Stage 1 Sign-off | PENDING | Cannot be confirmed. Technical and business sign-offs are both PENDING. Multiple other governance items are outstanding. The agent cannot provide final approval. | Complete all applicable governance items. Obtain explicit Final Stage 1 sign-off from the confirmed Stage Gate / Accountable Owner. |

---

# 8. Risks & Limitations

| Risk / Limitation | Impact | Mitigation / Required Action | Status |
|---|---|---|---|
| Scaled Data coverage gap (~35% of Hub4 customers not scored) | A significant portion of Hub4 customers cannot be identified using this model. High-propensity callers outside Scaled Data coverage will not be captured. | Document the coverage constraint in communications to downstream users. Treat scored output as a subset of the total opportunity. | Known limitation |
| Severe class imbalance (~0.25% positive class) | Binary class label predictions are unreliable. The model may not be well-suited to use cases requiring high recall at the default threshold. | Primary output is the propensity probability score. Downstream users should be explicitly instructed not to use binary labels for targeting decisions. | Known limitation |
| Training data requires repointing to MLPod tables | Future retraining using the original training base table SQL will produce errors or incorrect results if tables have not been migrated. | Update `training_base_table.sql` to reference MLPod-hosted dataset equivalents before any future retrain. Confirm with the MLPod team which tables have been migrated. | Mitigation required |
| Ownership not confirmed | Without confirmed owners, governance reviews and sign-offs cannot proceed and operational responsibility is unclear. | Confirm Business/Product Owner and Technical Owner and record in DSLC documentation. | Mitigation required |
| Formal target leakage audit not evidenced | Without a documented leakage check, there is a risk that features derived at or after the call event may have been inadvertently included. | Conduct and document a formal target leakage review, confirming all features represent the customer state at the point of assessment (before the call event). | Mitigation required |

---

# 9. Stage 1 Recommendation

**What is sufficiently evidenced:**

The technical development for the Scaled Data Propensity to Call Model is substantially complete. A LightGBM binary classifier has been trained on a large Hub4 customer dataset using a well-documented and reproducible preprocessing pipeline. Feature engineering decisions are serialised and applied consistently in production scoring. A dedicated validation notebook demonstrates out-of-sample scoring performance against ground-truth call labels. The model is in active weekly production in MLPod. SHAP-based feature importance analysis supports interpretability and secondary use cases. Three model versions have been developed, evaluated and documented, with the calibration-free version 3 selected for production.

**What remains outstanding:**

Stage 1 governance is incomplete. None of the required governance approvals — Business Review, Technical Review, AI Inventory Registration, Data Governance, Deployment Handover, Technical Sign-off, Business Sign-off or Final Sign-off — have been confirmed from available evidence. Business and technical ownership are not confirmed. A delivery epic or roadmap reference has not been evidenced. A formal target leakage audit report is not available.

**Readiness for human review:**

This document is ready for human review of the technical content. It is not suitable for governance sign-off in its current state.

**Whether Stage 1 can proceed to sign-off:**

Stage 1 cannot currently proceed to sign-off. The governance framework must be completed before sign-off is appropriate.

**Highest-priority next steps:**

1. **Confirm owner names.** Alex Morgan (Business/Product Owner), Sam Taylor (Technical Owner) and Jamie Roberts (Executive Sponsor) are recorded in the Use Case Shaping document as assumed placeholders. Each must be confirmed by the named individual and recorded as a verified owner before governance reviews and sign-offs can proceed.
2. Register the model in the organisation's AI Inventory and record the registration reference.
3. Obtain formal Data Governance confirmation for all training and production scoring datasets.
4. Obtain and record a Business Review outcome from a named business reviewer.
5. Obtain and record a Technical Review outcome from a named technical reviewer (including confirmation of the leakage audit position).
6. Produce and confirm a formal Deployment / Model Handover record with the MLPod team.
7. Obtain Technical Sign-off and Business Sign-off from the confirmed owners.
8. Obtain Final Stage 1 Sign-off from the Stage Gate / Accountable Owner.

---

# Appendix A — Evidence Register

| DSLC Requirement | Evidence Source | What the Evidence Demonstrates |
|---|---|---|
| Use Case Definition | Use Case Shaping document (attached PDF), readme (2).md | Business problem, decision context, stakeholders, scope, owner placeholders, epic reference (assumed placeholder) and success measures. Owners are marked as assumed placeholders and require confirmation. |
| Solution Design | readme (2).md, call_model_training_v3 (1).ipynb | Problem type, analytical approach, data sources, target variable, output format, limitations, production approach and scoring schedule. |
| Delivery Epic / Milestone | No evidence found | No delivery epic or milestone reference located in any available source. |
| Business Review | Use Case Shaping document (attached PDF) | Business context has been captured in a Use Case Shaping template. This does not constitute a formal Business Review: no reviewer name, explicit review outcome or approval decision is recorded. |
| Technical Review | No evidence found | No technical review record or reviewer located in any available source. |
| AI Inventory Registration | No evidence found | No AI Inventory registration reference or ID located in any available source. |
| Data Governance | readme (2).md (dataset list) | Datasets are documented. No formal governance approval or Data Steward confirmation located. |
| Data in Solution Design | readme (2).md, call_model_training_v3 (1).ipynb | Data sources, features, target variable and data quality steps documented in README and training notebook. |
| Deployment Data Handover | call_model_training_v3 (1).ipynb, call_model_scoring_with_validation_2026_02_04 (1).ipynb, readme (2).md | Scoring notebook, pickle files and SQL scripts exist. No formal handover record or named deployment team located. |
| EDA Report | call_model_training_v3 (1).ipynb | EDA performed within training notebook: class balance, missing values, cross-correlation analysis. No standalone EDA artefact found. |
| Stakeholder Presentation | No evidence found | No standalone stakeholder presentation located in available evidence. |
| Feature Engineering Report | call_model_training_v3 (1).ipynb | Full preprocessing pipeline documented and implemented: imputation, OHE, scaling, cross-correlation feature selection. All components serialised. |
| Feature Engineering Quality Check | call_model_training_v3 (1).ipynb | Reproducible pipeline, serialised components, correlation-based feature selection. Formal target leakage audit not evidenced. |
| Modelling Report | call_model_training_v3 (1).ipynb, readme (2).md | LightGBM hyperparameters, train/test split, class imbalance handling, evaluation metrics, SHAP analysis, model version history documented. |
| Model Card | readme (2).md, call_model_training_v3 (1).ipynb | Model name, purpose, approach, training data summary, limitations and production context documented. Formal standalone Model Card artefact not confirmed. |
| Modelling Quality Check | call_model_training_v3 (1).ipynb | Train/test evaluation, confusion matrices, ROC curves, gain/lift charts, SHAP analysis. Formal peer or technical review not evidenced. |
| Model Handover | call_model_training_v3 (1).ipynb, call_model_scoring_with_validation_2026_02_04 (1).ipynb, readme (2).md | Model artefacts (pickle files in scoring_pkl_files_3), scoring notebook and SQL scripts documented. Formal handover record and named receiving team not confirmed. |
| Validation Evidence | call_model_scoring_with_validation_2026_02_04 (1).ipynb | Out-of-sample validation: scoring pipeline applied to production dataset, output merged with ground-truth call labels. Accuracy, precision, recall, F1, confusion matrix and ROC AUC calculated. Five weeks of OOT validation referenced in README. |
| Technical Sign-off | No evidence found | No technical sign-off record located in any available source. |
| Business Sign-off | No evidence found | No business sign-off record located in any available source. |
| Final Stage 1 Sign-off | No evidence found | Cannot be confirmed. All prerequisite governance items are PENDING. |

---

# Appendix B — Data Sources

| Data Source / Dataset | Purpose |
|---|---|
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_call_model_complete_ip_v15` | Primary training dataset. Contains IHH/BBH RAG/MOT status features, customer attributes and call flag for Hub4 customers with Scaled Data availability. Used in v3 training. |
| `skydata-dsamldtmgmtuk-prod.uk_pub_service_checker_is.scaled_data_call_model_complete_ip_scoring_test` | Production scoring base table. Used by the scoring notebook to produce weekly propensity scores in MLPod. |
| `skydata-dsamldtmgmtuk-prod.uk_pub_service_checker_is.scaled_data_call_model_complete_ip_scoring_with_validation_02_04` | Validation dataset containing actual call labels for out-of-sample validation (04 February 2026). |
| `skyuk-uk-pa-pres-prod.uk_pub_data_foundation_base_ic.hub_telemetry_base` | Hub telemetry data providing reboot counts and device-level identifiers. Also provides the scoring customer base. |
| `skyuk-uk-data-foundation-prod.reporting.sc_reactive_journeys` | Historical contact / reactive journey data providing the call target variable. |
| `skyuk-uk-decis-models-01-prod.forecasting.Cust_Weekly_Base` | Customer weekly base providing subscription and demographic attributes. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_ihh_ihh_rag_aggregated` | IHH RAG status aggregations for Hub4 customers. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_ihh_mot_wifi_status_aggregated` | IHH MOT Wi-Fi status check aggregations. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_ihh_mot_slow_wifi_aggregated` | IHH MOT slow Wi-Fi check aggregations. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_ihh_mot_unreliable_wifi_aggregated` | IHH MOT unreliable Wi-Fi check aggregations. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_ihh_mot_poor_coverage_aggregated` | IHH MOT poor coverage check aggregations. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_bbh_bbh_rag_aggregated` | BBH RAG status aggregations for Hub4 customers. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_bbh_mot_hub_retrains_aggregated` | BBH MOT hub retrain check aggregations. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_bbh_mot_hub_downstream_errors_aggregated` | BBH MOT hub downstream error check aggregations. |
| `sky-uk-ids-analytics-prod.service_checker.scaled_data_hub4_bbh_mot_speed_aggregated` | BBH MOT speed check aggregations. |
| `skyuk-uk-decis-models-01-prod.uk_pub_polygon_hist_ic.allbase_whix_historic_results` | WHIX (Wi-Fi Health Index) historical performance data providing the avg_whix_score feature. |
| `skyuk-uk-decis-etl-01-prod.uk_pub_prism_is.prism_customer_base_live_weekly` | PRISM customer base providing demographic and household-level features including age band and household affluence. |

---

# Appendix C — Model Technical Detail

## Final Model Hyperparameters (v3)

```
LGBMClassifier(
    n_estimators      = 500,
    learning_rate     = 0.05,
    max_depth         = 7,
    num_leaves        = 24,
    min_child_samples = 30,
    subsample         = 0.8,
    colsample_bytree  = 0.8,
    reg_alpha         = 1.5,
    reg_lambda        = 1.5,
    is_unbalance      = True,
    random_state      = 42
)
```

## Preprocessing Components

All components are fitted on training data only and applied consistently to test and production scoring data. Components are serialised as pickle files in `scoring_pkl_files_3/`.

| Component | Implementation | Pickle File |
|---|---|---|
| Numerical imputer | SimpleImputer(strategy='median') | numerical_imputer.pkl |
| Categorical imputer | SimpleImputer(strategy='most_frequent') | categorical_imputer.pkl |
| One Hot Encoder | OneHotEncoder(sparse_output=False, handle_unknown='ignore') | ohe.pkl |
| Scaler | RobustScaler() | scaler.pkl |
| Model | LGBMClassifier (see hyperparameters above) | model.pkl |

## Numerical Features — Pre-processing (33 features)

talk_active_flag, ihh_rag_duration_green_time_of_call, bbh_rag_duration_green_prev_1wk, mot_unreliable_wifi_any_green_time_of_call, multiscreen_flag, non_maintenance_reboots_in_last_1wk, any_calls_in_last_90d, days_since_last_payment, user_and_system_reboots_in_last_24h, mot_speed_count_red_prev_24hr, mot_slow_wifi_duration_green_prev_1wk, bb_tenure_months, mot_unreliable_wifi_duration_green_prev_48hr, tv_active_flag, curr_offer_amount_bb, sports_flag, mot_unreliable_wifi_count_red_time_of_call, mot_slow_wifi_any_green_time_of_call, mot_poor_coverage_any_red_time_of_call, ultra_hd_flag, mot_unreliable_wifi_count_green_prev_6hr, avg_whix_score_in_last_1wk, mot_poor_coverage_count_green_time_of_call, mot_wifi_status_duration_green_prev_48hr, mobile_active_flag, disney_plus_active, mot_wifi_status_any_green_prev_48hr, bb_booster_flag, mot_hub_downstream_errors_duration_grey_time_of_call, avg_temperature_in_last_1wk, sky_live_flag, cinema_flag, bbh_rag_count_grey_prev_6hr

## Categorical Features (8 features)

age_range, bb_type, bb_offer_depth, bb_contract_status, bb_tenure_bands, bb_speed_band, bb_status_code, h_affluence

## Top 10 Feature Importances (from scoring notebook)

1. mot_unreliable_wifi_duration_green_prev_48hr
2. user_and_system_reboots_in_last_24h
3. age_range_F._66+
4. avg_whix_score_in_last_1wk
5. bbh_rag_duration_green_prev_1wk
6. any_calls_in_last_90d
7. tv_active_flag
8. bb_booster_flag
9. bb_contract_status_G._In_Contract
10. mot_speed_count_red_prev_24hr

## Model Artefact Locations

| Artefact | Location |
|---|---|
| Production pickle files | scoring_pkl_files_3/ |
| Training notebook (v3) | call_model_training_v3.ipynb |
| Scoring notebook | call_model_scoring_with_validation_2026_02_04.ipynb |
| SQL — production scoring base | sql_scripts/scoring.sql |
| SQL — training base (requires repointing) | sql_scripts/training_base_table.sql |
| SQL — validation base | sql_scripts/validation.sql |
| Out-of-time validation notebooks | validation_notebooks/ (v1, v2, v3 — 5 weeks OOT) |
