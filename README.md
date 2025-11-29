# FinNLP-Contrarian: AI 기반 역발상 투자 가설 검증

> "거리에 피가 흐를 때 매수하라 (Buy when there's blood in the streets)."
>
> 금융 특화 NLP 모델을 활용하여 16년(2008-2024) 간의 S&P 500 시장 심리와 주가 변동성의 상관관계를 분석한 연구 프로젝트입니다.

## 프로젝트 개요 (Project Overview)
본 프로젝트는 경제학의 오랜 격언인 '역발상 투자(Contrarian Investing)' 전략이 현대 주식 시장에서도 유효한지 데이터 과학적 방법론으로 검증하고자 시작되었습니다.

2008년 글로벌 금융위기부터 2024년 AI 랠리까지의 S&P 500 관련 주요 금융 뉴스 헤드라인 19,000여 건을 확보하여 텍스트 마이닝을 수행했습니다. 단순한 감성 분석을 넘어, **금융 도메인 지식이 결합된 AI 모델링(Loughran-McDonald)**이 범용 모델 대비 얼마나 우수한 성과를 내는지 입증하는 데 초점을 맞췄습니다.

## 핵심 가설 (Key Hypotheses)
1. **공포와 기회:** 뉴스 헤드라인에 나타난 시장의 부정적 심리(공포)가 극에 달했을 때, 실제 주가는 바닥을 치고 반등하는가?
2. **선행 지표:** 텍스트에서 추출한 '심리 지수'가 S&P 500 지수의 향후 변동성을 예측하는 유의미한 선행 지표(Leading Indicator)가 될 수 있는가?

## 연구 방법 (Methodology)

### 1. 데이터 확보 및 전처리 (Data Acquisition & Preprocessing)
* **데이터셋:** S&P 500 일별 종가 및 주요 금융 언론사(Bloomberg, Reuters 등) 뉴스 헤드라인 (약 19,000건)
* **분석 기간:** 2008년 1월 ~ 2024년 3월 (약 16년)
* **전처리:** 결측치 제거, 텍스트 토큰화(Tokenization), 뉴스 데이터와 주가 데이터의 시계열 정렬(Time-series Alignment)

### 2. 비교 감성 분석 (Comparative Sentiment Analysis)
도메인 적합성(Domain Adaptation)의 중요성을 입증하기 위해 두 가지 모델을 비교 분석했습니다.

* **Baseline (VADER):** 소셜 미디어 분석에 최적화된 일반 감성 분석 모델.
    * *결과:* 금융 뉴스 특유의 건조한 사실 전달(Fact-based) 문체를 '감정 없음(Neutral, 0.0)'으로 오분류하는 한계 노출.
* **Proposed (Loughran-McDonald):** 금융 문서 분석을 위해 설계된 특화 사전(Dictionary) 기반 모델.
    * *결과:* VADER가 놓친 'Profit(이익)', 'Loss(손실)', 'Recession(침체)' 등의 재무적 뉘앙스를 정확히 포착하여 유의미한 심리 점수 산출.

### 3. 통계적 검증 (Statistical Validation)
* **추세 분석 (Trend Analysis):** 일별 심리 점수에 **120일(약 6개월) 이동평균**을 적용하여 단기 노이즈를 제거하고 거시적인 시장 심리 추세(Trend)를 도출.
* **상관관계 분석 (Correlation):** 도출된 심리 지수와 **향후 1개월(20 거래일) 간의 S&P 500 수익률** 간의 상관관계 분석 수행.

## 핵심 결과 (Key Findings)
1. **도메인 특화 모델의 우수성 입증:** 금융 텍스트 분석 시, 범용 모델(VADER)보다 금융 특화 사전(LM)이 시장의 위기 신호를 훨씬 더 민감하게 포착함을 확인. 이는 금융 분석에서 도메인 지식의 결합이 필수적임을 시사함.
2. **역발상 가설 검증:** 120일 이동평균 심리 지수와 미래 수익률 간에 **-0.19의 음의 상관관계**가 관찰됨.
    * *해석:* 시장 심리가 부정적일수록(공포 국면), 향후 수익률은 오히려 상승하는 경향이 있으며, 이는 통계적으로 유의미함.

## 기술 스택 (Tech Stack)
* **Language:** Python
* **Data Analysis:** Pandas, NumPy
* **NLP Models:** vaderSentiment, pysentiment2 (Loughran-McDonald Dictionary)
* **Visualization:** Matplotlib, Seaborn
* **Statistics:** SciPy (Pearson Correlation, P-value)

---
*본 프로젝트는 경제학적 통찰(Economic Insights)과 데이터 과학 기술(Data Science)의 융합을 목표로 수행되었습니다.*
