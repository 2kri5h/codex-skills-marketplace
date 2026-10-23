---
name: document-formatting
description: Professionally edit and format academic reports, theses, research manuscripts, and lab reports into polished Word, LaTeX, or PDF deliverables. Use for editorial refinement, publisher or school templates, typography, citations, equations, tables, figures, and final layout quality assurance.
---

# Document Formatting

Treat the report as a professional scholarly publication: clear editorial hierarchy, consistent notation, restrained typography, readable figures and tables, and a verified final render. Preserve the author's meaning, findings, uncertainty, citations, and data. Rephrase for clarity without strengthening conclusions or introducing research findings. Flag substantive ambiguity for the author; route additional investigation to document-research when authorized.

Read `~/.codex/skills/academic-report-runtime/SKILL.md` for the installed Python, Pandoc, Mermaid, and LaTeX paths. Read only the downstream skills needed for the chosen deliverable. This skill coordinates editing and production; it does not certify acceptance by a journal or university.

For a connected Google Doc or Drive template, use the available google-drive and google-docs skills and their connected tools. For a user-selected live Word session, discover the Document Control session and its supported operations before editing. Use the user's requested destination; do not assume local package installation creates a live connector.

## Determine the production specification

Inspect the actual source document and supplied examples or template. Identify the output format, editable-source requirement, language, audience, venue, required sections, citation style, paper size, margins, page limits, and school-specific elements. A supplied mandatory template takes priority over generic aesthetics. Verify current publisher requirements from official guidelines when a named venue is the target; do not substitute a generic IEEE/ACM/Nature profile for the specific venue.

When no template is supplied, use a restrained academic design with consistent body and heading styles, generous readable spacing, and a small typographic palette. Choose document-appropriate defaults and disclose meaningful assumptions. Do not add a title page, abstract, TOC, or decorative elements unless useful or required. Preserve existing source files; produce an edited copy and a brief record of material editorial changes.

## Edit the document

Review structure, argument flow, paragraph focus, terminology, tense, grammar, and redundancy. Define acronyms at first use and keep spelling conventions consistent. Preserve technical qualifiers and authorial intent. Reconcile heading hierarchy, captions, table/figure callouts, footnotes, and cross-references. Keep editorial queries separate from final prose.

Check notation, units, significant figures, and reported uncertainty for consistency. Verify apparent numerical errors against supplied calculations or source data before changing values. Do not silently recalculate results or replace ambiguous numbers. Ensure equations retain mathematical meaning and that every symbol needed by the reader is defined.

## Produce the target format

### Word

Read the available documents skill for DOCX editing and render verification. Use named Word styles for body, headings, captions, lists, and references instead of ad hoc spacing. Use real section/page breaks, consistent headers/footers, correct page numbering, accessible heading order, and maintainable captions/cross-references. A TOC must reflect the actual heading structure; field refresh may require Word and must be disclosed if not performed.

For evidence-backed generation, calculated tables, school template fitting, or OMML equations, read `~/.codex/skills/report-workflow/SKILL.md` and its upstream references. Use the installed CLI/Python wrapper with real preflight results. Map template styles and page geometry explicitly. Preserve native editable equations using OMML; do not replace them with screenshots. Inspect conversion fidelity, especially equation numbering, citations, tables, and page breaks. For simple existing-document edits, use the document tools directly when rebuilding through the full evidence pipeline would risk loss or unnecessary work.

### LaTeX and PDF

Read `~/.codex/skills/researcher-journal-formatting/SKILL.md` for a target venue, and the available latex-document-skill for document mechanics. Use the correct document class and bibliography configuration; avoid manual overrides that violate a publisher class. Read researcher-latex-tables for booktabs tables. Use semantic labels and cross-references, consistent equation notation, proper unit formatting, and maintainable source organization.

For standalone LaTeX documents in Codex, use the built-in editor/compiler when applicable under the environment's instructions; use installed MiKTeX for workflows requiring a multi-file project or the report skill's own build checks. Run the relevant bibliography and cross-reference passes. Fix compile errors, missing references, and meaningful overflow warnings. LaTeX build success validates typesetting, not the truth of the research.

### Figures, tables, and diagrams

Use matplotlib for numerical plots and the installed Mermaid wrapper for workflows, with TikZ when an editable technical diagram is preferable. Keep data encodings accurate and accessible; label axes and units, provide meaningful legends/captions, and ensure fonts remain readable at final size. Prefer vector assets when the output supports them. Avoid decorative charts and misleading scales.

Tables need clear headings, units, numeric alignment, consistent precision, and readable widths. Avoid shrinking a dense table until illegible; restructure, split, or use landscape when appropriate. Preserve formulas/calculated values and source attribution. Booktabs is a LaTeX table style, not a requirement to reproduce LaTeX markup inside Word.

## Verify the actual deliverable

Audit bibliography/citation pairing and numbering. Use citation-management for mechanical consistency and citation-audit for substantive source validation when requested or needed. Formatting must not imply that previously unverified references were verified. Preserve and disclose unresolved evidence issues from the research handoff.

Render the final Word/PDF output and visually inspect all pages for clipping, overflow, blank-page errors, broken equations, awkward headings, orphaned captions, figure readability, and table splits. Inspect high-risk figures and equations at readable size. Validate that edits did not drop paragraphs, tables, figures, equations, notes, or references. For long documents, automated page/content checks can supplement but not substitute for claimed visual inspection. Re-render changed pages after fixes.

Use the actual available Word, LibreOffice, document, or PDF rendering tools. If Word rendering is unavailable, perform structural DOCX checks and provide the editable document with an explicit render limitation; do not claim Word pagination was verified using an unrelated approximate PDF conversion. Do not install extra applications or connect accounts solely to hide a verification limitation.

For a lab-report-craft final submission, preserve its applicable numerical, workflow-evidence, independent-review, and compilation gates. For a Report Workflow output, run its applicable validation/render gates. Report real pass/fail results. Label a document with unresolved material issues as a draft.

Deliver the requested professional artifact, editable source when requested or needed for maintainability, and a concise editorial/QA note listing changes, actual checks, and remaining author queries. Include external assets and bibliography files required to rebuild a LaTeX project. Use clear filenames and link the final outputs.
