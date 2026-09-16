---
name: paper-patent-visualizer
description: Sync a requested local paper or patent PDF into Git when needed, analyze semiconductor process and equipment documents, and produce a Korean Word report plus source-grounded diagrams. Use when a user asks to find, analyze, compare, explain, or visualize a PDF in papers/ or another supplied location. Do not use for legal infringement or validity opinions.
---

# Paper Patent Visualizer

Turn a technical PDF into an evidence-traceable Korean explanation and a small set of diagrams that help a non-specialist understand the mechanism.

## Preflight

1. Read repository instructions such as `AGENTS.md` and `CLAUDE.md` before writing.
2. Resolve the requested PDF exactly. If ambiguous, show the matching filenames and ask the user to choose.
3. Check for an existing report or visual directory. Do not replace an existing analysis without explicit approval.
4. Preserve the source PDF. Use a temporary directory for page renders, OCR, and extraction intermediates.
5. In the `study` repository, write ChatGPT/Codex results under `analysis_GPT/`. Treat `analysis/` as another agent's output and do not modify it unless the user explicitly asks.

## Sync a local `papers/` PDF before analysis

When the user says that a PDF was placed in the PC's local `papers/` folder, perform this sequence before reading the paper:

1. Confirm that the active workspace is the user's local `study` Git checkout and that its `papers/` directory is readable. Do not claim access to a Windows path merely because the user named it; if the local checkout is not mounted or opened, ask the user to open it in Codex or upload/push the PDF.
2. Find the requested PDF by normalized title, filename fragment, DOI, patent number, or other identifier. Search only filenames first. If exactly one file matches, use it. If multiple files plausibly match, show their filenames and ask the user to choose.
3. Validate that the selected file is a readable PDF, then run `git status --short -- <exact-pdf-path>` to determine whether it is untracked or modified.
4. If the PDF is already committed and the working copy is unchanged, skip the source push and continue to analysis.
5. If the PDF is new or modified, stage only that exact PDF path. Never use `git add .`, `git add papers`, a wildcard, or any command that stages unrelated files. Show `git status` and a staged diff summary, commit it with `papers: <document title or filename> 추가`, and request explicit approval immediately before pushing, as required by the repository instructions.
6. Push the source-PDF commit before starting the analysis. If the push fails, preserve the commit, report the blocker, and do not pretend the remote repository contains the file.
7. After a successful source push, analyze the same local PDF and save all ChatGPT/Codex outputs under `analysis_GPT/`. Follow the repository's separate approval rule before pushing the finished analysis.

Do not upload every file in `papers/` merely because the user said “papers 폴더 푸시.” Interpret that phrase as synchronizing the requested analysis source while preserving unrelated local files.

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
