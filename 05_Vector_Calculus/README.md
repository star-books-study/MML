# 5. Vector Calculus

- 머신러닝에서 많은 알고리즘들은 목적 함수(Objective Function)을 최적화한다.
- 목적함수는 모델이 데이터를 얼마나 잘 설명하는지 컨트롤하는 파라미터와 관련됨.
- 좋은 파라미터를 찾는 것을 **최적화 문제**로 표현할 수 있다.
- 이 장의 핵심은 **the concept of a function**
- 함수 $f$는 두 quantities를 서로 연관시키는 quantitity

<img width="561" alt="스크린샷 2024-07-15 오후 9 21 41" src="https://github.com/user-attachments/assets/27030125-5148-4155-8c2d-2e4cdbf4e643">

이는 함수 $f$를 $mathbb{R}^D$에서 $mathbb{R}$로의 mapping으로 취급한다는 것을 의미

#### Example 5.1

3.2장에서 살펴봤던 inner product의 special case인 dot product를 떠올려봅시다. Dot product를 위에서 언급한 함수의 notion으로 표현하면 
$f(x) = x^Tx$, $x\in\mathbb{R}^2$로 표현할 수 있음. 즉 다음과 같음.
<img width="562" alt="image" src="https://github.com/user-attachments/assets/bbb1af73-49b6-46a3-8925-bc90c85889b2">


## 5.1 Differentiation of Univariate Functions


### 5.1.1 Taylor Series
- Taylor Series : 함수 $f$를 어떤 항의 무한한 합으로 표현하는 것
  - 여기서 어떤 항은 $x_0$에서 계산된 $f$의 derivations에 의해 결정

#### Definition 5.3 Taylor Polynomial
$x_0$에서 $f : \mathbb{R} \rightarrow \mathbb{R}$의 n차 Taylor Polynomial은 다음과 같이 정의된다.

<img width="555" alt="스크린샷 2024-07-15 오후 9 25 52" src="https://github.com/user-attachments/assets/5e312095-4700-412d-9453-95c0d9ff7671">

위 식에서 $f^{(k)}(x_0)$는 $x_0$에서의 $f$의 k차 도함수이고, $\frac{f^{(k)}(x_0)}{k!}$은 다항식의 계수 (coefficients)이다.

#### Definition 5.4 Taylor Series


#### Example 5.3 Taylor Polynomial

#### Example 5.4 Taylor Series

### 5.1.2 Differentiation Rules

#### Example 5.5 Chain Rule




## 5.2 Partial Differentiation and Gradients

#### Definition 5.5 Partial Derivative

#### Example 5.6 Partial Derivatives Using the Chain Rule

#### Example 5.7 Gradient


### 5.2.1 Basic Rules of Partial Differentiation
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
