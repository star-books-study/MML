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
- 데이터셋 $\chi$에 대해, parameter prior $p(\theta)$, 우도 함수, posterior은 베이즈 정리르 통해 아래의 식을 얻을 수 있다.

<img width="582" alt="image" src="https://github.com/user-attachments/assets/85c96011-e544-45c6-8b32-b8b4a5ecd0fd">

- 여기의 핵심 아이디어는 베이즈 정리를 통해 파라미터 $\theta$와 데이터 $\chi$ 사이의 관계를 역전 시켜 사후 분포 $p(\theta|\chi)$를 얻는 것이다.

### 8.4.3 Latent-Variable Models (잠재 변수 모델)
- 잠재변수 모델은 파라미터로부터 데이터를 생성하는 과정을 정의할 수 있다.


---

# 비교: Maximum Likelihood Estimation (MLE), Maximum A Posteriori (MAP), 그리고 Bayesian Inference



## 1. Maximum Likelihood Estimation (MLE)

### 1.1 개요
- Maximum Likelihood Estimation (MLE)은 주어진 데이터를 가장 잘 설명하는 파라미터 값을 찾는 방법
- 즉, 관측된 데이터를 가장 높은 확률로 생성할 수 있는 파라미터를 찾는 것

### 1.2 수학적 정의
- MLE는 다음과 같은 우도(likelihood) 함수를 최대화하는 파라미터 $\theta$를 찾는다.

$$
\[
\hat{\theta}_{MLE} = \arg\max_{\theta} \ L(\theta) = \arg\max_{\theta} \ p(\chi|\theta)
\]
$$

- 우도를 로그 변환한 negative log-likelihood를 최소화하는 방식으로 문제를 풀기도 한다.

$$
\[
\hat{\theta}_{MLE} = \arg\min_{\theta} \left(-\sum_{i=1}^{n} \log p(x_i|\theta)\right)
\]
$$

### 1.3 장단점
- **장점**: 계산이 상대적으로 간단하고, 데이터에 기반한 직관적인 추정 방법이다.
- **단점**: 사전 정보(prior information)를 고려하지 않으며, 데이터가 적거나 노이즈가 많을 경우 민감하게 반응할 수 있다.

## 2. Maximum A Posteriori (MAP)

### 2.1 개요
- Maximum A Posteriori (MAP) 추정은 MLE와 유사하지만, 파라미터에 대한 사전 확률(prior)을 고려하여 더 현실적인 추정을 가능하게 합니다. 베이즈 정리를 사용하여 파라미터의 사후 확률을 최대화하는 방법

### 2.2 수학적 정의
- MAP는 다음과 같은 식으로 사후 확률을 최대화하는 파라미터 $\theta$를 찾는다.

$$
\[
\hat{\theta}_{MAP} = \arg\max_{\theta} \ p(\theta|\chi) = \arg\max_{\theta} \ \left[p(\chi|\theta) \cdot p(\theta)\right]
\]
$$

이를 로그 변환하여 표현하면,

$$
\[
\hat{\theta}_{MAP} = \arg\max_{\theta} \left[\log p(\theta) + \log p(\chi|\theta)\right]
\]
$$

### 2.3 장단점
- **장점**: 사전 지식을 반영할 수 있어, 데이터가 적거나 불확실할 때 더 안정적인 추정을 할 수 있다.
- **단점**: 사전 확률을 선택하는 것이 어려울 수 있으며, 잘못된 사전 확률은 잘못된 추정을 초래할 수 있다.

## 3. Bayesian Inference

### 3.1 개요
- Bayesian Inference는 관측된 데이터를 바탕으로 파라미터의 사후 확률 분포를 계산하는 방법이다. MLE와 MAP가 단일 추정치를 제공하는 반면, Bayesian Inference는 파라미터의 모든 가능한 값을 확률적으로 표현한다.

### 3.2 수학적 정의
- Bayesian Inference는 다음의 베이즈 정리를 기반으로 한다.

$$
\[
p(\theta|\chi) = \frac{p(\chi|\theta) \cdot p(\theta)}{p(\chi)}
\]
$$

여기서 $p(\theta|\chi)$는 사후 확률, $p(\chi|\theta)$는 우도, $p(\theta)$는 사전 확률, 그리고 $p(\chi)$는 evidence이다.

### 3.3 장단점
- **장점**: 불확실성을 포함한 파라미터 추정을 가능하게 하며, 새로운 데이터가 들어올 때마다 사후 확률을 업데이트할 수 있다.
- **단점**: 계산이 복잡하고, 특히 고차원 문제에서는 계산 비용이 매우 높을 수 있다.

## 4. MLE, MAP, 그리고 Bayesian Inference의 비교

| **특징** | **MLE** | **MAP** | **Bayesian Inference** |
|----------|---------|---------|------------------------|
| **사전 확률 고려** | 없음 | 있음 | 있음 |
| **파라미터 추정** | 단일 값 | 단일 값 | 확률 분포 |
| **복잡도** | 낮음 | 중간 | 높음 |
| **데이터 요구량** | 많음 | 적음 | 다양함 |
| **불확실성 표현** | 없음 | 제한적 | 있음 |


## 결론

- MLE, MAP, 그리고 Bayesian Inference는 각기 다른 상황에서 사용될 수 있는 강력한 도구들입니다. MLE는 간단하고 효율적인 방법이지만, 데이터가 부족하거나 노이즈가 많은 상황에서는 MAP나 Bayesian Inference가 더 나은 결과를 제공할 수 있다. 



## 참고 자료
- https://savanna.korea.ac.kr/wp/?page_id=1294


