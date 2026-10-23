---
name: report-workflow
description: Generate, revise, validate, and export academic or educational DOCX reports with evidence, OMML equations, calculated tables, and school templates.
---

# Report Workflow for Codex

Read [the upstream skill](skills/report-workflow/SKILL.md) and follow its workflow. Resolve its relative reference links from skills/report-workflow/.

Use this installed Python interpreter for all package and wrapper calls:
`C:/Users/krish/.codex/report-env/Scripts/python.exe`

The CLI is `C:/Users/krish/.codex/report-env/Scripts/report-workflow.exe`.
Tools named in upstream skill.yaml are not automatically registered as Codex MCP tools. Use the CLI or import report_workflow.agent_wrapper using the interpreter above.
Pandoc is bundled through pypandoc-binary. For Windows console output, use Python -X utf8.

Before running these tools in PowerShell, prepend the environment Scripts directory to PATH so Pandoc is discoverable:
```powershell
$env:PATH = "$env:USERPROFILE\.codex\report-env\Scripts;$env:PATH"
```
Activation of report-env also sets this PATH.
