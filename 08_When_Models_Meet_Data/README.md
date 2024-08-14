# 8. When Models Meet Data

## 8.1 Data, Models and Learning
- Data, Model, Learning은 기계 학습 시스템의 주요 요소

### 8.1.1 Data as Vectors

<img width="563" alt="스크린샷 2024-08-14 오후 5 09 49" src="https://github.com/user-attachments/assets/430cf8f1-63d0-455e-b3ef-dd144c286f9e">

- 데이터는 위처럼 표현
- 행은 instance 혹은 example이라고 표현하고, 열은 특정한 Feature를 나타낸다고 한다.
- 데이터를 분석하기 위해서는 다양한 전처리 과정이 필요하다.
  - 단순한 예시로 Gender feature를 1과 -1로 나누고 학위 Degree를 학사, 석사, 박사 순서대로 1~3으로 나타내고, Postcode를 위도와 경도로 표현할 수 있다. 또한 Annual salary는 수치가 너무 크기 때문에 천 단위로 줄여서 다음과 같이 표현할 수 있다.
<img width="629" alt="스크린샷 2024-08-14 오후 5 10 04" src="https://github.com/user-attachments/assets/e7a87314-8336-409d-86cf-e3681ed637d8">

- 이 책에서는 이러한 전처리 과정들이 이미 적절히 이루어졌다고 가정한다.

### 8.1.2 Models as Functions

### 8.1.3 Models as Probability Distributions
- Data에는 원초적인 효과로 인해 노이즈가 자주 발생하고, 머신러닝을 학습할 때는 이러한 노이즈 속에서도 특별한 Signal을 발견하는 것이 목적이다.
- 그러기 위해서는 **노이즈를 수치화**할 수 있어야 한다.
  - 확률 이론과 분포가 이를 가능하게 해준다.
- 확률 이론을 활용해 Predictor Function을 표현하면, 좀 더 정확하게 예측을 수행할 수 있다.

### 8.1.4 Learning is Finding Parameters

- 머신러닝 알고리즘을 수행하는 대표적인 세 가지 단계는 다음과 같다.
  - Prediction of Inference (예측, 추론)
  - Training of Parameter Estimation (훈련, 파라미터 평가)
  - Hyperparameter Tuning or Model Selection (하이퍼파라미터 조정, 모델 선택)

## 8.3 Parameter Estimation (파라미터 추정)

### 8.3.1 Maximum Likelihood Estimation (최대 우도 측정)

- `Maximum Likelihood Estimation(MLE)`의 핵심은 데이터에 적합한 모델을 찾을 수 있도록 하는 파라미터의 함수를 정의하는 방법이다.
- Estimation 문제는 likelihood function, 더 정확하게는 이의 negative logarithm에 초점을 맞춘다.

- 확률 변수 $x$로 대표되는 데이터와 $\theta$에 관한 확률 밀도 $p(x|\theta)$의 계열의 경우, negative log-likelihood는 아래와 같다.

<img width="692" alt="스크린샷 2024-08-14 오후 6 53 10" src="https://github.com/user-attachments/assets/68c361e7-3ed3-4088-93a5-0d25702aa939">

### 8.3.2 Maximum A Posteriori Estimation (최대 사후 확률 측정)
- MAP 추정은 MLE와 유사하지만, 사전 확률을 포함하여 파라미터의 사후 확률을 최대화하는 방법
- 베이즈 정리를 통해 사후 확률을 계산하고, 이 확률을 최대화하는 $\theta$를 찾는다.
<img width="475" alt="스크린샷 2024-08-14 오후 8 29 23" src="https://github.com/user-attachments/assets/266017e0-8d6a-4bb6-84c9-d3daea7160ba">

## 8.4 Probabilistic Modeling and Inference (확률적 모델링 및 추론)

### 8.4.1 Probabilistic Models (확률론적 모델)
- 확률론적 모델은 데이터 생성 과정을 확률 분포로 모델링
  - 데이터가 주어졌을 때, 이 데이터를 설명하는 가장 적합한 확률 분포를 찾는 것이 목표

### 8.4.2 Bayesian Inference (베이지안 추론)
- 베이지안 추론은 주어진 데이터에 대한 사전 지식(사전 확률)을 바탕으로, 데이터를 관찰한 후에 **사후 확률**을 계산하는 방법
- 데이터셋 $\chi$에 대해, parameter prior $p(\theta), 우도 함수, posterior은 베이즈 정리르 통해 아래의 식을 얻을 수 있다.

<img width="582" alt="image" src="https://github.com/user-attachments/assets/85c96011-e544-45c6-8b32-b8b4a5ecd0fd">

- 여기의 핵심 아이디어는 베이즈 정리를 통해 파라미터 $\theta$와 데이터 $\chi$ 사이의 관계를 역전 시켜 사후 분포 $p(\theta|\chi)$를 얻는 것이다.

### 8.4.3 Latent-Variable Models (잠재 변수 모델)
- 잠재변수 모델은 파라미터로부터 데이터를 생성하는 과정을 정의할 수 있다.


## 참고 자료
- https://savanna.korea.ac.kr/wp/?page_id=1294
