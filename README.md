# Cosmetics HS Classification

화장품 완제품 HS 코드 분류 프로젝트의 코드 저장소입니다.

## 구성

- `notebooks/01_TFIDF_LinearSVC_Baseline.ipynb`: 코드만 포함한 경량 Google Colab 노트북
- `src/`: 추후 재사용 함수 및 실험 코드를 관리하는 폴더
- 학습 데이터와 모델 파일은 저장소에 포함하지 않고 Google Drive에 별도 보관합니다.

## Colab 실행

1. 이 저장소를 GitHub에 업로드합니다.
2. Google Drive의 `MyDrive/HS_cosmetics_project/` 폴더에 `완제품 모델 테스트셋.xlsx`를 업로드합니다.
3. GitHub의 노트북 파일을 열어 `Open in Colab` 또는 Colab의 GitHub 탭에서 불러옵니다.
4. 셀을 위에서부터 실행하고 Google Drive 접근을 승인합니다.
5. 결과와 최종 모델은 같은 Drive 폴더에 저장됩니다.

## 현재 베이스라인

- 특징 추출: 각 입력 필드별 문자 단위 TF-IDF (2~5-gram), 품명에는 단어 단위 TF-IDF (1~2-gram) 추가
- 분류기: LinearSVC (`class_weight='balanced'`, `C=1.0`)
- 입력: 품명, 주요성분, 물품형태·포장, 용도, 제품유형
- 정답: 결정세번
- `판정요지`는 정보 누수 가능성 때문에 입력에서 제외
- 교차검증: 2-Fold Stratified CV

주의: 현재 사용 데이터의 `사례_중복제거` 시트에는 사례ID가 없어 사례ID 기준 Group CV는 수행하지 않습니다. 평가 결과는 예비 성능이며 일반화 성능을 보장하지 않습니다.
