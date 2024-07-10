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

  $$ r = \begin{bmatrix}2 \newline 0 \newline -8\end{bmatrix}, g = \begin{bmatrix}6 \newline 1 \newliine 0\end{bmatrix}, b = \begin{bmatrix}1 \newline 4 \newliine -1\end{bmatrix} \quad A = [r,g,b] = \begin{vmatrix} 2 & 6 & 1 \newline 0 & 1 & 4 \newline -8 & 0 & 1\end{vmatrix}$$
  
  
