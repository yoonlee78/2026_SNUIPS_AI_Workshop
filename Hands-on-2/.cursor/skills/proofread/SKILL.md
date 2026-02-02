---
name: proofread
description: 학술 문서를 검토하고 평가합니다. "프루프리딩", "proofread", "논문 검토", "Methods 평가", "Results 평가", "overclaim 분석" 요청 시 사용.
---

# Proofreading Skill

학술 문서를 Nature 리뷰어 관점에서 검토하고 평가합니다.

> 상세 가이드는 `guides/proofreading_guide.md` 참조

---

## 동작 순서

1. **GitHub 파일 참조** (필요시)
   - 사용자가 제공한 GitHub 링크에서 원본 문서 확인
   - 관련 코드/데이터 파일 검토

2. **Methods 섹션 평가**
   - 5가지 측면에서 약점 지적:
     - Reproducibility (재현성)
     - Controls (통제)
     - Sample size/power (샘플/검정력)
     - Statistical appropriateness (통계 적절성)
     - Validation (타당성)
   - 각 약점에 대해: 구체적 문제점, 리뷰어 예상 질문, 개선 방안 제시

3. **Results 섹션 평가**
   - 각 문장별 분석:
     - Claim type (causal/correlational/mechanistic/general)
     - Evidence level (direct/indirect/suggestive)
     - Overclaiming risk (1-10)
     - Conservative alternative phrasing
   - 가장 위험한 overclaim 3개 지적 및 수정 방법 제시

4. **종합 프루프리딩**
   - 평가 결과 통합
   - 수정 사항 도출
   - 최종 권고안 작성

---

## Methods 평가 프롬프트

```
다음 Methods 섹션을 Nature 리뷰어 관점에서 평가해줘:

[Methods text를 여기에 붙여넣기]

다음 5가지 측면에서 약점을 지적해줘:

1. Reproducibility (재현성)
2. Controls (통제)
3. Sample size/power (샘플/검정력)
4. Statistical appropriateness (통계 적절성)
5. Validation (타당성)

각 약점에 대해 다음을 제시해줘:
- 구체적 문제점
- 리뷰어가 제기할 질문
- 개선 방안
```

---

## Results 평가 프롬프트

```
다음 Results 문장들을 분석해줘:

[Results text with claims를 여기에 붙여넣기]

각 문장에 대해 다음을 분석해줘:
1. Claim type (causal/correlational/mechanistic/general)
2. Evidence level (direct/indirect/suggestive)
3. Overclaiming risk (1-10)
4. Conservative alternative phrasing

그리고:
- 가장 위험한 overclaim 3개 지적
- 각각을 데이터에 맞게 수정하는 방법
```

---

## 체크리스트

### Methods 관련
- [ ] 모든 재현성 문제점이 해결되었는가?
- [ ] 통제 조건이 명확히 기술되었는가?
- [ ] 표본 크기/검정력 정당화가 포함되었는가?
- [ ] 통계 방법이 적절히 선택되고 기술되었는가?
- [ ] 검증 절차가 포함되었는가?

### Results 관련
- [ ] 모든 고위험 overclaim이 수정되었는가?
- [ ] Claim type과 evidence level이 일치하는가?
- [ ] 인과적 표현이 적절히 사용되었는가?
- [ ] 제한점이 명시되었는가?

### 전체 문서
- [ ] 일관된 용어 사용
- [ ] 논리적 흐름
- [ ] 문법/철자 오류 없음
- [ ] 참고문헌 정확성

---

## 참고

> 평가 기준, 출력 템플릿, 참고 문서 목록은 모두 `guides/proofreading_guide.md` 참조