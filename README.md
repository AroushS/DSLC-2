# DSLC Stage 1 Documentation Agent

## Purpose

Generates **DSLC Stage 1 documentation** from existing project evidence.

## What You Need

Before running the agent, add the following project files to the workspace:

* **Project Notebook**
* **EDA**
* **Project README**
* **Use Case Shaping Template**

The agent uses these files as its project evidence. **Missing information will be flagged rather than assumed or invented.**

## Requirements

* VS Code
* GitHub Copilot
* Python 3.x

## How to Use

1. Open the repository in **VS Code**.

2. Add the four project files listed above to the workspace.

3. Open **GitHub Copilot Chat**.

4. Ask:

   **`Generate the Stage 1 DSLC documentation.`**

5. Review the generated document and any evidence gaps identified by the agent.

## Output

Generated files are saved in the `output/` folder:

* **Editable DOCX**
* **PDF**, where available
