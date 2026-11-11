# 저온 Treatment 장비 개발

저온(Low thermal budget) 산화/질화/열처리 Treatment 장비 개발 프로젝트 폴더.

## 폴더 구조

| 폴더 | 용도 |
|---|---|
| `01_요구사양/` | 목표 스펙 (온도 상한, 막 두께·균일도, Throughput, Wafer 크기 등) |
| `02_선행기술조사/` | 관련 특허·논문 정리. 원본 PDF는 `../papers/`, 개별 분석 보고서는 `../analysis/` 참고 |
| `03_공정조건_Window/` | 온도·압력·가스·Power·시간 등 공정 Window 정리 |
| `04_장비구성_설계/` | 플라즈마 소스(Remote/ICP/Microwave), Grid, Chamber, Heater, 가스계 구성안 |
| `05_실험계획_결과/` | DOE 계획 및 평가 결과 (XPS, CET, Leakage 등) |
| `06_회의록/` | 회의록·의사결정 기록 |
| `07_참고자료/` | 기타 자료 |

## 관련 기존 분석 (../analysis/)

- Remote plasma / Grid: US5844195, US9245761, US12580157B2, US20140273309A1, US202600074150A1
- Microwave plasma: US11942308B2
- 저온 산화: KR20240121901A, Photooxidation ultrathin SiO2, Low-thermal-budget high-k (CET 0.9 nm)
- 질화: N2/NH3 remote plasma nitridation, HfSiO N incorporation

## Git 주의사항

- `git add .` 금지 (Fasoo DRM). 새로 만든/수정한 파일만 경로 지정해서 add.
