# ruble-oil-fx

본 저장소는 논문 **「러시아·우크라이나 전쟁 이후 루블화의 유가–환율 연계성 변화: 구조변화와 예측정보 분석」**의 재현성 패키지입니다.

## 연구 개요

본 연구는 러시아·우크라이나 전쟁 이후 러시아 루블화의 유가–환율 연계성이 변화하였는지를 분석합니다. 러시아 루블화, 우크라이나 흐리우냐화, 한국 원화를 2022년 2월 24일 전후로 비교하고, 추가 비교통화로 JPY, EUR, CAD, NOK, KZT를 사용합니다.

## 자료 출처

자료는 `yfinance` 패키지를 통해 Yahoo Finance에서 수집합니다.

- 자료 출처: Yahoo Finance via `yfinance`
- 빈도: 주간 자료 (`interval="1wk"`)
- 표본 기간: 2019년 1월부터 2026년 4월까지
- 구조변화 기준일: 2022년 2월 24일

## 환율 정의

환율 변수는 **미국 달러 1단위당 자국통화 단위**로 측정합니다.

따라서 환율 변수가 상승하면 해당 통화가 미국 달러 대비 절하되었음을 의미합니다.

| 변수 | Yahoo Finance 티커 | 해석 |
|---|---|---|
| RUB | `RUB=X` | 미국 달러당 러시아 루블 |
| UAH | `UAH=X` | 미국 달러당 우크라이나 흐리우냐 |
| KRW | `KRW=X` | 미국 달러당 한국 원 |
| JPY | `JPY=X` | 미국 달러당 일본 엔 |
| CAD | `CAD=X` | 미국 달러당 캐나다 달러 |
| NOK | `NOK=X` | 미국 달러당 노르웨이 크로네 |
| KZT | `KZT=X` | 미국 달러당 카자흐스탄 텡게 |
| EUR | `EURUSD=X` | 원자료는 유로당 미국 달러이므로, 분석 전 미국 달러당 유로로 역수 변환 |

## 주요 분석

- OLS 회귀분석
- Granger 예측력 검정
- GARCH(1,1) 변동성 모형
- Chow 구조변화 검정
- Newey–West HAC 보조 상호작용 분석
- COVID-19 유가폭락 구간 제외 강건성 검정
- Student-t GARCH 민감도 분석
- 추가 비교집단 분석

## 실행 방법

```bash
git clone https://github.com/<YOUR_GITHUB_ID>/ruble-oil-fx.git
cd ruble-oil-fx
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

그 다음 아래 노트북을 실행합니다.

```text
notebooks/01_full_replication.ipynb
```

강건성 분석만 실행하려면 아래 노트북을 사용합니다.

```text
notebooks/02_appendix_robustness_checks.ipynb
```

## 라이선스

- 코드: MIT License
- 원자료: 사용자가 Yahoo Finance에서 직접 다운로드하며, 본 저장소에서는 원자료를 재배포하지 않습니다.
