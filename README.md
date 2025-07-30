# 📈 HyperInsight: 실시간 스트리밍 데이터 기반 투자성향별 시나리오 브리핑 서비스

> **"뉴스의 파편 속에서 전략을 읽어주는 AI"** 
> 관심 종목과 뉴스 이슈의 유사도를 계산하고,  
> 투자자 성향에 맞는 전략 시나리오를 자동 생성합니다.

---

## 🚨 문제 인식

- 방대한 뉴스 속에서 내 종목과 관련된 이슈만 추려내기 어렵고,  
- 정책 변화나 글로벌 이벤트의 투자 영향은 개인이 해석하기엔 너무 복잡합니다.

👉 따라서  
① 뉴스 요약  
② 관심 종목과의 유사도 분석  
③ 투자 성향에 맞는 전략 생성  
이 세 과정을 **자동화한 브리핑 시스템**이 필요합니다.

---

## 🔍 서비스 구성

| 단계 | 설명 |
|------|------|
| 1. 뉴스 요약 | KoBART 또는 Clova Summary API 사용 |
| 2. 유사도 분석 | 요약문과 관심 종목 키워드 간 코사인 유사도 계산 |
| 3. 전략 생성 | HyperCLOVA X 프롬프트 체이닝을 통한 성향 기반 전략 출력 |

---

## 🧠 기술 요약

- **LLM 기반 전략 프롬프트 설계:** HyperCLOVA X 활용  
- **뉴스 요약:** KoBART 또는 Clova Summary API 기반  
- **유사도 분석:** 요약문과 종목 키워드 간 코사인 유사도 계산  
- **성향 반영:** 위험 선호도 및 투자 기간에 따른 프롬프트 분기  
- **전체 파이프라인:** Google Colab 기반 MVP 구현 + Streamlit 데모 배포

---

## 🖥️ 실행 방법

### ▶️ 1. [Streamlit 데모 실행하기](https://miraeasset-2025-mgffvwkge3srevnq3peswg.streamlit.app)

> 사용자가 직접 뉴스와 성향을 입력하고, HyperCLOVA 기반 전략 보고서를 생성할 수 있습니다.

#### 🪄 사용법
1. **뉴스 요약문 입력**
2. **관심 종목 입력** (쉼표로 구분, 예: 삼성전자, 두산로보틱스)
3. **경제 지표 / 기술 지표 입력** (기본값 제공)
4. **투자 성향 설정**
   - 리스크 선호도 (예: 중립)
   - 투자 기간 (예: 중기)
   - 관심 섹터 (예: 2차전지)
5. **[보고서 생성] 버튼 클릭**
6. 자동 생성된 전략 보고서를 확인하고 `.md` 파일로 다운로드 가능

---

### ▶️ 2. [Google Colab 실행하기](https://colab.research.google.com/github/hojiahn/miraeasset-2025/blob/main/%EB%AF%B8%EB%9E%98%EC%97%90%EC%85%8B.ipynb#scrollTo=oZbBAeBR_gZw)

> 사전 뉴스 파일과 종목 키워드 기반으로 자동 보고서를 생성하는 방식입니다.

#### 🪄 실행 순서
1. 셀을 위에서부터 실행
2. 뉴스 입력: `merged_news_summaries_cleaned.xlsx`
3. 종목 키워드 유사도 분석: `filtered_similarity.csv`
4. 전략 보고서 생성: `report_template.md` 템플릿 사용

---

### ▶️ 3. 로컬 실행

```bash
git clone https://github.com/hojiahn/miraeasset-2025.git
cd miraeasset-2025
pip install -r requirements.txt
streamlit run app.py
```

---

## 📊 Sample 결과 예시

- **뉴스 요약문:**  
  “트럼프 2기 행정부에서 미국이 자랑하는 ‘자유방임’ 시장 질서에 중대 변화가 감지되고 있는 것은  
  정부가 개입해 수출과 생산은 물론 제품 원료까지 통제하는 ‘국가 자본주의’의 출현이다.  
  바이든 행정부는 역내 투자 기업에 보조금과 정부 대출을 지원하는 ‘칩스법’을 제정해  
  대만 TSMC, 삼성전자 등 외국 반도체 기업을 국내로 유인하는 전략을 취했다.”

- **관심 종목:** 삼성전자  
- **투자 성향:** 위험중립형  

- **전략 시나리오 출력:**  
  > “미국 정부의 반도체 산업 개입 확대는 삼성전자에 긍정적인 기회로 작용할 수 있습니다.  
  > 중장기 보유 전략이 유효하며, 분할 매수 관점에서 접근하는 것이 바람직합니다.”

---

## ✅ 핵심 차별성

- ✅ 관심 종목 기반 뉴스 필터링 및 유사도 점수화
- ✅ 투자자 성향(위험 성향·보유 기간) 기반 전략 분기
- ✅ HyperCLOVA X 활용 자동 전략 생성
- ✅ 전체 파이프라인 Google Colab 기반 MVP + Streamlit UI 구현

---

## 📁 파일 구성

| 파일명 | 설명 |
|--------|------|
| `app.py` | Streamlit 실행용 메인 코드 |
| `report_template.md` | Jinja2 템플릿 (전략 보고서 형식) |
| `requirements.txt` | 의존 패키지 목록 |
| `final_report.md` | 샘플 보고서 |
| `미래에셋.ipynb` | Colab 기반 전략 생성 노트북 |
| `merged_news_summaries_cleaned.xlsx` | 뉴스 요약문 데이터 |
| `dart_summaries_cleaned.xlsx` | 공시 요약 데이터 |
| `filtered_similarity.csv` | 관심 종목과의 유사도 결과 |

---

## 🏁 구현 범위 및 한계

- ✅ 핵심 파이프라인: 뉴스 → 유사도 → 성향 기반 전략 생성까지 완성
- ✅ HyperCLOVA X 기반 실제 LLM 응답 연동
- ✅ Colab + Streamlit 모두 MVP 수준 구현 완료
- ❌ 실시간 뉴스 크롤링, 사용자 맞춤 알림 등은 추후 고도화 예정

---

## 🙌 팀 소개 및 기여 방식

> 본 프로젝트는 미래에셋 AI 공모전 2025 참가를 위해 제작되었습니다.  
> 관심 있으신 분들은 언제든지 Fork & Star 환영합니다!

