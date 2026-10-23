---
name: ph227-assignment
description: Guide and standard workflow for solving IIT Bombay PH227 (AI and Data Science) lab assignments and tutorial sheets. Use whenever working on PH227 tutorial sheets, lab assignments, or creating Jupyter notebooks for PH227 courses.
license: Apache-2.0
metadata:
  version: v1
---

# PH227: AI and Data Science — Lab Assignment & Tutorial Workflow

This skill encapsulates the exact patterns, student coding style, and deliverables required for IIT Bombay's PH227 (AI and Data Science) lab assignments and tutorial sheets.

---

## 1. Student Identity & Context
* **Course:** PH227: AI and Data Science (Semester 3, IIT Bombay)
* **Student Name:** Krish
* **Roll Number:** 25B3004
* **Target Directory:** `i:\My Drive\IITB\Acads\Sem-3\PH227\Lab Assignments\TUT-<N>`
* **Primary File Naming:** `25B3004_Tut<N>.ipynb` (and optionally `Tutorial_Sheet_<N>.ipynb` copy)

---

## 2. Coding Style & Formatting Rules
When writing solutions for PH227:
1. **Student-Level Simplicity:**
   - Write standard, normal undergraduate AI/ML student code.
   - Do NOT use complex classes, decorators, fancy helper abstractions, or overly advanced functions.
   - For algorithms (e.g. K-means), implement from clean first principles using standard loops and basic `numpy`.
2. **Minimal to No Comments:**
   - Avoid verbose comment blocks, decorative dividers, or step-by-step commentary.
   - Short labels like `# Part (a)` or `# Part (b)` are sufficient.
3. **Short Variable Names:**
   - Use concise, intuitive student variable names:
     - Data & Files: `df`, `fname`, `X`, `y`, `col`, `pts`
     - Statistics: `ct` (contingency table), `chi2`, `p`, `dof`, `crit`, `alpha`
     - Clustering: `K`, `idx`, `c` (centroids), `new_c`, `d` (distance)
4. **Plain Printing (Option A):**
   - **Never** use complex string formatting specifiers like `:.4f`, `:.4e`, or `%` formatting unless explicitly requested.
   - Use standard commas in plain `print()` statements:
     ```python
     print("Chi-Square Statistic:", chi2)
     print("Degrees of Freedom:", dof)
     print("p-value:", p)
     ```
   - **Never** print decorative separator lines like `print("=" * 65)`.
5. **Interactive & Non-Interactive Input Handling:**
   - When assignment asks for user choice using `input()`, handle headless/non-interactive execution gracefully:
     ```python
     try:
         choice = input("Enter choice ('a' for Gender, 'b' for Class, or Enter for both): ").strip().lower()
     except Exception:
         choice = 'both'

     if not choice:
         choice = 'both'
     ```

---

## 3. Deliverable Structure & Layout
* **Deliverable:** Exactly one `.ipynb` notebook per tutorial sheet.
* **Cell Structure:**
  - **Cell 1 (Markdown):**
    ```markdown
    # PH227: AI and Data Science
    ## Tutorial Sheet <N>: Python / Data Science Part
    **Name:** Krish  
    **Roll Number:** 25B3004  
    ```
  - **For Each Question:**
    - A Markdown cell containing the exact question description.
    - A single Code cell containing the complete solution for that question.
* **Pre-Rendered Outputs:**
  - Always pre-execute the notebook (e.g., using `NotebookClient`) so all stream text, tables, and matplotlib figures are fully saved and visible upon opening.
