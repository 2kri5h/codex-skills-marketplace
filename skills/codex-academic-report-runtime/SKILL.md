---
name: academic-report-runtime
description: Use the configured local Python and LaTeX runtimes when generating academic reports, physics lab reports, plots, numerical analysis, or DOCX exports with the installed report skills.
---

# Local academic report runtime

Run Python with `C:/Users/krish/.codex/report-env/Scripts/python.exe` (PowerShell: `& "C:/Users/krish/.codex/report-env/Scripts/python.exe" -X utf8 script.py`). Do not rely on the system Python for these dependencies.
This environment contains python-docx, matplotlib, scipy, numpy, PyMuPDF, pandas, and report-workflow with its render dependencies.
Researcher uses its own uv-managed environment: `uv run --project "C:/Users/krish/.codex/researcher/core" researcher-core --help`.
MiKTeX provides xelatex, pdflatex, latexmk, ctexart and booktabs. Use the language requested by the user; lab-report-craft defaults to Chinese and ctexart, so adapt the template for English reports when requested.
Read the relevant installed workflow before authoring. Never fabricate source data or citations.

Before running these tools in PowerShell, prepend the environment Scripts directory to PATH so Pandoc is discoverable:
```powershell
$env:PATH = "$env:USERPROFILE\.codex\report-env\Scripts;$env:PATH"
```
Activation of report-env also sets this PATH.

## Optional report integrations
NotebookLM CLI and browser support, tavily-python, and Mermaid CLI are installed. Activate report-env or prepend its Scripts directory to PATH. Its mmdc.cmd wrapper uses the installed Playwright Chromium. NotebookLM needs Google login via notebooklm login and a selected notebook ID before syncing. Web research needs TAVILY_API_KEY, SERPER_API_KEY or SERPAPI_API_KEY; load a user-level variable into the shell when the app predates its creation. Do not claim integrations are authenticated merely because dependencies are present.
