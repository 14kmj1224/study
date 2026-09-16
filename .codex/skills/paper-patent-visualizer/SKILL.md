---
name: paper-patent-visualizer
description: Analyze technical paper or patent PDFs, especially semiconductor process and equipment documents, and produce a Korean Word report plus source-grounded diagrams. Use when a user asks to analyze, compare, explain, or visualize PDFs in papers/ or another supplied location. Do not use for legal infringement or validity opinions.
---

# Paper Patent Visualizer

Turn a technical PDF into an evidence-traceable Korean explanation and a small set of diagrams that help a non-specialist understand the mechanism.

## Preflight

1. Read repository instructions such as `AGENTS.md` and `CLAUDE.md` before writing.
2. Resolve the requested PDF exactly. If ambiguous, show the matching filenames and ask the user to choose.
3. Check for an existing report or visual directory. Do not replace an existing analysis without explicit approval.
4. Preserve the source PDF. Use a temporary directory for page renders, OCR, and extraction intermediates.
5. In the `study` repository, write ChatGPT/Codex results under `analysis_GPT/`. Treat `analysis/` as another agent's output and do not modify it unless the user explicitly asks.

## Source extraction

- Prefer embedded text extraction, but render every relevant page for visual inspection.
- If the PDF is scanned, OCR it and label uncertain readings. Verify names, identifiers, claims, values, units, and figure references against rendered pages.
- Extract or render figures needed to interpret the apparatus, process, or results. Do not infer a missing connection merely because OCR suggests it.
- Record each material conclusion with its PDF page and, when available, figure, claim, table, or column reference.

## Route by document type

- For patents, read [references/patent-analysis.md](references/patent-analysis.md).
- For academic papers, read [references/paper-analysis.md](references/paper-analysis.md).
- Before designing diagrams, read [references/visual-guidelines.md](references/visual-guidelines.md).
- Before saving deliverables, read [references/output-schema.md](references/output-schema.md).

## Analysis workflow

1. Build an evidence table before drafting prose: `finding`, `source location`, `fact or interpretation`, and `confidence`.
2. Identify the problem, proposed mechanism, essential components or variables, operating sequence, evidence, limitations, and practical implications.
3. Separate document facts, author or inventor assertions, and analyst interpretation.
4. Explain specialist terms in Korean with the English term on first use.
5. Draft the primary Word report in the repository's required section order. If no repository format exists, use the format in `output-schema.md`.
6. Create only visuals that materially improve understanding. Prefer three complementary views: system structure, operating or decision flow, and quantitative evidence.
7. Cross-check every label, arrow, number, unit, and threshold in each visual against the evidence table.
8. Render the Word report to PNG and inspect every page. Verify that diagrams are readable and captions remain with their figures.

## Visual production

- Use SVG or another deterministic diagram format for technical structures, flows, and text-heavy infographics.
- Use generated raster illustrations only for clearly labeled conceptual views where exact geometry and wording are not factual evidence.
- A reconstructed diagram must say `원문 기반 재구성` and cite its source pages.
- Do not present embodiment details as claim requirements. Do not present a schematic as being to scale.
- Keep one visual focused on one question. Split crowded diagrams instead of shrinking labels.

## Safety and publication

- Patent analysis is technical, not a legal opinion. Do not conclude infringement, freedom to operate, validity, or current legal status from the supplied PDF alone.
- Do not silently browse for newer facts. If current legal status, family data, or later research is requested, verify it from authoritative current sources and distinguish it from the supplied document.
- Follow repository-specific staging and push rules. In this repository, stage only named paths, never `git add .`, show status and the diff summary, and obtain explicit approval before push.
