# 5. Vector Calculus (벡터 미적분학)

- 머신러닝 알고리즘을 접하다 보면 자연스레 최적의 parameter 값을 찾는 문제에 직면하게 된다. 이렇게 최적의 값을 찾아가는 과정을 learning이라고 한다. 이 과정에서 필요한 정보가 gradient다.
- 이 gradient는 **미분**을 통해 쉽게 얻을 수 있다. 벡터, 행렬의 미분으로 가면 복잡해지지만 다항식에 대한 미분은 어렵지 않게 구할 수 있다.


## 5.1 Differentiation of Univariate Functions (일변수 함수의 미분)
- 이번 장에서는 머신러닝에서 미지수가 하나인 univariate function에 대한 내용을 알아본다.

> 다항식은, 변수의 개수에 따라, 일변수(univariate), 이변수(bivariate), 다변수(multivariate) 등으로 구분된다.


### 5.1.1 Taylor Series (테일러 급수)
- 테일러 급수(Taylor's series)를 이용하면, 복잡하거나 우리가 잘 모르는 함수를 다항함수(polynomial function)로 대체 할 수 있다.

- 어떤 함수에 대해서 $x = x_0$에 대해 계속적으로 미분 가능한 경우, $x=x_0$의 근처에서 아래의 관계식의 좌변과 우변이 근사하게 된다.
  
  <img width="555" alt="스크린샷 2024-07-15 오후 9 25 52" src="https://github.com/user-attachments/assets/5e312095-4700-412d-9453-95c0d9ff7671">

- 테일러 급수에서 주의해야 할 사항은 좌변과 우변이 모든 $x$에 대해서 같은 것이 아니라, **$x = x_0$ 근처에서만 성립**한다는 점
- 즉, $x$가 $x_0$에서 멀어지면 멀어질수록 $f(x) = T_n(x)$로 놓는 것은 큰 오차를 갖게 된다.

  ➡️ 결국 $x=x_0$에서 $f$와 동일한 미분계수를 갖는 어떤 다항함수로 $f$를 근사시키는 것
- 테일러 급수를 이용해 이와 같이 $x=x_0$에서 미분 계수를 일치시키면 $x=x_0$ 뿐만 아니라 주변의 일정 구간에서도 $f(x)$와 $T_\infty(x)$가 거의 일치되게 된다.

#### Definition 5.3 Taylor Polynomial (테일러 다항식)
- f가 n번까지 미분 가능한 함수라고 하자. 이 때 정수 n이 0에서 n까지의 임의의 정수라고 할 때, $x=x_0$에서 $f$에 의해 발생하는 n차 테일러 다항식은 아래와 같이 정의할 수 있다.
  
 <img width="511" alt="스크린샷 2024-07-17 오후 2 28 16" src="https://github.com/user-attachments/assets/87347e75-a1ac-4aa6-8ac2-35b2a744caff">


- 위 식에서 $f^{(k)}(x_0)$는 $x_0$에서의 $f$의 k번째 미분 계수이고, $\frac{f^{(k)}(x_0)}{k!}$은 다항식의 계수 (coefficients)이다.
- 다항식의 차수(n)이 커지면 커질수록 테일러 급수에 가까워진다.

#### Example 5.3 Taylor Polynomial
- 다음 예제는 6번의 미분을 통해 원래 $f(x)$와 같아짐을 보게 된다.


<img width="579" alt="스크린샷 2024-07-17 오전 9 46 47" src="https://github.com/user-attachments/assets/a26f927b-0c0a-4e7b-a375-5fca7c988386">

- $f(x) = sin(x) + cos(x) \in C^{\infty}, x_0$에서의 테일러 급수

  <img width="341" alt="스크린샷 2024-07-17 오전 9 47 04" src="https://github.com/user-attachments/assets/29e7cb5e-bf41-4643-9662-b1c6d1c9931e">


  - $k$번의 미분으로 얻은 polynomial을 approximation하는 그래프들은 **차수를 높일수록** 특정 x에 대하여 설명을 잘하게 된다. 

### 5.1.2 Differentiation Rules (미분법)

- 다음은 기본적인 미분 공식이다.

<img width="552" alt="스크린샷 2024-07-17 오전 9 49 28" src="https://github.com/user-attachments/assets/afc4bf89-8b1f-4228-ba54-4f81fa00de5d">

#### Example 5.5 Chain Rule

- 다음은 간단한 Chain Rule을 푸는 에제이다.
<img width="576" alt="스크린샷 2024-07-17 오전 9 49 55" src="https://github.com/user-attachments/assets/e669922e-07f0-4268-8253-9f5d1ffe5f02">

- $h(x)$를 $f(x)$와 $g(x)$로 표현하여 전개하고 있다.

<img width="573" alt="스크린샷 2024-07-17 오전 9 51 33" src="https://github.com/user-attachments/assets/375e2776-4943-42d3-9c7b-1830db0d6bdb">


## 5.2 Partial Differentiation and Gradients (편미분과 기울기)

- 이제는  multivariate variable를 대상으로 미분을 한다.
- 수학에서, 여러 변수에 대한 함수의 편미분이라는 것은 여러 변수들 중 하나에 대해서 미분하고, 나머지는 상수로 취급하는 것을 의미한다.
- 여기서 gradient를 구하는 방법은 여러 개의 variable 중 하나씩에 대한 미분을 진행하고 모두 모아주면 된다.
- 이 모아진 것을 gradient라고 한다.
- 그리고 특정 변수에 대한 gradient를 partial derivative(편미분)라고 한다.

#### Definition 5.5 Partial Derivative
- 하나씩 변수에 대한 미분을 진행하고, 이들을 모아놓은 것이 $(5.40)$이 된다. 이를 $f$의 gradient라고 한다.
<img width="572" alt="스크린샷 2024-07-17 오전 9 54 42" src="https://github.com/user-attachments/assets/7b40bcbc-8b80-4c2b-ae16-b55d332303ba">



- 선형대수를 포함한 대부분의 vector은 column vector로 표현하는 반면, gradient vector은 row vector로 사용하는 것이 학술적 약속이다.


#### Example 5.7 Gradient
- 이번에는 multivariate variable의 gradient를 구해보자.
- 여기에서도 마찬가지로 partial derivative를 구하고, 이들을 모은 로우 벡터 형태로 만들어주면 된다.

  
<img width="575" alt="스크린샷 2024-07-17 오전 9 57 59" src="https://github.com/user-attachments/assets/57bc9898-2972-4463-97f0-7bcc9300736f">



### 5.2.1 Basic Rules of Partial Differentiation (편미분의 기본 규칙)

- 다음은 Partial derivative의 기본적인 규칙에 대한 설명이다. 순서에 주의하여야 한다.
<img width="532" alt="스크린샷 2024-07-17 오전 9 59 20" src="https://github.com/user-attachments/assets/274c84c5-e874-403c-a6dd-461e20cc6564">

<img width="528" alt="스크린샷 2024-07-17 오전 10 07 35" src="https://github.com/user-attachments/assets/8be03197-4ee6-44c3-a23c-51a464b70a03">




### 5.2.2 Chain Rule (연쇄 법칙)
- 변수가 $x_1$과 $x_2$에 대한 함수 $f$를 생각해보자. 또한 $x_1(t), x_2(t)$는 t에 대한 함수이다.
- $f$의 $t$에 대한 gradient를 구하는 일반식은 다음과 같다.

<img width="523" alt="image" src="https://github.com/user-attachments/assets/59f4fc57-6cdc-44e2-9834-80336a14dea8">

- 만일 $f$가 $x_1$, $x_2$에 대한 함수이고, $x_1(s,t)$, $x_2(s,t)$가 두 변수 $s$, $t$에 대한 함수라면, 연쇄 법칙은 다음과 같은 편미분 결과를 낸다.

<img width="515" alt="image" src="https://github.com/user-attachments/assets/e9d5589c-58af-4d10-8b9e-b208c9e11ec2">


- 그리고 gradient는 행렬곱을 통해 얻어지게 된다.
<img width="446" alt="image" src="https://github.com/user-attachments/assets/ee8be93f-f030-4b36-a8c1-b59c880e5c72">

- 위에서 색으로 구분한 것과 같이, gradient를 vector 및 matrix 형태로 표현할 때는, 항상 row 방향으로 적어야 한다.


## 5.3 Gradients of Vector-Valued Functions (벡터 함수의 기울기)
- 이전까지 다룬 함수를 n차원에서 1차원으로 mapping 되는 것이었다면,
  
  $$f : \mathbb{R}^n \rightarrow \mathbb{R}$$

- 이 장에서 다룰 함수는 n차원에서 m차원으로, 즉 더 일반적인 경우에 대한 mapping을 다룬다. (이 때 n >= 1, m > 1을 만족한다.)


  $$f : \mathbb{R}^n \rightarrow \mathbb{R}^m$$

- n차원에서 m차원으로 mapping 되는 이 function values의 vector는 아래와 같다. input이 모두 vector 임을 확인할 수 있다.
  
  <img width="450" alt="스크린샷 2024-07-17 오후 4 46 18" src="https://github.com/user-attachments/assets/86d2eb3c-77ab-4a23-b378-6e226d591c60">

- n에서 m차원으로 mapping 되는 위 vector-valued function의 partial derivative를 구하면 아래와 같다.
  
  <img width="452" alt="image" src="https://github.com/user-attachments/assets/212d0d8d-c7d4-440c-9c89-54a80e44eb9f">

  - partial deriviatives의 row vector 형태가 우리가 구하려는 각 f의 gradient이고,
  - 모든 partial derivatives는 column vector로 이루어져 있다.

- 즉, 다음과 같이, partial derivatives를 row 방향으로 결합한 형태로 vector-valued function의 gradient를 구할 수 있다.

- 그리고 아래와 같이 $m\times n$ 형태로 주어진 matrix를 `Jacobian`이라 한다.
  
  <img width="489" alt="스크린샷 2024-07-17 오후 4 51 31" src="https://github.com/user-attachments/assets/e4a1728b-019d-425d-821b-f427d280a279">

#### Definition 5.6 Jacobian
- 앞서 언급했듯이, $\mathbb{R}^n$에서 $\mathbb{R}^m$에 mapping되는 벡터 함수의 모든 partial derivative의 모음을 `Jacobian`이라고 하고, 다음과 같이 나타낸다.

<img width="495" alt="스크린샷 2024-07-17 오후 4 59 24" src="https://github.com/user-attachments/assets/33d26cfa-bba0-468c-9f71-1223b5fd87c6">

- 이 때 input인 x는 다음과 같은 n 차원의 column vector 형태를 띄며, 주어진 Jacobian은 "i 번째 output의 변화량 / j 번째 input의 변화량"을 의미한다.

<img width="488" alt="image" src="https://github.com/user-attachments/assets/b1ea9d9b-1820-4524-8106-6c7df1a41af3">




## 5.4 Gradients of Matrices (행렬의 기울기)

- multidemensional tensor이기 때문에 output의 dimension과 크기만 신경 쓰면 지금까지 배운 미분 개념에서 크게 벗어나지 않는다.
- 예를 들어 행렬 $A (m \times n)$이 행렬 $B(p \times q)$로 미분되면 4 dimensional tensor $J$가 되고, $J_{ijkl}$ 엔트리에는 각각 paritial derivatives 값이 들어간다.
- 행렬을 벡터 또는 행렬로 미분했을 때 **output의 shape**를 잘 상기해야 한다.


<img width="530" alt="스크린샷 2024-07-17 오후 8 42 54" src="https://github.com/user-attachments/assets/ed930bae-b579-4689-acd2-173f68f0e776">

- 이를 편미분 하면 다음과 같다.

<img width="522" alt="image" src="https://github.com/user-attachments/assets/03d5d996-f79c-41a9-987a-d29a214471ae">

- 이를 모아보면 다음과 같은 자코비안을 만들 수 있다.

<img width="528" alt="스크린샷 2024-07-17 오후 8 43 55" src="https://github.com/user-attachments/assets/ec0bd4ab-a823-458b-8c16-9dffad3feaa3">


- $A \in \mathbb{R}^{4\times2}$ 행렬을 $x \in \mathbb{R}^3$ 벡터로 미분했을 때, 최종적으로는 4x2x3의 결과가 되는데, 이 때 각 셀에는 $A$와 $x$의 1 demension 곱으로 표현된다.
- 그림을 통해서는 $A$를 각각 $x_1, x_2, x_3$으로 미분한 partial deriatives들이 있고, 최종적으로 4x2x3 결과가 되는 개념만 파악하자.

<img width="334" alt="스크린샷 2024-07-17 오전 10 25 27" src="https://github.com/user-attachments/assets/8b23a6ac-467e-4712-be24-50d13dfb9bd0">

## 5.5 Useful Identities for Computing Gradients
- 자주 사용되는 유용한 gradient

<img width="549" alt="스크린샷 2024-07-19 오전 12 28 15" src="https://github.com/user-attachments/assets/efbae57f-da9f-44ec-8733-c26356720eb2">

## 5.6 Backpropagation and Automatic Differentiation
- 많은 머신러닝 애플리케이션에서 gradient descent를 수행함으로써 좋은 모델 파라미터를 얻는다.

### 5.6.1 Gradients in a Deep Network
- chain rule이 많이 사용되는 분야는 딥러닝
- function value $y$가 다양한 레벨의 function composition에서 계산된다.

<img width="557" alt="스크린샷 2024-07-19 오전 12 32 06" src="https://github.com/user-attachments/assets/4f2edf8f-8a19-496a-b2d1-b34076199513">

- 
## 참고자료
- https://www.youtube.com/watch?v=MDL384gsAk0
- https://data-science-hi.tistory.com/112
- https://data-science-hi.tistory.com/113
- https://darkpgmr.tistory.com/59
- https://jangpiano-science.tistory.com/123
- https://stevenkim1217.tistory.com/entry/MML-4-Vector-Calculus-4-Gradient-for-Vector-Valued-FunctionJacobian
