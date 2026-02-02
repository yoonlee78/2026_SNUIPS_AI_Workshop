# SAPA 데이터 분석 파이프라인

## 개요

- **데이터**: SAPA (Synthetic Aperture Personality Assessment) 성격 검사
- **특징**: 696개 문항, planned missingness (설계된 결측)
- **목표**: 데이터 탐색 → 전처리 → 시각화 → 주별 분석 → 논문 초안 → 프루프리딩 → 수정

---

## 파이프라인 구조 (7 Steps)

```
┌─────────────────────────────────────────────────────────────┐
│  Step 1: Data Scan                                          │
│  → 01_data_scan.ipynb → step1_scan.json                     │
│  → 데이터 구조 파악, 결측 패턴 확인                          │
│                    ↓                                        │
│  Step 2: Preprocessing                                      │
│  → 02_preprocessing.ipynb → step2_preprocess.json           │
│  → QC + 역채점 + Big Five/Ideology/H-H 점수 계산            │
│  → guides/preprocessing_guide.md 참조                       │
│                    ↓                                        │
│  Step 3: Visualization                                      │
│  → 03_visualization.ipynb → step3_viz.json                  │
│  → 상관행렬, 분포 히스토그램                                 │
│                    ↓                                        │
│  Step 4: State Analysis                                     │
│  → 04_state_analysis.ipynb → step4_state.json               │
│  → Critical Ratios로 주별 특징 분석                         │
│  → guides/stats.md 참조                                     │
│                    ↓                                        │
│  Step 5: Writing                                            │
│  → step5_draft_method.md, step5_draft_results.md            │
│  → Method/Results 초안 작성                                 │
│  → guides/writing.md 참조                                   │
│                    ↓                                        │
│  Step 6: Proofreading                                       │
│  → step6_proofreading_report.md                             │
│  → Nature 리뷰어 관점 평가, overclaim 분석                  │
│  → guides/proofreading_guide.md 참조                        │
│                    ↓                                        │
│  Step 7: Revision                                           │
│  → step7_revised_method.md, step7_revised_results.md        │
│  → 프루프리딩 피드백 반영 수정                              │
│  → guides/revision.md 참조                                  │
└─────────────────────────────────────────────────────────────┘
```

---

## Skills (4개)

| Skill | 역할 | 요청 예시 |
|-------|------|----------|
| `capture-results` | 노트북 결과 → JSON 저장 | "결과 저장해줘" |
| `generate-next-step` | Context 기반 → 다음 단계 생성 | "다음 단계 만들어줘" |
| `github-update` | 변경사항 → GitHub push | "GitHub 업데이트해줘" |
| `proofread` | 학술 문서 검토 및 평가 | "프루프리딩해줘" |

---

## 핵심 파일

### 파이프라인 상태
| 파일 | 용도 |
|------|------|
| `reports/pipeline_context.json` | 현재 단계 및 완료 단계 추적 |

### 가이드 문서 (guides/)
| 파일 | 용도 |
|------|------|
| `guides/preprocessing_guide.md` | 전처리 로직, 점수 계산식 |
| `guides/stats.md` | Critical Ratios 통계 방법론 |
| `guides/writing.md` | Method/Results 작성 가이드 (Few-shot 예시) |
| `guides/proofreading_guide.md` | 프루프리딩 평가 기준 (Few-shot 예시) |
| `guides/revision.md` | 수정 전략 가이드 (Few-shot 예시) |

### 스타일 가이드 (guides/)
| 파일 | 용도 |
|------|------|
| `guides/APA7-Style.pdf` | APA 7판 인용/형식 가이드 |
| `guides/The Elements of Style.pdf` | 간결한 영문 작성 원칙 |
| `guides/Writing Science.pdf` | 과학 글쓰기 원칙 |

### 데이터
| 파일 | 용도 |
|------|------|
| `data/raw/superKey696.csv` | 채점 키 (역채점 정보 포함) |
| `data/processed/sapa_scores.csv` | 계산된 척도 점수 |

---

## 사용 흐름

```
[Step 1: Scan]
사용자: (01_data_scan.ipynb 실행)
사용자: "결과 저장해줘"
AI: → step1_scan.json 저장, current_step: "preprocess"

[Step 2: Preprocess]
사용자: "다음 단계 만들어줘"
AI: → guides/preprocessing_guide.md 참조 → 02_preprocessing.ipynb 생성
사용자: (실행 후) "결과 저장해줘"
AI: → step2_preprocess.json 저장, current_step: "viz"

[Step 3: Visualization]
사용자: "다음 단계 만들어줘"
AI: → 03_visualization.ipynb 생성
사용자: (실행 후) "결과 저장해줘"
AI: → step3_viz.json 저장, current_step: "state_analysis"

[Step 4: State Analysis]
사용자: "다음 단계 만들어줘"
AI: → guides/stats.md 참조 → 04_state_analysis.ipynb 생성
사용자: (실행 후) "결과 저장해줘"
AI: → step4_state.json 저장, current_step: "writing"

[Step 5: Writing]
사용자: "다음 단계 만들어줘"
AI: → guides/writing.md 참조 → step5_draft_method.md, step5_draft_results.md 생성
AI: → current_step: "proofreading"

[Step 6: Proofreading]
사용자: "다음 단계 만들어줘" 또는 "프루프리딩해줘"
AI: → guides/proofreading_guide.md 참조 → step6_proofreading_report.md 생성
AI: → current_step: "revision"

[Step 7: Revision]
사용자: "다음 단계 만들어줘"
AI: → guides/revision.md 참조 → step7_revised_method.md, step7_revised_results.md 생성
AI: → current_step: "done"
```

---

## 중요 참고사항

1. **Planned Missingness**: SAPA의 결측은 오류가 아니라 설계된 것
2. **가이드 문서**: 각 단계별 `guides/` 폴더의 가이드 반드시 참조
3. **출력 위치**: 
   - 점수 데이터 → `data/processed/`
   - 분석 결과 → `reports/`
   - 그림 → `reports/figures/`
4. **컬럼명 규칙**: Big Five는 약어 사용 (NEO_O, NEO_C, NEO_E, NEO_A, NEO_N)
5. **Overclaiming 방지**: Results 작성 시 "meaningful" → "statistically significant" 등 보수적 표현 사용
