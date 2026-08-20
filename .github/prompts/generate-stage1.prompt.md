# Generate Stage 1 DSLC

Generate the complete Stage 1 Proof of Value DSLC package for the active project.

Follow the repository-wide DSLC instructions and all relevant knowledge rules.

## Workflow

1. Review all available project evidence.

2. Assess the project against every applicable Stage 1 requirement.

3. Identify missing or conflicting evidence.

4. Ask only targeted questions where genuinely necessary and where the answer cannot reasonably be verified from available evidence.

5. Build evidence traceability for the major Stage 1 requirements.

   For each local project evidence file used:

   - confirm the evidence file actually exists in the workspace;
   - run `tools/resolve_evidence_link.py` for that file;
   - use exactly the evidence location returned by the tool;
   - if the tool returns a verified GitHub URL, preserve it as a Markdown hyperlink;
   - if the tool returns only a relative workspace path, use that path as plain text;
   - if no evidence location can be verified, use `Location not available`.

   Never manually construct or guess:

   - a GitHub repository URL;
   - organisation name;
   - repository name;
   - branch name;
   - commit;
   - file path;
   - SharePoint URL;
   - Confluence URL;
   - Databricks URL;
   - any other evidence location.

   Where an explicit external evidence URL already exists in supplied project evidence, preserve that URL rather than replacing it.

6. Generate the Stage 1 content using the standard Stage 1 structure.

7. Populate Appendix A — Evidence Register with:

   - DSLC Requirement;
   - Evidence Source;
   - What the Evidence Demonstrates;
   - Evidence Location.

   Appendix A is the authoritative evidence-traceability location.

   Do not repeatedly reproduce evidence links throughout the main report.

8. Validate the content before final output.

9. Produce the standard Stage 1 deliverables:

   - editable DOCX;
   - PDF review copy.

## Output quality

The final document must:

- be concise and business-readable;
- prioritise Stage 1 readiness and outstanding actions;
- avoid unnecessary repetition;
- avoid exposing YAML or internal agent terminology;
- clearly distinguish technical readiness from governance readiness;
- clearly identify pending items;
- show important evidence without dumping raw notebook content;
- provide traceability to project evidence through the Evidence Register;
- include verified clickable evidence links where available;
- fall back safely to verified workspace paths where clickable links are unavailable;
- never contain guessed, fabricated or inferred evidence URLs;
- include technical detail only where useful to Stage 1 review;
- use the standard output structure and formatting rules.

Do not return only Markdown unless document generation is technically unavailable.