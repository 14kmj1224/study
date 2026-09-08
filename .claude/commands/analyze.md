---
description: papers 폴더의 특허/논문을 분석해 Word 보고서로 만들고 GitHub에 푸시
---

다음 대상을 분석하세요: $ARGUMENTS

1. `papers/` 폴더에서 위 대상과 일치하는 PDF를 찾으세요. 없으면 어떤 파일들이
   있는지 목록을 보여주고 사용자에게 물어보세요.
2. CLAUDE.md에 정의된 워크플로우와 출력 형식을 그대로 따라 분석하고
   `analysis/` 폴더에 .docx로 저장하세요.
3. 저장 후 `git status`로 변경사항을 보여주고, 커밋 메시지를 제안하세요.
4. 사용자가 승인하면 commit + push까지 진행하세요. 승인 전에는 push하지 마세요.