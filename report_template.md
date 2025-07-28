# 투자 전략 보고서: {{ title }}
*보고서 생성일: {{ date }}*

---

## 목차
1. 서론
2. 뉴스 요약
3. 시장 상황
4. 사건 분석
5. 투자 전략
   5.1 기간별·성향별 전략 요약
   5.2 핵심 종목별 전략 포인트
   5.3 전체 비중·가정·리스크
6. 투자자 유형별 안내
7. 시나리오별 대응 방안
8. 결론
9. 면책 조항
10. 데이터 출처 및 업데이트 주기

---

## 1. 서론
- **보고서 목적**: {{ intro.purpose }}
- **분석 범위**: {{ intro.scope }}

---

## 2. 뉴스 요약
- **요약**: {{ news.summary }}
- **핵심 키워드**: {{ news.keywords | join(', ') }}

---

## 3. 시장 상황

### 3.1 경제 지표
- KOSPI: {{ market.kospi }}
- 환율 (원/달러): {{ market.fx }}
- 기준 금리: {{ market.rate }}

### 3.2 기술 지표
- RSI (14일): {{ market.rsi }}
- MACD: {{ market.macd }}
- 거래량: {{ market.volume }}
- 기타: {{ market.other }}

---

## 4. 사건 분석

### 4.1 사건 설명
{{ event.description }}

### 4.2 주가 영향 분석
| 시점             | 영향 요인                        | 설명                          |
| ---------------- | -------------------------------- | ----------------------------- |
| 단기 (1주)       | {{ event.impact.short.factor }}  | {{ event.impact.short.desc }} |
| 중기 (1개월)     | {{ event.impact.mid.factor }}    | {{ event.impact.mid.desc }}   |
| 장기 (3개월 이상)| {{ event.impact.long.factor }}   | {{ event.impact.long.desc }}  |

---

## 5. 투자 전략

### 5.1 기간별·성향별 전략 요약
| 투자 기간        | 안정형                 | 안정추구형                 | 위험중립형                | 적극투자형                   | 공격투자형                        |
| ---------------- | ---------------------- | -------------------------- | ------------------------- | ---------------------------- | --------------------------------- |
| 단기 (1주)       | {{ strat.short.cons }} | {{ strat.short.cautious }} | {{ strat.short.neutral }} | {{ strat.short.aggressive }} | {{ strat.short.very_aggressive }} |
| 중기 (1개월)     | {{ strat.mid.cons }}   | {{ strat.mid.cautious }}   | {{ strat.mid.neutral }}   | {{ strat.mid.aggressive }}   | {{ strat.mid.very_aggressive }}   |
| 장기 (3개월 이상)| {{ strat.long.cons }}  | {{ strat.long.cautious }}  | {{ strat.long.neutral }}  | {{ strat.long.aggressive }}  | {{ strat.long.very_aggressive }}  |

### 5.2 핵심 종목별 전략 포인트
{% for stock, point in strat.points.items() %}
- **{{ stock }}**: {{ point }}
{% endfor %}

### 5.3 전체 비중·가정·리스크
- **전체 비중**: {{ strat.total_weight }}
- **주요 가정**:
  {% for assumption in strat.assumptions %}- {{ assumption }}
  {% endfor %}
- **주요 리스크**:
  {% for risk in strat.risks %}- {{ risk }}
  {% endfor %}

---

## 6. 시나리오별 대응 방안
{% for s in scenarios %}
- **{{ s.name }} ({{ s.level }})**: {{ s.action }}
{% endfor %}

---

## 7. 결론
{{ conclusion }}

---

## 8. 면책 조항
본 자료는 정보 제공용이며, 특정 매매 권유가 아닙니다.
최종 투자 결정 및 책임은 투자자 본인에게 있습니다.

---

## 9. 데이터 출처 및 업데이트 주기
- **데이터 출처**: {{ data.source }}
- **업데이트 주기**: {{ data.freq }}
