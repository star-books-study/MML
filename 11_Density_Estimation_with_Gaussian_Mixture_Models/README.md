# 11. Density Estimation with Gaussian Mixture Models

## 11.1 Gaussian Mixture Model
- Gaussian Mixture Model (GMM)은 이름 그대로 가우시안 분포 (정규분포)를 여러 개 혼합하여 데이터의 복잡한 분포를 근사하기 위한 머신러닝 알고리즘
- 이 모델은 머신러닝에서 주로 비지도학습(Unsupervised Learning)에서 클러스터링 목적으로 사용된다.
  > **클러스터링** : 비지도학습의 한 예시로, 어떠한 label 없이 데이터 내에서 거리가 가까운 것들끼리 각 군집들로 분류하는 기법
- **Gaussian Mixture Model**은 평균과 분산($\mu와 \sigma^2$)으로부터 군집의 특성을 알 수 있다.
  
  ![](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99237F395BEECA1507)


- Mixture Model (혼합 모형)은 데이터가 하나의 확률 분포가 아니라 여러개의 확률 분포를 이용해서 생성되었다고 가정한 모델을 말한다.
  - 즉, 데이터가 모수(population parameter)를 갖는 여러 개의 분포로부터 생성되었다고 가정하는 모델
    > 모수 : 모집단을 조사하여 얻을 수 있는 통계적인 특성치
  
- 이 중에서 가장 많이 사용되는 Gaussian Mixture Model(GMM)은 **데이터가 $K$개의 정규 분포로부터 생성되었다고 생성되었다고 보는 모델**

-  GMM은 데이터가 $K$개의 가우시안 분포(=정규 분포)로부터 생성되었다고 가정한다. 여기서 $K$는 몇 개의 가우시안 분포를 혼합할 것인지를 결정하는 GMM의 hyperparameter이다.
-  다음 그림은 $K=3$으로 설정된 GMM을 나타낸다.
![image](https://github.com/user-attachments/assets/bf83e814-fe6b-4255-ab79-ab1c909c68e2)

- GMM에서 주어진 데이터 $x$가 발생할 확률은 아래의 식과 같이 $K$개의 가우시안 확률 밀도 함수의 혼합으로 정의된다.
  <img width="587" alt="스크린샷 2024-08-15 오후 4 10 29" src="https://github.com/user-attachments/assets/798d45a1-62be-4b52-a30f-5789ecbf1fcf">

- $\pi_{k}$는 `mixing coefficient` 또는 `weight`라고 하며, 혼합 분포에 대한 확률밀도함수에서 $k$ 번째 가우시안 분포가 선택될 확률을 의미한다. 따라서 $\pi_{k}$는 반드시 11.2 조건을 만족해야 한다.
- GMM을 학습시킨다는 것은 주어진 데이터셋 $\chi =  \{ x_1, x_2, ..., x_N \}$에 대하여 데이터의 확률 $p(x)$를 최대화하는 파라미터 $\theta = \{ \pi_1, ... , \pi_{K}, \mu_{1}, ..., \mu_{K}, \sum_{1}, ... \sum_{K} \}$를 추정하는 것과 같다.

## 11.2 Parameter Learning via Maximum Likelihood
### 최대 우도 추정 (Maximum Likelihood Estimation, MLE) 기반의 GMM 학습
- 최대 우도 추정 (MLE)은 확률모델의 매개변수를 최적화하기 위해 머신러닝에서 가장 일반적으로 이용되는 방법 중 하나이다. MLE는 관찰된 데이터를 가장 잘 설명하는 모델의 파라미터를 찾는 방법으로, 주어진 데이터셋에 대해 likelihood를 최대화하는 파라미터를 찾는다.
- 각 데이터가 동일한 확률 분포에서 다른 데이터와 독립적으로 생성되었다고 가정하면, 주어진 데이터 N 개의 관측치가 있는 데이터 $\chi$에 대해서 likelihood를 아래와 같이 조건부 확률 형태로 나타낼 수 있다. likelihood를 계산할 때에는 독립변수가 서로 독립이라고 가정하기 때문에 다음과 같이 $\Pi$를 이용해서 수열의 곱셈으로 나타낼 수 있다.
<img width="673" alt="image" src="https://github.com/user-attachments/assets/d59e06c4-298d-490c-8218-198dd55ed93b">

- MLE는 11.9 식을 최대화하도록 모델을 학습시킨다.
- 그러나 곱셈이 있으면 미분이 힘들기 때문에 로그를 붙여서 log-likelihood를 사용한다. (로그를 적용하면 곱셈이 덧셈으로 변환)
- log-likelihood를 통해 다음과 같이 표현할 수 있다.
<img width="541" alt="image" src="https://github.com/user-attachments/assets/1f462a24-1366-4675-8b9a-cad1aabad9dd">

- 우리의 목적은 이 식을 최대화하는 파라미터 $\pi_k, \mu_k, \sum_k$를 찾는 것이다.
- 로그 우도 함수는 위로 볼록한 형태를 가지므로, 이 함수를 $\mu_k$, $\Sigma_k$, $\pi_k$에 대해 미분하고, 미분값이 0이 되는 점을 찾아 maximization 문제를 해결할 수 있다.
<img width="543" alt="image" src="https://github.com/user-attachments/assets/f55d40a5-e90d-46bc-a1e8-529df504a633">

## 11.3 EM Algorithm
- GMM에서의 모수는 두 가지 종류가 있다.
  1. 3가지 정규분포 중 확률적으로 어디에서 속해있는가를 나타내는 Weight 값
  2. 각각의 정규분포의 모수(평균, 분산)
- 첫 번째 종류의 모수를 잠재 변수라고 부르며, 잠재변수가 포함된 모델은 Mixture Model에서의 모수 추정은 MLE로 구할 수 없기 때문에 EM(Expectation Maximazation)이라고 부르는 알고리즘을 통해 iterative하게 구하게 된다.
- 왜냐하면 잠재변수가 포함되었기 때문에 likelihood function을 미분할 수가 없기 때문

// TODO : EM 알고리즘 정리
## 11.4 Latent-Variable Perspective

### 11.4.1 Generative Process and Probabilistic Model

### 11.4.2 Likelihood

### 11.4.3 Posterior Distribution

### 11.4.5 EM Algorithm Revisited

## 참고자료
- https://untitledtblog.tistory.com/133
- https://yeong-jin-data-blog.tistory.com/entry/GMM-Gaussian-Mixture-Models
- https://sanghyu.tistory.com/16
- https://3months.tistory.com/154 -> 모수 추정은 MLE로 구할 수 없어 EM을 사용 (EM 알고리즘 공부 시 다시 보기)
