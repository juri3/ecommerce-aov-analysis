# 매출은 성장하는데 왜 AOV는 오르지 않는가
### AOV 정체 원인 분석 및 전략 제안

---

## 프로젝트 개요

이커머스 쇼핑몰 데이터를 활용해 **거래건수는 증가하지만 AOV(평균 주문 금액)가 정체되는 원인**을 분석하고, 데이터 기반 개선 전략을 제안한 포트폴리오입니다.

---

## 분석 목적

- 거래건수 3배 이상 성장에도 AOV가 550,000 IDR 내외로 정체
- 단일 원인이 아닌 복합적 구조 문제로 접근
- 가설 검증 → 세그먼트 분석 → 퍼널 분석 순으로 원인 탐색

---

## 분석 구조

```
1. 비즈니스 문제 정의     매출 성장이 거래건수 증가에만 의존, AOV 정체 확인
2. 가설 검증             3가지 가설 구조화 및 검증
   A. 신규고객 증가 → 기각 (신규고객 비율 오히려 감소)
   B. 프로모션 구조 문제 → 부분 채택 (고율 할인 구간에 저가 상품 집중)
   C. 고가 세그먼트 이탈 → 기각 (고가 구매 비율 25%로 일정)
3. 세그먼트 분석         연령대 × 성별 × 카테고리 교차 분석
4. 퍼널 분석             이벤트 도달률 분석 (순차 퍼널 한계 검토 포함)
5. 전략 제안             단기/중기/장기 실행 우선순위 기반 전략
6. A/B 테스트 설계       전략별 검증 실험 설계
7. KPI                  분석 연계 성과 측정 기준
```

---

## 핵심 인사이트

- **AOV 정체는 고객/상품 구성의 문제가 아님** — 세그먼트 및 카테고리별 AOV 차이 미미
- **HOMEPAGE → ITEM_DETAIL 미진입률 41%** — 상세페이지 진입 시 AOV 3%, CVR 2%p 개선 효과 확인
- **고율 할인(3%+) 구간에 저가 상품 집중** — 프로모션 구조가 AOV 상승을 제한할 가능성

---

## 데이터셋

| 테이블 | 설명 | 주요 컬럼 |
|--------|------|-----------|
| customer | 고객 정보 | customer_id, birthdate, gender |
| product | 상품 정보 | id, masterCategory, subCategory |
| transactions | 거래 내역 | booking_id, customer_id, total_amount, promo_amount |
| click_stream | 행동 로그 | session_id, event_name, event_time, traffic_source |

> 출처 : [Kaggle E-commerce Transactional Dataset](https://www.kaggle.com/)  
> 분석 기간 : 2019 ~ 2022 (4개년)

---

## 사용 기술

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat&logo=tableau&logoColor=white)

---

## 분석 한계

- 캐글 시뮬레이션 데이터로 실제 비즈니스 패턴과 차이가 있을 수 있음
- click_stream의 session_id가 실제 접속 세션 단위와 상이해 순차 퍼널 적용 불가
  - 30분 기준 세션 재정의 시도했으나 세션당 이벤트 중앙값 1건으로 한계 확인
  - 세션 내 이벤트 포함 여부 기준으로 도달률 측정으로 전환
- 프로모션 비용 데이터 없어 ROI 직접 측정 불가
- 50대 여성 세그먼트 등 일부 표본 부족으로 통계적 신뢰도 제한

---

## 대시보드

분석 결과를 시각화한 Tableau 대시보드를 아래 링크에서 확인할 수 있습니다.

🔗 [Tableau Public 바로가기](https://public.tableau.com/여기에주소)

**구성** : 비즈니스 현황 / 가설 검증 / 세그먼트 분석 / 퍼널 분석 / KPI 모니터링
