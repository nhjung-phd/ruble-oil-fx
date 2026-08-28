# 재현성 자료: 러시아 루블화의 유가–환율 연계성 변화

이 저장소는 다음 논문의 재현성 자료를 제공합니다.

**Changes in the Russian Ruble’s Oil–Exchange Rate Linkage after the Russia–Ukraine War: An Analysis of Structural Change and Predictive Information**

최종 소스 노트북은 `notebooks/01_full_replication.ipynb`입니다. 노트북을 실행하면 표와 그림이 노트북 안에 바로 출력됩니다. 기본적으로 `outputs/` 폴더를 만들지 않으며, CSV·Excel·PNG·PDF 파일을 저장하지 않습니다.

## 실행 방법

Google Colab 또는 로컬 Jupyter 환경에서 다음 파일을 실행하면 됩니다.

```text
notebooks/01_full_replication.ipynb
```

로컬 실행 시에는 다음 명령어로 패키지를 설치할 수 있습니다.

```bash
pip install -r requirements.txt
```

## 환율 정의

모든 환율 변수는 **미국 달러 1단위당 현지통화 단위**로 정의합니다. 따라서 RUB, UAH, KRW, JPY, CAD, NOK, KZT 값이 상승하면 해당 통화가 미국 달러 대비 절하된 것으로 해석합니다. `EURUSD=X`는 Yahoo Finance에서 유로 1단위당 미국 달러로 제공되므로, 분석 전 역수 변환하여 유로 per USD 기준으로 맞춥니다.

## 자료 출처

자료는 `yfinance` 패키지를 통해 Yahoo Finance에서 다운로드하며, 원자료는 이 저장소에 재배포하지 않습니다.
