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

- 다음은 Partial derivative의 기본적인 규칙에 대한 설명이다. 순서에 주의하여야 한다.
<img width="532" alt="스크린샷 2024-07-17 오전 9 59 20" src="https://github.com/user-attachments/assets/274c84c5-e874-403c-a6dd-461e20cc6564">

<img width="528" alt="스크린샷 2024-07-17 오전 10 07 35" src="https://github.com/user-attachments/assets/8be03197-4ee6-44c3-a23c-51a464b70a03">



### 5.2.2 Chain Rule
- Chain Rule에 대해서 알아보자.
- 여기서는 $x_1$과 $x_2$ 역시 $f$처럼 함수라고 한다.
- 이 때 $t$라는 하나의 input을 받아서 2개의 output이 탄생하였고, 이 둘을 $f$ 함수를 거쳐 하나의 output을 내게 되었다.
- 다시 말하면, $t$라는 input은 두 개의 함수를 만나 각각 $x_1(t), x_2(t)$ output을 발생시키고, 이게 다시 2개의 output으로 multi variative function인 $f$를 만나서 $f(x_1(t), x_2(t))$가 되어 최종적으로는 1개의 output이 된다는 말이다.
- 그래서 $f$에 대한 $t$를 미분하여 gradient를 얻는 것이다.
- output이 여러 개일 경우, gradient를 column vector로 나타내주고, 한 개일 경우 이전 처럼 row vector 형태로 나타내주면 된다.
> 계산 순서에 유의 하자.

<img width="572" alt="스크린샷 2024-07-17 오전 10 10 31" src="https://github.com/user-attachments/assets/edb002ee-87b1-450c-b87b-00320579723b">

- 아래 식 3개는 처음 input이 $t$로 하나였지만, 이번에는 $s$와 $t$로 두 개로 시작한다는 점이 다를 뿐이고 다른 건 다 같고, 일반화를 표현한 것이다.


<img width="562" alt="스크린샷 2024-07-17 오전 10 11 22" src="https://github.com/user-attachments/assets/f664f094-51bd-49ed-a58a-5284a65d5e21">

<img width="559" alt="스크린샷 2024-07-17 오전 10 11 35" src="https://github.com/user-attachments/assets/ac017049-0c70-4ae4-abef-61d0aad4e84d">


## 5.3 Gradients of Vector-Valued Functions
- 지금까지는 $\mathbb{R}^n$을 real value로 매핑하는 함수를 미분하였는데, 지금부터는 real value가 아닌 $\mathbb{R}^m$으로 매핑하는 함수를 미분한다.
- 즉, 미분 값이 **vector 형태로 나오는 함수를 미분**한다.

<img width="557" alt="스크린샷 2024-07-17 오전 10 13 04" src="https://github.com/user-attachments/assets/f66499d3-c787-4379-bd4c-0cccf85dfd2b">

- 이전과의 차이는 $f$가 총 $m$개 있어서 각각의 gradient 값을 뱉어낸다는 점이다.
- 아래는 맨 처음 partial derivative를 할 때 봤던 식인데, 이것을 함수의 $f$의 개수 만큼 열 벡터로 쭉 나열해준 것이다.

- 최종적으로 네모 칸이 의미하는 것은 **$m$개의 함수를 하나의 변수 $x_1$로 미분한 값이 되고, 행렬과 로우는 각 함수의 gradient 값이다.**


<img width="560" alt="스크린샷 2024-07-17 오전 10 14 46" src="https://github.com/user-attachments/assets/f938ea9e-275b-41c9-a287-3582a1881c28">


<img width="545" alt="스크린샷 2024-07-17 오전 10 14 58" src="https://github.com/user-attachments/assets/4deafe07-7aab-4310-945a-9c9052feea6f">

#### Definition 5.6 Jacobian
- row로 쭉 나열된 것이 함수의 output이 되고(gradient), col 방향으로 죽 나열된 것이 input이 된다.
- 이 matrix를 `Jacobian`이라고 한다.

<img width="561" alt="스크린샷 2024-07-17 오전 10 16 00" src="https://github.com/user-attachments/assets/44b52dd5-fbd6-47da-b6af-987c4b522a9c">

- linear mapping으로 transformation했을 때 얼마나 scailing 되는지를 나타낼 때, linear transformation일 때 가능한데 non linear transformation일 경우에는 어떤지 알려주는 게 `Jacobian`이고, 이 때 그 volume은 approximation이다.


<img width="547" alt="스크린샷 2024-07-17 오전 10 17 16" src="https://github.com/user-attachments/assets/f80305fd-0cf7-4f11-a441-f4ff2a3d2698">


- 위의 그림처럼 $f$를 통해 linear mapping을 한다고 해보자. $b$를 $[(1,0), (0,1)]$, $c$를 $[(-2,1), (1,1)]$이라고 하면, 쉽게 transformation matrix가 $[(-2,1), (1,1)]$이라는 것을 알 수 있고, 이를 식으로 나타내면 다음과 같다.

<img width="551" alt="스크린샷 2024-07-17 오전 10 18 49" src="https://github.com/user-attachments/assets/8fd4a078-9e1c-479f-9aba-ecdba0b7fec4">

- 그리고 이를 partial derivative하게 되면 Jacobian을 구할 수 있게 된다.
- 이에 determinant를 구하게 되면 3을 얻게 된다.

<img width="559" alt="스크린샷 2024-07-17 오전 10 19 58" src="https://github.com/user-attachments/assets/0028dea3-49b9-4cb1-8d53-2e90e4883f2a">


## 5.4 Gradients of Matrices

- 행렬이 주어졌을 때 행렬을 벡터로 미분한 gradient 혹은 행렬을 다른 행렬로 미분한 gradient들은 multidemensional tensor로 계산이된다.
- 이 gradient를 어떻게 구하는지 알아보자.
- multidemensional tensor이기 때문에 output의 dimension과 크기만 신경 쓰면 지금까지 배운 미분 개념에서 크게 벗어나지 않는다.
- 예를 들어 행렬 $A (m x n)$이 행렬 $B(pxq)$로 미분되면 4 dimensional tensor $J$가 되고, $J_{ijkl}$ 엔트리에는 각각 paritla derivatives 값이 들어간다.
- 행렬을 벡터 또는 행렬로 미분했을 때 **output의 shape**를 잘 상기해야 한다.

- A라는 행렬을 $x$ 벡터로 미분했을 때, 최종적으로는 4x2x3의 결과가 되는데, 이 때 각 셀에는 $A$와 $x$의 1 demension 곱으로 표현된다.
- 그림을 통해서는 $A$를 각각 $x_1, x_2, x_3$으로 미분한 partial deriatives들이 있고, 최종적으로 4x2x3 결과가 되는 개념만 파악하자.

<img width="334" alt="스크린샷 2024-07-17 오전 10 25 27" src="https://github.com/user-attachments/assets/8b23a6ac-467e-4712-be24-50d13dfb9bd0">

#### Example 5.12 Gradient of Vectors with Respect to Matrices
- 위 그림을 예제 5.12로 보면, $M$ 차원의 $f$를 $A$ 행렬로 미분하면 5.86과 같이 $M x (M x N)$의 결과를 얻는다.
- 5.87)은 partial derivatives의 벡터들을 모아 gradient를 이루게 된다. (5.88)식은 $A$의 하나의 element에 대해서 어떻게 표현되는지 보여준다. 행렬 $A$
의 element들과 $j$번째 $x$벡터와의 곱으로 표현된다. 특정 $f_i$를 $A_{iq}$로 미분하여 $x_q$라 하고 이는 하나의 행벡터로 partial derivatives가 된다.

<img width="575" alt="스크린샷 2024-07-17 오전 10 28 00" src="https://github.com/user-attachments/assets/1385726c-0078-4f68-92d1-899ac9fb2be7">

<img width="578" alt="스크린샷 2024-07-17 오전 10 28 09" src="https://github.com/user-attachments/assets/53d80b82-42dc-49d3-9394-8f390d6b0d48">

#### Example 5.13 Gradient of Matrices with Respect to Matrices
- 이번에는 행렬을 행렬로 미분하는 예제를 살펴보자. 
- output의 shape 부터 살펴보면 $(N x N) x (M x N)$ 의 4 dimension tensor라는 것을 알 수 있다. $K$의 각 element들은 $r$의 내적으로 표현된다.
<img width="412" alt="스크린샷 2024-07-17 오전 10 28 54" src="https://github.com/user-attachments/assets/7300d75a-356e-4fa9-91a0-3db44a2f3ad1">

<img width="409" alt="스크린샷 2024-07-17 오전 10 29 00" src="https://github.com/user-attachments/assets/3c99a58b-bd17-4899-8505-1d9d7c54292b">

## 참고자료
- https://www.youtube.com/watch?v=MDL384gsAk0
- https://data-science-hi.tistory.com/112
- https://data-science-hi.tistory.com/113
