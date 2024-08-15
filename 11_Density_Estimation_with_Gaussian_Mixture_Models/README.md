# 11. Density Estimation with Gaussian Mixture Models

## 11.1 Gaussian Mixture Model
- Gaussian Mixture Model (GMM)은 이름 그대로 가우시안 분포 (정규분포)를 여러 개 혼합하여 데이터의 복잡한 분포를 근사하기 위한 머신러닝 알고리즘
-  GMM은 그림 1과 같이 $K$개의 가우시안 분포를 혼합하여 복잡한 형태의 확률분포를 근사한다. 
는 몇 개의 가우시안 분포를 혼합할 것인지를 결정하는 GMM의 hyperparameter이며, 그림 1은 
으로 설정된 GMM을 나타낸다
![image](https://github.com/user-attachments/assets/bf83e814-fe6b-4255-ab79-ab1c909c68e2)

- GMM에서 주어진 데이터 $x$가 발생할 확률은 아래의 식 (1)과 같이 $K$개의 가우시안 확률 밀도 함수의 혼합으로 정의된다.
<img width="587" alt="스크린샷 2024-08-15 오후 4 10 29" src="https://github.com/user-attachments/assets/798d45a1-62be-4b52-a30f-5789ecbf1fcf">

## 11.2 Parameter Learning via Maximum Likelihood

### 11.2.1 Responsibilities

### 11.2.2 Updating the Means

### 11.2.3 Updating the Covariances

### 11.2.4 Updating the Mixture Weights


## 참고자료
- https://untitledtblog.tistory.com/133
