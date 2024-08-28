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

### EM 알고리즘
- EM 알고리즘은 Latent 변수를 도입하여 최대 우도 추정량을 구하는 방법
  - Latent 변수 : 실제로 관측이 되지 않았지만 관측된 데이터에 상호 영향을 미치리라 판단되는 변수
- EM 알고리즘을 정의하기 위해 필요한 재료는 실제로 관측된 데이터 $\chi$, Latent 변수 데이터 $Z$ 그리고 최대 우도 추정법으로 추정해야 할 파라미터 $\theta$
- EM 알고리즘은 $\theta$를 수학적인 테크닉을 통해 한방에 구하는 알고리즘이 아니다. 주어진 $\theta$를 이용하여 업데이트 해나가야 하는 Iterative 알고리즘
- 따라서 EM 알고리즘을 정의하는 데 $\theta$의 현재 추정값 $\theta^*$이 추가적으로 필요하다.

- 보통 최대 우도 추정량을 구하기 위해 다음과 같은 로그 우도 함수를 생각한다.
  <img width="578" alt="스크린샷 2024-08-28 오후 7 31 39" src="https://github.com/user-attachments/assets/fbed76ae-1cc6-47cd-ad9d-8be1864d8ac8">

- 여기서 $x$는 $\theta$의 관측값, $f_{\theta}(x)$는 $\chi$의 확률 밀도 함수다.
- 이 때 로그 우도 함수를 최대화하는 $\theta$를 찾는 것이 최대 우도 추정법이다.
- 그런데 여기에 Latent 변수 $Z$를 도입한다고 하였다. 근데 $Z$는 관측된 것이 아니므로 로그 우도 함수에 직접적으로 끼워줄 수가 없다. 따라서 다음의 식을 이용한다.
  <img width="554" alt="스크린샷 2024-08-28 오후 7 33 51" src="https://github.com/user-attachments/assets/8a530a5e-4df7-4f7a-b2d6-b8f53baa82a9">
- 위 식 양변에 로그를 취해주자
  <img width="596" alt="스크린샷 2024-08-28 오후 7 34 19" src="https://github.com/user-attachments/assets/d0e05a5b-159f-466e-9eff-f2c87b1f1076">
- 그리고 파라미터 추정값 $\theta$에 의존하는 $Z$의 조건부 확률 밀도 함수 $f_{Z|X,\theta*}(z)$를 양변에 곱한 다음 $z$에 대해 적분을 취해주자.
  
<img width="734" alt="스크린샷 2024-08-28 오후 7 35 16" src="https://github.com/user-attachments/assets/5b36350e-6645-4a62-987f-4091ad0bf94f">

- 이 등식은 $l(\theta ; x)$가 $z$와 관계 없고 함수의 적분 값은 1이기 때문에 성립한다.
- 이제 이 식을 통하여 $l(\theta ; x)$를 최대화하는 것은 $Q(\theta|\theta^*) + H(\theta|\theta^*)$화하는 문제와 같아진다.
- 이 때 EM 알고리즘은 $\theta^*$가 주어진 상황에서 $Q(\theta|\theta^*)$를 최대화하는 $\theta$를 찾는다.
  - 왜냐하면 $Q$를 최대화하는 것이 $l(\theta ; x)$을 최대화하는 것보다 일반적으로 쉽기 때문이다.
- Q를 최대화 하는 $\theta$는 $l(\theta ; x)$를 최대화 하는 $\theta$와 같지는 않다. 그렇다면 EM 알고리즘을 왜 사용하는가?
- 왜냐하면 $l(\theta ; x)$를 최대화하는 $\theta$를 찾는데 도움이 되기 때문이다.
- 위 식에서 $\theta$ 대신 $\theta^*$을 넣으면 다음과 같이 된다.
<img width="556" alt="스크린샷 2024-08-28 오후 7 52 57" src="https://github.com/user-attachments/assets/86f8e588-993e-41b5-a69c-8d9bed833282">
- 이제 처음 식에서 이 식을 빼준다.
  <img width="652" alt="스크린샷 2024-08-28 오후 7 53 18" src="https://github.com/user-attachments/assets/8f8504f9-c458-467a-ad1a-b0fd3cb329f6">
- 여기서 $H(\theta|\theta^*)$을 살펴보자.
  <img width="796" alt="스크린샷 2024-08-28 오후 7 53 53" src="https://github.com/user-attachments/assets/c2fe3c4a-fe58-49c9-a468-cad1eda844c3">

### EM 알고리즘 정의
1. 파라미터 초기값 $\theta^{(0)}$을 설정한다.
2. $\theta^{(0)}$에 대하여 다음을 계산한다.
   <img width="619" alt="image" src="https://github.com/user-attachments/assets/870988d0-0e54-434c-99df-a449c670fe23">
   - 이 단계는 조건부 기대값을 구하는 과정이라 볼 수 있어 Expectation Step이라고 한다.
3. $Q(\theta | \theta^{(t)})$을 최대화하는  $\theta^{(t+1)}$을 찾는다. 즉,
   <img width="548" alt="스크린샷 2024-08-28 오후 7 57 20" src="https://github.com/user-attachments/assets/5bba49e2-46e6-423d-95a1-aceac0710eef">
  - 이 단계는 $Q$를 최대화한다는 의미에서 Maximization Step이라고 한다.
4. 수렴할 때까지 단계 2 ~ 단계 3을 반복한다.

- E 단계에서는 결국에는 Q를 지정해서 부등식을 등식으로 하여 Lower bound를 tight 하게 만들고, M-step에서는 다시 금 해당 로그 가능도의 Θ를 바탕으로 최대화 시켜서 새로운 공간으로 이동시키는 것이다. 이걸 수렴할 때 까지 반복한다. 

## 참고자료
- https://untitledtblog.tistory.com/133
- https://yeong-jin-data-blog.tistory.com/entry/GMM-Gaussian-Mixture-Models
- https://sanghyu.tistory.com/16
- https://3months.tistory.com/154
- https://zephyrus1111.tistory.com/89
- https://m.blog.naver.com/sw4r/221428818089
