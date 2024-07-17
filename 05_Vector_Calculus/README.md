# 5. Vector Calculus (벡터 미적분학)

- 머신러닝 알고리즘을 접하다 보면 자연스레 최적의 parameter 값을 찾는 문제에 직면하게 된다. 이렇게 최적의 값을 찾아가는 과정을 learning이라고 한다. 이 과정에서 필요한 정보가 gradient다.
- 이 gradient는 **미분**을 통해 쉽게 얻을 수 있다. 벡터, 행렬의 미분으로 가면 복잡해 지지만 다항식에 대한 미분은 어렵지 않게 구할 수 있다.


<img width="548" alt="스크린샷 2024-07-17 오전 9 24 39" src="https://github.com/user-attachments/assets/99752a23-cda0-44f6-bd11-172ec8449e7f">

- (a)와 같은 경우는 + 모양의 관측치를 잘 설명해줄 수 있는 최적의 그래프를 구해주어야 한다. 이러한 함수를 `likelyhood`라는 함수로 정의하고, 이를 최대화하는 과정을 겪어서 파란색 선과 같은 최적의 curve를 가지게 된다.
- (b)와 같은 경우는 여러 개의 가우시안 혼합 모형으로 밀도를 추정하게 되는데, 여기서도 얼마나 데이터를 잘 설명하는가를 측정할 수 있는 `likelyhood`를 정의하고 이를 최대화하는 mean과 covariance를 측정하게 된다.


- 이러한 최적화 과정에서 목적함수의 gradient를 찾아 나서야 한다.

## 5.1 Differentiation of Univariate Functions (일변수 함수의 미분)
- 이번 장에서는 머신러닝에서 미지수가 하나인 univariate function에 대한 내용을 알아본다.

- 아래의 이미지를 통해서 x가 변화할 때 y의 변화랑은 아래의 식과 같이 나타난다.
  
  <img width="289" alt="스크린샷 2024-07-17 오전 9 35 40" src="https://github.com/user-attachments/assets/a8d53d2a-3540-483a-a5c7-c3f1ce71c1c0">
  
<img width="541" alt="스크린샷 2024-07-17 오전 9 36 14" src="https://github.com/user-attachments/assets/3181b934-8d14-4cb9-9a2d-e448c4316337">


- polynomial에 대한 미분을 하는 과정은 다음과 같다.
  
  <img width="563" alt="스크린샷 2024-07-17 오전 9 38 45" src="https://github.com/user-attachments/assets/bfed06ad-39ff-4ec8-978a-e4f4e6bf73ec">


### 5.1.1 Taylor Series

- Taylor Series : 함수 $f$를 어떤 항의 무한한 합으로 표현하는 것
  - 여기서 어떤 항은 $x_0$에서 계산된 $f$의 derivations에 의해 결정

#### Definition 5.3 Taylor Polynomial

<img width="555" alt="스크린샷 2024-07-15 오후 9 25 52" src="https://github.com/user-attachments/assets/5e312095-4700-412d-9453-95c0d9ff7671">

- 위 식에서 $f^{(k)}(x_0)$는 $x_0$에서의 $f$의 k차 도함수이고, $\frac{f^{(k)}(x_0)}{k!}$은 다항식의 계수 (coefficients)이다.

- $k$번의 미분으로 얻은 polynomial을 approximation하는 그래프들은 **차수를 높일수록** 특정 x에 대하여 설명을 잘하게 된다. 여기서 $x = 1$일 때는 기준으로 구한 것이기 때문에 그 주변에 대해서 approximation하게 이루어진다.

#### Example 5.3 Taylor Polynomial
- 다음 예제는 6번의 미분을 통해 원래 $f(x)$와 같아짐을 보게 된다.

<img width="341" alt="스크린샷 2024-07-17 오전 9 47 04" src="https://github.com/user-attachments/assets/29e7cb5e-bf41-4643-9662-b1c6d1c9931e">


<img width="579" alt="스크린샷 2024-07-17 오전 9 46 47" src="https://github.com/user-attachments/assets/a26f927b-0c0a-4e7b-a375-5fca7c988386">

### 5.1.2 Differentiation Rules

- 다음은 기본적인 미분 공식이다.

<img width="552" alt="스크린샷 2024-07-17 오전 9 49 28" src="https://github.com/user-attachments/assets/afc4bf89-8b1f-4228-ba54-4f81fa00de5d">

#### Example 5.5 Chain Rule

- 다음은 간단한 Chain Rule을 푸는 에제이다.
<img width="576" alt="스크린샷 2024-07-17 오전 9 49 55" src="https://github.com/user-attachments/assets/e669922e-07f0-4268-8253-9f5d1ffe5f02">

- $h(x)$를 $f(x)$와 $g(x)$로 표현하여 전개하고 있다.

<img width="573" alt="스크린샷 2024-07-17 오전 9 51 33" src="https://github.com/user-attachments/assets/375e2776-4943-42d3-9c7b-1830db0d6bdb">


## 5.2 Partial Differentiation and Gradients (편미분과 기울기)

- 이제는 mutivariate variable $x \in \mathbb{R}^n$에 대한 미분을 한다.
- 여기서 gradient를 구하는 방법은 여러 개의 variable 중 하나씩에 대한 미분을 진행하고 모두 모아주면 된다.
- 이 모아진 것을 gradient라고 한다.
- 그리고 특정 변수에 대한 gradient를 partial derivative라고 한다.

#### Definition 5.5 Partial Derivative
- 하나씩 변수에 대한 미분을 진행하고, 이들을 모아놓은 것이 5.40이 된다. 이를 $f$의 gradient라고 한다.
<img width="572" alt="스크린샷 2024-07-17 오전 9 54 42" src="https://github.com/user-attachments/assets/7b40bcbc-8b80-4c2b-ae16-b55d332303ba">


#### Example 5.6 Partial Derivatives Using the Chain Rule
- 각각 $x,y$ multivariate variable에 대한 Partial Derivatives를 구한 것이다.
  
<img width="577" alt="스크린샷 2024-07-17 오전 9 55 27" src="https://github.com/user-attachments/assets/bc503967-db1c-4d07-9027-e3dd7cafc3cb">


<img width="577" alt="스크린샷 2024-07-17 오전 9 55 55" src="https://github.com/user-attachments/assets/a5f312db-a476-4e65-b8dd-ad3922d6f8a6">


#### Example 5.7 Gradient
- 이번에는 multivariate variable의 gradient를 구해보자.
- 여기에서도 마찬가지로 partial derivative를 구하고, 이들을 모은 로우 벡터 형태로 만들어주면 된다.

  
<img width="575" alt="스크린샷 2024-07-17 오전 9 57 59" src="https://github.com/user-attachments/assets/57bc9898-2972-4463-97f0-7bcc9300736f">



### 5.2.1 Basic Rules of Partial Differentiation (편미분의 기본 규칙)
<img width="532" alt="스크린샷 2024-07-17 오전 9 59 20" src="https://github.com/user-attachments/assets/274c84c5-e874-403c-a6dd-461e20cc6564">

<img width="558" alt="스크린샷 2024-07-17 오전 9 59 31" src="https://github.com/user-attachments/assets/0bb2a155-dad9-4374-9277-5f79f91e785c">

- 

### 5.2.2 Chain Rule

#### Example 5.8




## 5.3 Gradients of Vector-Valued Functions

#### Definition 5.6 Jacobian

#### Example 5.9 Gradient of a Vector-Valued Function
#### Example 5.10 Chain Rule
#### Example 5.11 Gradient of a Least-Squares Loss in a Linear Model




## 5.4 Gradients of Matrices

#### Example 5.12 Gradient of Vectors with Respect to Matrices

#### Example 5.13 Gradient of Matrices with Respect to Matrices

## 참고자료
- https://www.youtube.com/watch?v=MDL384gsAk0
- https://data-science-hi.tistory.com/112
