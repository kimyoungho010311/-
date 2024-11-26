
### resorce of the data  
-> [uci-secom](https://www.kaggle.com/datasets/paresh2047/uci-semcom)

---
# 불균형 데이터 분류 모델 성능 비교 분석

## 1. 개요
다양한 분류 모델에 대해 **불균형 데이터 문제**를 해결하기 위한 실험을 진행하였습니다. 주요 모델로는 **XGBoost**, **Random Forest**, **Logistic Regression**, **Lasso**가 포함되었으며, 데이터 샘플링 방법으로 **언더샘플링**과 **오버샘플링**을 적용하였습니다. 각 모델의 성능은 **Accuracy**, **Recall**, **Precision**, **F1-score**를 기준으로 평가하였습니다.

---

## 2. 모델별 성능 요약

### 2.1 XGBoost
- **Normal (정상 데이터)**:
  - Accuracy: **93.2%**
  - Recall: **0**
  - Precision: **0**
- **Under (언더샘플링)**:
  - F1-score: **0.628**
- **Over (오버샘플링)**:
  - F1-score: **0.502**

### 2.2 Random Forest
- **Normal (정상 데이터)**:
  - Accuracy: **93.2%**
  - Recall: **0**
  - Precision: **0**
- **Under (언더샘플링)**:
  - F1-score: **0.652**
- **Over (오버샘플링)**:
  - F1-score: **0.664**

### 2.3 Logistic Regression
- **Normal (정상 데이터)**:
  - Accuracy: **90.6%**
  - Recall: **0.125**
  - Precision: **0.25**
  - F1-score: **0.167**
- **Under (언더샘플링)**:
  - F1-score: **0.657**
- **Over (오버샘플링)**:
  - F1-score: **0.719**

### 2.4 Lasso
- **Normal (정상 데이터)**:
  - Accuracy: **0**
  - Recall: **0**
  - Precision: **0**
  - F1-score: **0**
- **Under (언더샘플링)**:
  - F1-score: **0.020**
- **Over (오버샘플링)**:
  - Recall: **1**
  - Precision: **0.555**
  - F1-score: **0.714**

---

## 3. 샘플링 기법별 성능 분석

### 3.1 Normal (정상 데이터)
- 모든 모델에서 Accuracy는 높지만, Recall과 Precision은 매우 낮거나 **0**으로 불균형 문제 해결에 한계가 있음.

### 3.2 Under (언더샘플링)
- 샘플링으로 소수 클래스의 비율이 높아지면서 F1-score가 개선됨.
- Random Forest와 Logistic Regression에서 비교적 우수한 성능을 보임(F1-score: **0.65** 수준).

### 3.3 Over (오버샘플링)
- 대부분의 모델에서 가장 높은 성능을 기록.
- Logistic Regression이 F1-score **0.719**로 최상의 성능을 기록.

---

## 4. 결론 및 추천

1. **최고 성능 모델**:
   - Logistic Regression이 오버샘플링 환경에서 F1-score **0.719**로 가장 높은 성능을 기록하였음.
2. **샘플링 기법**:
   - 오버샘플링(SMOTE)이 언더샘플링 대비 전체적으로 더 나은 성능을 보였음.
3. **Lasso 모델**:
   - 대부분의 실험에서 낮은 성능을 기록하며 불균형 데이터 문제 해결에는 적합하지 않음.

---

## 5. 향후 개선 방향
- **Logistic Regression** 기반으로 추가적인 하이퍼파라미터 튜닝 및 데이터 전처리를 통해 성능을 더욱 개선 가능.
- **Random Forest** 및 **XGBoost**에서도 추가적인 실험을 통해 성능 향상을 도모할 여지가 있음.
- **특성 중요도(Feature Importance)** 분석을 통해 주요 변수(예: 72번, 74번, 45번 변수)를 활용한 모델 최적화를 고려.

---

위 결과를 바탕으로, Logistic Regression과 SMOTE 기반의 데이터 증강이 현재 데이터셋에서 가장 효과적인 접근법으로 판단됩니다.
