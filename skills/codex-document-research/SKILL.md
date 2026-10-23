---
name: document-research
description: Conduct doctoral-level academic research and produce an evidence-backed research report, literature review, thesis chapter, or research proposal. Use for deep scholarly investigation, critical synthesis, research-gap analysis, or a complete research-to-report workflow.
---

# Document Research

Aim for doctoral research standards: a defensible question, explicit methods, critical engagement with competing explanations, traceable evidence, and reproducible analysis. Depth is demonstrated through evidence and reasoning, not length or a promised credential. Distinguish original research, secondary synthesis, and a proposed study; never present a proposal as completed experiments.

Read [the local tool guide](references/tools.md) before choosing tools. Read the entry point of each downstream skill actually used. Use individual Researcher stages by default; the upstream research-pipeline skill imposes author checkpoints and is appropriate only when that checkpointed workflow is requested. Do not silently inherit it as the orchestrator for this skill.

## Establish the research contract

Extract the topic, research question, discipline, audience, academic level, report type, language, length, date range, source access, required sources, and target style from the request and supplied documents. Ask only for omissions that would materially change the investigation; otherwise state reasonable assumptions and proceed. Preserve the user's language. For a broad topic, formulate a focused main question and supporting questions before retrieving literature.

Choose and record a suitable method: critical or scoping review, systematic review, theoretical argument, empirical analysis, or proposal. Do not label an ordinary literature search systematic. A systematic review needs an explicit protocol, eligibility criteria, recorded screening, and reproducible counts. Scope effort to the requested deliverable without silently downgrading the promised method.

Create a concise research plan and maintain working artifacts under the task's work directory. Keep final deliverables in the user-designated output location. Record the search date and actual coverage rather than promising exhaustive access to all literature.

## Retrieve and qualify evidence

Use literature-search and the Researcher evidence kernel for scholarly retrieval and metadata. Use Codex web search for current facts, source discovery, and publisher guidelines. Use Report Workflow's Tavily/Serper/SerpAPI backend only when its credentials are actually configured. A missing optional API key does not block research through available search tools.

Search synonyms, alternative terminology, foundational studies, recent work, replication or negative results, and competing schools of thought. Select databases and search depth for the discipline. Maintain search strings, dates, databases, filters, retrieved counts, and exclusions. Deduplicate by DOI and normalized metadata. Follow references and forward citations when they can resolve important gaps.

Prefer original papers, scholarly books, official datasets, standards, and authoritative institutional sources. Separate preprints from peer-reviewed publications. Capture DOI or stable URL, bibliographic metadata, access date, and abstract/full-text access status. Read the actual evidence supporting substantive claims; search snippets and generated summaries are discovery aids. If access is limited, mark the limitation and narrow the claim.

Use a supplied NotebookLM notebook for source-grounded questions and cross-document synthesis when useful. Verify its responses and citation locators against the underlying documents. It supplements retrieval and interpretation; it is not an independent scholarly source. Use only the selected notebook and authorized materials; do not upload files or create external artifacts just because the integration exists.

## Build a critical synthesis

Maintain an evidence matrix containing source ID, question addressed, methods, population/context, findings, effect estimates or uncertainty when relevant, limitations, and supporting page/section/passage locators. Maintain a claim ledger linking each central factual claim to evidence and classifying it as supported, qualified, disputed, speculative, or unresolved.

Compare studies by design quality, measurement validity, bias, assumptions, reproducibility, and applicability. Explain disagreement rather than counting votes. Separate association from causation and statistical significance from practical importance. Identify what is established, what is contested, and what remains unknown.

Use research-gaps, contradiction-detection, extraction-tables, and experiment-design when relevant. Frame a research gap as an evidenced limitation of existing work; do not claim novelty solely because a search found nothing. Present proposed contributions with the evidence needed to establish them.

For empirical or quantitative work, read the applicable analysis skill, including ml-best-practices when required. Use supplied or legitimately retrieved data; preserve raw inputs, document cleaning and exclusions, justify models, test relevant assumptions, and report uncertainty, sensitivity, and limitations. Generate results from scripts. Do not manufacture data, significance, experiments, source access, or analyses. For a physics/engineering lab report, use lab-report-craft and follow its numerical and final-delivery checks.

## Draft, verify, and deliver

Organize for the actual document type. A substantial research report usually needs a clear question, background, explicit methods, thematic synthesis or results, discussion, limitations, conclusion, and references. A proposal instead needs research aims, planned methods, feasibility, and expected contributions labeled as expectations. Explain the chain from evidence to conclusions and address the strongest counterarguments.

Use paper-drafting for prose and citation-management for the bibliography. Every reference must be retrieved or verified; every borrowed claim must cite the supporting source. Audit reference identity and claim faithfulness with citation-audit and human-level passage review. Automated lexical matches do not establish semantic support. Distinguish verified, mismatched, unresolvable, and inconclusive outcomes; a timeout or inaccessible source is not evidence of fabrication.

Perform an adversarial review of the strongest claims, missing literature, methods, internal consistency, and alternative explanations. Revise substantiated issues and record unresolved ones. Never claim independent review unless a separate reviewer actually performed it. If the Researcher lineage model is used, follow its documented schemas and run its compile gate; report the real result. Do not invent gate records or equate LaTeX compilation with evidence validation.

For a polished deliverable, invoke document-formatting with the draft, bibliography, evidence matrix, figures, target format, and unresolved issues. Presentation-only work must not conceal evidence limitations.

Deliver the requested report and editable source, bibliography, a concise methods/search record, and material limitations. Include reproducibility files when analysis was performed, and evidence-matrix/claim-ledger files for a substantial review. State which verification and render checks actually passed. If a required gate fails, preserve the useful work and label the document as a draft instead of claiming submission readiness.
