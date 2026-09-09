---
description: papers 폴더의 특허/논문을 분석해 Word 보고서로 만들고 GitHub에 푸시
---

다음 대상을 분석하세요: $ARGUMENTS

1. `papers/` 폴더에서 위 대상과 일치하는 PDF를 찾으세요. 없으면 어떤 파일들이
   있는지 목록을 보여주고 사용자에게 물어보세요.
2. CLAUDE.md에 정의된 워크플로우와 출력 형식을 그대로 따라 분석하고
   `analysis/` 폴더에 .docx로 저장하세요.
3. 저장 후 이번에 새로 만들거나 수정한 파일만 경로를 지정해 `git add`하세요
   (`git add .` 등 전체 추가는 절대 쓰지 마세요 — 회사 보안 프로그램(Fasoo DRM)이
   기존 파일들을 암호화해 내용을 바꿔놓을 수 있습니다). `git status`로 변경사항을
   보여주고, 커밋 메시지를 제안하세요.
4. 사용자가 승인하면 commit + push까지 진행하세요. 승인 전에는 push하지 마세요.
   push가 끝나면, 방금 add한 파일 경로마다
   `git update-index --assume-unchanged <경로>`를 실행해 해당 파일이 이후
   자동으로 add 대상이 되지 않도록 "추적하되 변경 무시" 상태로 표시해두세요.