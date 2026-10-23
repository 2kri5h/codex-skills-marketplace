# Installed research and report tools

Resolve these paths from the current user's home directory. Read skill files before using their procedures. Use actual frontmatter names or file paths, since the installed Researcher directories have prefixes that differ from their skill names.

## Runtime

Read `~/.codex/skills/academic-report-runtime/SKILL.md` for the maintained local configuration. On this Windows environment:

```powershell
$reportScripts = Join-Path $env:USERPROFILE '.codex\report-env\Scripts'
$env:PATH = "$reportScripts;$env:PATH"
& "$reportScripts\python.exe" -X utf8 your_script.py
uv run --project "$env:USERPROFILE\.codex\researcher\core" researcher-core --help
```

The report environment has NumPy, SciPy, pandas, matplotlib, PyMuPDF, python-docx, Report Workflow, Pandoc, NotebookLM with Playwright, and tavily-python. Its `mmdc.cmd` wrapper uses installed Chromium. MiKTeX supplies LaTeX engines. Probe availability instead of assuming a prior installation still works. Keep secrets and authentication files out of reports, logs, and shared outputs.

## Route to the smallest relevant skill

Researcher skills are `~/.codex/skills/researcher-<suffix>/SKILL.md`:

| Work | Suffix |
| --- | --- |
| Literature retrieval and bibliography | literature-search, citation-management |
| Critical synthesis and gap analysis | research-convergence, research-gaps, contradiction-detection, extraction-tables |
| Review protocols and screening | systematic-review |
| Design and analysis | experiment-design, statistical-analysis |
| Writing and scholarly review | paper-drafting, peer-review, citation-audit |
| Publisher formatting and figures | journal-formatting, latex-tables, visualization, tikz-diagrams |

The kernel's command documentation is `~/.codex/researcher/references/core-cli.md`. Read it and relevant `--help` output before constructing search, citation, passage, or lineage commands. Use real CLI results rather than reproducing examples as alleged outputs.

For DOCX pipelines, read `~/.codex/skills/report-workflow/SKILL.md` and its linked upstream skill. The functions named in upstream skill.yaml are not automatically registered MCP tools; call the installed CLI or Python wrappers. Use the upstream preflight and record the user's actual feature decisions. Authorization to research does not supply an API key or notebook ID.

For experimental physics/engineering reports, read `~/.codex/skills/lab-report-craft/SKILL.md`. Its Chinese template is a default, not a reason to change the user's requested language.

## NotebookLM and web-search readiness

NotebookLM's Python client is a third-party integration. Check current authentication using documented CLI commands. Google sign-in was completed during setup, but sessions may expire. Ask the user to select the relevant notebook when it is ambiguous. Use `notebooklm --help` and command-specific help; do not guess SDK signatures. Prefer read-only questions and source retrieval. Creating, uploading, or sharing material requires task-specific authorization.

Report Workflow web research supports `TAVILY_API_KEY`, `SERPER_API_KEY`, or `SERPAPI_API_KEY`. Check whether configured without displaying their values. Windows processes started before a user environment-variable change may need a restart or an explicit load. The SDK installation alone is not proof of authenticated search. Codex's existing web search and the kernel's available scholarly indexes can be used without configuring these optional backends.

Mermaid makes process diagrams; matplotlib makes quantitative plots; TikZ makes editable technical schematics. Use each where it conveys real information. A diagram or plot must distinguish observations from proposals and cite external information when needed.

## Connected sources

When the user supplies connected Google Drive/Docs/Sheets materials, read the available google-drive entrypoint and the relevant file-type skill, then retrieve the source through the connected tools. Use other installed source connectors only when they fit the actual research question. Preserve source IDs and useful locators. Inspect available tool metadata rather than assuming the local Python packages registered connectors or MCP servers. Keep local deliverables local unless the user requests a connected document or publication.
