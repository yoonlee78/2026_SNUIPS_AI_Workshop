# AI Workshop Session 2: SAPA 데이터 분석 파이프라인

AI Agent를 활용한 성격 데이터 분석 및 학술 논문 초안 작성 워크샵입니다.

---

## 워크샵 개요

이 워크샵에서는 AI Agent와 협업하여 다음을 수행합니다:
- 대규모 성격 데이터 탐색 및 전처리
- 시각화 및 통계 분석
- 학술 논문 초안 작성
- AI 기반 프루프리딩 및 수정

---

## 프로젝트 구조

```
AIWorkshop_Session2/
├── INSTRUCTIONS.md              ← AI Agent 지침
├── README.md                    ← 이 파일
├── data/
│   └── raw/                     ← 원본 데이터
│       ├── sapa_data.csv
│       ├── item_info.csv
│       └── superKey696.csv
├── notebooks/
│   └── 01_data_scan.ipynb       ← 시작 노트북
├── guides/                      ← 참조 가이드
│   ├── preprocessing_guide.md
│   ├── stats.md
│   ├── writing.md
│   ├── proofreading_guide.md
│   ├── revision.md
│   └── *.pdf                    ← 스타일 가이드
└── .cursor/skills/              ← AI 스킬
    ├── capture-results/
    ├── generate-next-step/
    ├── github-update/
    └── proofread/
```

---

## 파이프라인 (7 Steps)

| 단계 | 이름 | 생성할 파일 | 트리거 |
|------|------|-------------|--------|
| 1 | **Scan** | `01_data_scan.ipynb` → `step1_scan.json` | ✅ 제공됨 |
| 2 | **Preprocess** | `02_preprocessing.ipynb` → `step2_preprocess.json` | "다음 단계 만들어줘" |
| 3 | **Visualization** | `03_visualization.ipynb` → `step3_viz.json` | "다음 단계 만들어줘" |
| 4 | **State Analysis** | `04_state_analysis.ipynb` → `step4_state.json` | "다음 단계 만들어줘" |
| 5 | **Writing** | `step5_draft_method.md`, `step5_draft_results.md` | "다음 단계 만들어줘" |
| 6 | **Proofreading** | `step6_proofreading_report.md` | "다음 단계 만들어줘" |
| 7 | **Revision** | `step7_revised_method.md`, `step7_revised_results.md` | "다음 단계 만들어줘" |

---

## 시작하기

### 1. 환경 준비

```bash
pip install pandas numpy matplotlib seaborn scipy
```

### 2. 첫 번째 노트북 실행

1. `notebooks/01_data_scan.ipynb` 열기
2. 모든 셀 실행하여 데이터 구조 파악

### 3. 결과 저장

```
"결과 저장해줘"
```
→ `reports/step1_scan.json` 생성

### 4. 다음 단계 진행

```
"다음 단계 만들어줘"
```
→ `02_preprocessing.ipynb` 생성

### 5. 반복

노트북 실행 → 결과 저장 → 다음 단계 생성을 Step 7까지 반복

---

## AI 스킬

| 스킬 | 트리거 키워드 | 설명 |
|------|--------------|------|
| **capture-results** | "결과 저장", "저장해줘" | 노트북 결과를 JSON으로 저장 |
| **generate-next-step** | "다음 단계 만들어줘" | 파이프라인 다음 단계 생성 |
| **github-update** | "GitHub 업데이트", "커밋" | 변경사항을 GitHub에 업로드 |
| **proofread** | "프루프리딩", "논문 검토" | 학술 문서 검토 |

---

## 참조 가이드

| 파일 | 단계 | 용도 |
|------|------|------|
| `guides/preprocessing_guide.md` | Step 2 | 전처리 및 척도 계산 방법 |
| `guides/stats.md` | Step 4 | Critical Ratios 통계 방법론 |
| `guides/writing.md` | Step 5 | Method/Results 작성 가이드 |
| `guides/proofreading_guide.md` | Step 6 | 프루프리딩 평가 기준 |
| `guides/revision.md` | Step 7 | 수정 전략 가이드 |

---

## 데이터 설명

- **SAPA**: Synthetic Aperture Personality Assessment
- **출처**: [Harvard Dataverse](https://dataverse.harvard.edu/)
- **특징**: 
  - 696개 성격 문항
  - Planned missingness (설계된 결측) 구조
  - Big Five, Ideology, Honesty-Humility 척도

---

## 학습 목표

1. AI Agent에게 **자연어로 작업 지시**하는 방법
2. **재현 가능한 분석 파이프라인** 구축
3. **학술 논문 초안** 자동 생성 및 검토
4. **Overclaiming 방지** 및 보수적 글쓰기 원칙
