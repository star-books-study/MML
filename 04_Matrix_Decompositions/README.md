# 4. Matrix Decompositions

- 지금까지는 유한한 차원 벡터에 대한 내적(inner product)에 대해서 알아보았다. 이번 챕터에서는 함수(function)에 대한 inner product에 대해 알아본다.

## 4.1 Determinant and Trace

### Determinant
- `Determinant`(행렬식)는 선형대수에서 중요한 개념
- Determinant는 선형대수에서의 a methematical object in the analysis and solution of systems
- Determinant는 오직 같은 수의 행과 열이 있는 정방행렬(square matrix, $A \in \mathbb{R}^2$)에서만 정의된다.
- square matrix $A$의 determinant는 A를 실수(real number)로 mapping하는 함수이고, 아래와 같이 표현한다.

<img width="289" alt="스크린샷 2024-07-10 오후 3 28 27" src="https://github.com/star-books-coffee/MML/assets/101961939/a523a88b-6c00-47d7-83cc-36412235528e">

### Matrix Invertibility
- $A \in \mathbb{R}^2$의 역행렬은 아래의 식으로 도출할 수 있다.
  <img width="326" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/9195872f-f536-499c-8548-92994c20acd4">
- $A$가 가역(invertible)하려면 $a_{11}a_{22} - a_{12}a_{21} \neq 0$의 조건이 충족되어야 한다.
- 이를 충족하는 matrix $A$의 determinant는 아래와 같이 정의된다.
  <img width="314" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/dc8cf0d2-c510-4372-ac52-3dc5734df98a">
#### Theroem 4.1
- 어떤 정방행렬이라도 $det(A) \neq 0$이라면 역행렬을 가진다.
   <img width="326" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/9195872f-f536-499c-8548-92994c20acd4">
  - n = 1
    
    <img width="205" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/3c343100-fc5a-4dbe-9f68-afbcec09af0c">

  - n = 2
    
    <img width="317" alt="스크린샷 2024-07-10 오후 3 54 24" src="https://github.com/star-books-coffee/MML/assets/101961939/bfa6b8a1-035d-4da7-8b95-3549f05e56e9">
  - n = 3 (Sarrus' rule)
    
    <img width="428" alt="스크린샷 2024-07-10 오후 3 55 20" src="https://github.com/star-books-coffee/MML/assets/101961939/17c5e155-91d7-4210-907f-bf0f21c7d17c">
  
    
### Triangular Matrix
- 정방행렬 $T \in R^{nxn}$의
  - i > j에 대해 $T_{ij} = 0 $이라면 이는 upper triangular matrix
  - i < j에 대해 $T_{ij} = 0 $이라면 이는 lower triangular matrix

![](https://media.geeksforgeeks.org/wp-content/uploads/20221207110618/tma.jpg)
- 정방행렬 $T \in R^{nxn}$의 determinant는 대각 행렬의 product로 도출할 수 있다. (Sarrus' rule)

  <img width="139" alt="스크린샷 2024-07-10 오후 4 17 39" src="https://github.com/star-books-coffee/MML/assets/101961939/e1391b5f-5e82-49b1-9dce-caa15485fe4a">

#### Example 4.2
- Determinant는 $\mathbb{R}^n$으로 mapping되는 n 개의 vector의 집합이며, 이는 n 차원에서의 부호를 가진(방향성을 가진) 부피(signed volume)으로 정의된다.
- n = 2인 경우, matrix의 column은 평행사변형 모양을 갖는다.
- 두 벡터가 linearly dependent(선형 종속)이라면 부피는 0이다.
- 두 벡터가 linearly independent(선형 독립)이고, vector $b, g$가 matrix $A = [b, g]$의 columns라면 $A$의 determinant의 절댓값은 0, b, g, b+g의 꼭지점을 갖는 평행사변형의 면적이다.

  <img width="130" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/798d2e43-9bb6-4971-8c09-2206e1409bbe">

  $$ b = \begin{bmatrix}b \newline 0\end{bmatrix}, g = \begin{bmatrix}0 \newline g\end{bmatrix} \quad \begin{vmatrix} b & 0 \newline 0 & g\end{vmatrix} = bg - 0 = bg$$



- $r,b,g \in \mathbb{R}^3$의 경우, 평행육면체의 형태로 spanning하게 된다.
- $r,b,g \in \mathbb{R}^3$, 각각 선형 독립인 3x3 matrix $[r,b,g]$의 determinant 절대값은 평행육면체의 부피가 된다.

  <img width="136" alt="스크린샷 2024-07-10 오후 4 31 33" src="https://github.com/star-books-coffee/MML/assets/101961939/7f8b6be2-7913-4df0-bc71-78c5130b1def">

$$
r = \begin{bmatrix}2 \newline 0 \newline -8 \end{bmatrix}, \quad g = \begin{bmatrix}6 \newline 1 \newline 0\end{bmatrix}, \quad b = \begin{bmatrix}1 \newline 4 \newline -1 \end{bmatrix}$$

$$
A = [r, g, b] = \begin{bmatrix} 2 & 6 & 1 \newline 0 & 1 & 4 \newline -8 & 0 & 1 \end{bmatrix}
$$


#### Theorem 4.2 Laplace Expansion
- $A \in \mathbb{R}^3$에서 **n>3인 경우**에 Laplace expansion(라플라스 전개)를 통해 determinent를 도출한다.
- 기본적인 개념은 $\mathbb{R}^3의 determinant를 구하기 위해 재귀적으로 $\mathbb{R}^{(n-1) x (n-1)}$의 determinant를 연산하는 것이다.
- $A \in \mathbb{R}^3$ 일 때,
  - Column j에 대한 expansion

    <img width="301" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/4bf4ad0a-f6ec-4a26-aa3e-e42a8a855226">

  - Row i에 대한 expansion

    <img width="298" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/7e912fa9-ad0d-4110-97a3-bfca1fc04b44">

- 여기서 $A_{k,j} \in \mathbb{R}^{(n-1) x (n-1)}$로 A의 submatrix라고 하며, k열과 j행을 제거하여 도출한다.


$$
A = [r, g, b] = \begin{bmatrix} 1 & 2 & 3 \newline 3 & 1 & 2 \newline 0 & 0 & 1 \end{bmatrix}
$$

의 행렬의 경우, laplaca expansion을 진행해보면,
<img width="447" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/2b4d3755-c4f2-4f68-b281-3fe9b01a271c">

- 2x2 matrix의 determinant를 구하여 대입하면 이는 아래와 같다.

  <img width="407" alt="스크린샷 2024-07-10 오후 4 49 23" src="https://github.com/star-books-coffee/MML/assets/101961939/a7fd7a9a-39a8-48d2-8a55-e399263f6fe6">

- Surrus' rule과 비교해보면 같은 값을 얻는 것을 알 수 있다.
  
  <img width="530" alt="스크린샷 2024-07-10 오후 4 49 51" src="https://github.com/star-books-coffee/MML/assets/101961939/600121c2-7461-478d-a44d-770592ac1344">

### Determinant Property
- Matrix product의 determinant는 각 determinant를 product한 것과 같다.
  
  $$det(AB) = det(A)det(B)$$


- 변환하여도 determinant는 변하지 않는다.
  
  $$det(A) = det(A^T) $$


- Matrix A가 invertible하면 $det(A^-1) = \frac{1}{det(A)}$이다.

- 행렬을 여러개 추가하여도 $det(A)$는 변하지 않는다.
- 행 / 열에 $\lambda \in \mathbb{R}$을 곱하여 $det(A)를 scailing하면 determinant는 $\lambda^n$을 곱한 만큼 변화한다.
  $$det(\lambda A) = lambda^n det(A)$$
- 행과 열을 바꾸면 $det(A)$의 **부호가 달라진다**

- 마지막 3개의 property로 인해 Gaussian elimination을 사용하여 $det(A)$를 도출할 수 있다.

#### Thereom 4.3
- 정방행렬(Square Matrix) $A \in R^{nxn}$의 $rk(n) = n$이면 $det(A) \neq 0이다.
- 즉, full rank를 가지고 있어야 A는 invertible할 수 있다.


#### Definition 4.4
- 정방행렬 $A \in \mathbb{R}^{nxn}$의 trace(대각합)은 아래와 같다.
  
  <img width="119" alt="스크린샷 2024-07-10 오후 6 21 29" src="https://github.com/star-books-coffee/MML/assets/101961939/201eb4da-675e-4ea0-8e0a-7a8791bdffd2">
- trace는 다음과 같은 property를 갖는다.
  
  <img width="279" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/4e716e86-2f7a-43a7-a553-b04d384589fd">

#### Definition 4.5
- $\lambda \in \mathbb{R}$이고 정방행렬 $A \in \mathbb{R}^{nxn}$에서,
  
  <img width="324" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/57212363-6274-4390-b143-6bb373a946a2">


## 4.2 Eigenvalues and Eigenvectors
- Eigenvalue는 linear mapping마다 존재하는 값으로, **Eigenvector라는 특별한 Vector가 Linear mapping에 의해 어떻게 변화하는지를 나타내는 값**이다.

#### Definition 4.6
- $A \in R^{nxn}$ 행렬이 있을 떄, $\lambda \in \mathbb{R}$는 A의 Eigenvalue이고, $x \in \mathbb{R}$^n\{0\}$은 그에 대응되는 Eigenvector다.
- 이 때, $Ax = \lambda x$가 성립하면 이 식을 Eigenvalue Equation이라고 한다.

#### Definition 4.7 Collinearity and Codirection
- 두 벡터가 같은 방향을 가리키는 경우를 `Codirected`라고 한다. 두 벡터가 같은 방향, 혹은 반대 방향을 가리키면 서로` Colinear`하다고 한다.

#### Remark Non-uniqueness of eigenvectors
- 만약 x가 A의 Eigenvector이고, Eigenvalue $\lambda$를 갖는다면, 모든 $c \in \mathbb{R}\{0\}$에 대해 $cx$는 $A$의 Eigenvector이고, 같은 $\lambda$를 갖는다.
- 이를 식으로 표현하면 다음과 같다.
  <img width="218" alt="스크린샷 2024-07-10 오후 6 39 18" src="https://github.com/star-books-coffee/MML/assets/101961939/044dd509-4397-4272-b5d6-ff19595248dd">

- 따라서 $x$에 colinear한 모든 벡터는 A의 Eigenvector인 것이다.


#### Theorem 4.8
- $\lambda$가 $A$의 Characteristic polynomial인 $P_a(\lambda)$의 근이면, $\lambda \in \mathbb{R}$은 $A \in R^{nxn}$의 Eigenvalue이고, 이는 서로 필요충분 조건이다.

#### Definition 4.9
- nxn 행렬 A의 Eigenvalue $\lambda_{i}$가 있다고 가정하면, $\lambda_{i}$의 Algebraic multiplicity를 Characteristic polynomial의 근의 개수로 정의한다.

#### Definition 4.10 Eigenspace and Eigenspectrum
- $A \in mathbb{R}^{nxn}$에 대하여 $A$의 모든 Eigenvector의 집합은 $mathbb{R}^{n}$의 subspace를 span한다.
- 해당 Eigenvector가 span하는 space를 A의 $\lambda$에 대한 Eigenspace라고 부르고 $E_{\lambda}로 표현한다.
- A의 모든 Eigenvalue의 집합을 Eigenspectrum, 혹은 A의 spectrum이라고 한다.
- 만약 $\lambda가 $A \in mathbb{R}^{nxn}$의 Eigenvalue라고 하면, 이에 대응되는 Eigenspace, $E_{\lambda}$는 Homogeneous한 연립선형방정식 $(A- \lambda I)x = 0$의 해공간(solution space)이다.

#### Example 4.4 The Case of the Identity Matrix
- 단위행렬 I는 Characteristic polynomial $P_I(\lambda) = det(I- \lambda I) = (1-\lambda)^n = 0$을 가지고 있다.
- 이 때 eigenvalue는 $\lambda = 1$을 중근으로 가진다.
- 또한 $Ix = \lambdax = 1x$가 모든 $x \in \mathbb{R}^n\{0\}$ 벡터를 포함한다.
- 따라서 단위 행렬의 유일한 eigensapce인 $E_1$은 n 차원을 span 하고 $mathbb{R}^n$의 모든 n개의 standard basis vector는 $I$의 eigenvector라는 것을 알 수 있다.

#### Eigenvalue와 Eigenvector에 대한 유용한 특성들


<img width="514" alt="스크린샷 2024-07-10 오후 6 55 25" src="https://github.com/star-books-coffee/MML/assets/101961939/031d7a6f-c125-4361-935d-fe04bb7d578b">

#### Definition 4.11
- $\lambda_i$를 square matrix A의 eigenvalue라고 하면, $\lambda_i$의 eigenvector 중 linearly independent한 것을 숫자의 Geometric multiplicity라고 한다.
- 이 떄, geometric multiplicity는 eigenspace의 demensionality라고 할 수 있다.

### Graphical Intuition in Two Dimensions

- 다음은 기하학적 직관을 위해 determinants, eigenvector, eigenvalue를 다른 다섯 개의 linear mapping을 사용해 변화시켰을 때의 그림이다.

  <img width="385" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/6ea9b65a-3471-4efa-93a5-36529d37b80b">

## 4.3 Cholesky Decomposition

- Cholesky Decomposition은 symmetric, positive definite matrix를 분해하는 데 사용

#### Theroem 4.18
- Symmetric, positive definite matrix A는 $LL^T$를 통해 분해 가능
- 여기서 $L$은 대각 성분을 가진 lower triagular matrix를 의미
  <img width="364" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/9d3eb37f-6edd-4fc9-9b69-5aac16fe73d5">

#### Difinition 4.19 Diagonalizable
- Matrix $A\in R_{nxn}$이 대각행렬과 similar하다면, 즉 $D= P^{-1} AP$를 만족시키는 역행렬이 존재하는 행렬 $P$가 존재한다면, 행렬 A를 diagonalizable, 즉 대각화가 가능하다고 말한다.
- $A \in R^{nxn}$이 있고, $\lambda_1, ..., \lambda_n$은 스칼라들의 집합 $p_1, ..., p_n$은 $R^{nxn}$에서의 벡터 집합이라 하자. 그리고 $P := [p_1, ... p_n]$을 정의하고, $D \in R^{nxn}$을 대각 요소들이 $\lambda_1, ..., \lambda_n$인 대각행렬이라고 정의합니다.
- 그러면 만약  $\lambda_1, ..., \lambda_n$이 A의 eigenvalule이고, $p_1, ... p_n$이 A의 eigenvector일 때 다음 식이 만족함을 볼 수 있다.

  $$AP = PD$$

- 아래 식이 만족하기 때문에 위 식이 만족한다.
  <img width="395" alt="스크린샷 2024-07-10 오후 7 25 16" src="https://github.com/star-books-coffee/MML/assets/101961939/0aa70ac3-3a82-46f3-915b-ea9d8115baf3">
  <img width="129" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/056b5934-134a-4168-b6e9-80ac11349bf8">

- 따라서 $P$의 column들은 반드시 $A$의 eigenvector이다.

### Geometric Intuition for the Eigendecomposition

<img width="307" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/e842997f-a330-4902-b05c-1b4f78eb9504">

- 행렬의 eigendecomposition은 다음과 같이 해석할 수 있다.
- 먼저 행렬 $\boldsymbol{A}$ 를 standard basis에 대한 linear mapping의 transformation matrix라고 하자.
- $\boldsymbol{P}^{-1}$ 은 standard basis에서 eigenbasis로의 basis change를 수행한다. 이는 eigenvectors $\boldsymbol{p}_i$ (그림의 red/orange 화살표)를 standard basis vectors $\boldsymbol{e}_i$ 로 만든다. 그리고, 대각 행렬 $\boldsymbol{D}$ 는 eigenvalues $\lambda_i$ 만큼 축을 따라 scaling 한다.
- 마지막으로 $\boldsymbol{P}$ 는 scaling된 벡터들을 다시 standard/canonical coordinates로 변환하며 이는 $\lambda_i\boldsymbol{p}_i$ 와 같다.

- Diagonal matrix $\boldsymbol{D}$ 를 사용하면 거듭제곱을 효율적으로 계산할 수 있다.
- 그러므로, $\boldsymbol{A}\in\mathbb{R}^{n\times n}$ 행렬의 거듭제곱은 eigenvalue decomposition을 사용하면 다음과 같이 계산할 수 있다.
- 또한, $\boldsymbol{D}^k$ 는 각 대각 요소들만 거듭제곱해주면 되므로 효율적으로 계산할 수 있다.

$$[\boldsymbol{A}^k = (\boldsymbol{PDP}^{-1})^k = \boldsymbol{PD}^k\boldsymbol{P}^{-1}$$

- Eigendecomposition $\boldsymbol{A} = \boldsymbol{PDP}^{-1}$ 이 존재한다고 가정해보자. 그러면, 다음의 식을 통해 $\boldsymbol{A}$ 의 determinant를 효율적으로 계산할 수 있다.
</ul>

$$
\det(\boldsymbol{A}) = \det(\boldsymbol{PDP}^{-1}) = \det(\boldsymbol{P})\det(\boldsymbol{D})\det(\boldsymbol{P}^{-1})  \\ = \det(\boldsymbol{D}) = \prod_i d_{ii}
$$


- 지금까지 살펴본 것과 같이 eigenvalue decomposition은 매우 편리하다.
- 하지만 eigenvalue decomposition은 square matrix에서만 적용할 수 있으며, 항상 적용할 수 없다.
- 따라서, 모다 더 일반적인 행렬에 대한 decomposition을 수행하는 것이 필요하며, 4.5장에서는 보다 더 일반적인 행렬을 분해하는 기법인 Singular Value Decomposition(특잇값 분해)에 대해 살펴본다.

## 4.5 Singular Value Decomposition
- SVD는 모든 행렬에 대해 항상 존재하며, 행렬을 세 개의 행렬로 분해한다
  $\boldsymbol{A} = \boldsymbol{U\Sigma V}^\top$. $\boldsymbol{U}$와 $\boldsymbol{V}$는 각각 $\boldsymbol{A}$의 좌측 및 우측 직교행렬이고, $\Sigma$는 $\boldsymbol{A}$의 특잇값들을 가진 대각행렬이다.

### SVD의 속성
- $\boldsymbol{U}$: $m \times m$ 직교행렬, $\boldsymbol{U}^\top\boldsymbol{U} = \boldsymbol{I}$
- $\boldsymbol{V}$: $n \times n$ 직교행렬, $\boldsymbol{V}^\top\boldsymbol{V} = \boldsymbol{I}$
- $\Sigma$: $m \times n$ 대각행렬로, 대각성분은 $\sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_r \geq 0$

### Geometric Intuition
- $\boldsymbol{V}^\top$: 원래 벡터 공간에서 기저 변환 수행
- $\Sigma$: 스케일링 및 차원 변환 수행
- $\boldsymbol{U}$: 새로운 벡터 공간에서 다시 기저 변환 수행

### Existence and Construction of SVD
- $\boldsymbol{A}^\top\boldsymbol{A}$의 고윳값과 고유벡터를 통해 $\boldsymbol{V}$와 $\Sigma$를 구한다
- $\boldsymbol{AA}^\top$의 고윳값과 고유벡터를 통해 $\boldsymbol{U}$를 구한다
- $\boldsymbol{A}$의 특잇값은 $\boldsymbol{A}^\top\boldsymbol{A}$와 $\boldsymbol{AA}^\top$의 양의 고윳값의 제곱근이다
