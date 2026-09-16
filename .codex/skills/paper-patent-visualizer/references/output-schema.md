# Output schema

Follow an existing repository format when present. In the `study` repository, preserve the report structure defined by `CLAUDE.md` but save ChatGPT/Codex outputs under `analysis_GPT/` so they remain separate from `analysis/`. Otherwise create a primary Word report and companion visual assets.

## Word report

1. 문서 개요
2. 핵심 요약
3. 기술 내용
4. 실험 데이터 또는 근거
5. 기존 기술 대비 차별점
6. 활용 가능성 및 리스크
7. 추가 확인 사항
8. 도면 정리

Each material claim should include a human-readable source location such as `PDF p.14, Fig. 6` or `PDF p.16, claim 1`.

## Companion directory

Use a stable document identifier:

```text
analysis_GPT/<document-id>_visuals/
├── README.md
├── source-notes.json
├── visual-overview.svg
├── component-map.svg
└── operation-flow.svg
```

Create only the files supported by the document. `source-notes.json` records findings, locations, fact versus interpretation, and confidence. The README explains each visual and its limits.

If the primary report already exists, do not overwrite it. Create the companion directory and ask before inserting or replacing figures in the report.
