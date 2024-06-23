# 2. Linear Algebra
- 선형 대수는 벡터와 벡터를 다루는 규칙을 연구하는 학문이다.
- 우리가 학교에서 배우는 벡터는 보통 화살표로 표시되는 기하 벡터 (e.g. $\vec{x}$, $\vec{y}$)이다.
- 이 책에서는 보다 일반적인 벡터를 논하며, 볼드체로 벡터를 표현한다. (e.g. **$x$**, **$y$**)

- 일반적으로 **벡터는 함께 더할 수 있고, 스칼라와 곱할 수 있는** 특별한 객체이다.
- 추상적인 수학적인 관점으로 볼 때, 이 두 가지 속성을 만족하면 벡터로 간주된다.

## 다양한 벡터 종류
다음은 벡터의 몇 가지 예시이다.

### 1. **기하 벡터 (Gemetric vector)**
  <img width="192" alt="image" src="https://github.com/star-books-coffee/MML/assets/101961939/ec3d4958-5bc6-43dc-8251-5074ff28f35e">
  
 - 고등학교 수학과 물리에서 배우는 벡터로, 방향을 가진 선분이다.
 - 두 기하학적 벡터  $\vec{x}$, $\vec{y}$는 더할 수 있다. ➡️ $\vec{x} + \vec{y} = \vec{z}$
   - $\vec{z}$는 새로운 기하 벡터이다.
 - 또한, $\lambda$와 기하 벡터를 곱하면 $\lambda \vec{x}$가 되며, 이 역시 기하 벡터이다.

### 2. **다항식 (Polynomial)**
   
   <img width="308" alt="스크린샷 2024-06-22 오후 4 54 32" src="https://github.com/star-books-coffee/MML/assets/101961939/6cb84d08-5282-4da1-b8c8-fbf46ebf49f9">
   
 - 위 그림에서 볼 수 있듯이 두 polynomial을 더하면 또 다른 polynomial이 된다.
 - 또한, 스칼라 $\lambda$와 다항식을 곱하면 역시 polynomial이 된다.

   ➡️ Polynomial도 벡터다.
 - polynomial은 기하 벡터와 매우 다르다.
   - geometry vector는 구체적인 "그림"인 반면, polynomial은 추상적인 개념이다.

     > 하지만 둘 다 앞서 설명한 벡터의 성질을 가진다.
  
### 3. **오디오 신호 (Audio Signal)**
  - audio signal은 숫자의 연속으로 표현된다.
  - 오디오 신호를 더하면 새로운 오디오 신호가 된다. 
  - audio signal를 스칼라로 곱하면 또 다른 오디오 신호가 된다.
  ➡️ audio signal도 벡터다.

### 4. $\mathbb{R}^n$의 요소
  - $\mathbb{R}^n$의 요소(즉, $n$개의 실수로 구성된 튜플)는 벡터다. 
  - $\mathbb{R}^n$은 polynomial보다 추상적이며, **이 책에서 집중적으로 다루는 개념**이다.
  - 예를 들어, 다음과 같은 수식은 세 개의 숫자로 이루어진 벡터다.

  $$a =
 \begin{bmatrix}
  1 \\
  2 \\
  3  \\
 \end{bmatrix}
 \in \mathbb{R}^3$$
  - 두 벡터 $\mathbf{a}, \mathbf{b} \in \mathbb{R}^n$을 더하면 새로운 벡터 $\mathbf{c} = \mathbf{a} + \mathbf{b} \in \mathbb{R}^n$가 된다.
  - 또한, 벡터 $\mathbf{a} \in \mathbb{R}^n$과 스칼라 $\lambda \in \mathbb{R}$를 곱하면 스케일링된 벡터 $\lambda \mathbf{a} \in \mathbb{R}^n$가 된다.
  - 공간 $\mathbb{R}^n$의 요소로서 벡터를 고려하면 컴퓨터에서의 실수 배열과 느슨하게 대응할 수 있다.
  - 많은 프로그래밍 언어가 배열 연산을 지원하여 알고리즘을 효율적으로 구현할 수 있다.

## 2장에 대한 소개
### 벡터 개념의 유사성
- 벡터들은 서로 더하고, 스칼라로 곱할 수 있다.
- 선형대수학은 이러한 벡터 개념 상의 유사점에 중점을 둔다. 
- 우리는 $\mathbb{R}^n$ 공간의 벡터에 집중하며, 이는 선형대수학의 알고리즘이 $\mathbb{R}^n$에서 공식화되기 때문이다.
### 데이터와 벡터
- 8장에서 데이터를 종종 $\mathbb{R}^n$의 벡터로 간주할 수 있다.
- 이 책에서 우리는 유한한 차원의 벡터 공간에 집중할 것이며, 기하 벡터와 배열 기반 알고리즘을 활용한다.

### 폐쇄성
- 수학의 중요한 개념 중 하나는 폐쇄성(closure)이다.
  - 주어진 연산으로 얻을 수 있는 모든 결과물의 집합이 무엇인지를 의미
    - 벡터의 경우 : 작은 벡터 집합에서 시작하여 서로 더하고 스칼라를 곱하여 결과를 얻을 수 있는 벡터들의 집합은 무엇인가
      ➡️ 이는 벡터 공간(vector space)을 형성한다.

- 벡터 공간(vector space)은 많은 머신러닝의 기초가 된다.

### 마인드맵
- 이 장에서 소개된 개념을 요약한 그림

  <img width="581" alt="스크린샷 2024-06-23 오후 8 52 55" src="https://github.com/star-books-coffee/MML/assets/101961939/9e9fcf1e-a77b-4a30-aa66-d888a676cba0">

- 이 장에서 소개된 개념들은 3장에서 기하학의 개념을 포함하도록 확장된다.
- 5장에서는 행렬 연산에 대한 지식이 필수적인 벡터 미적분을 논의
- 10장에서는 주성분 분석(PCA)를 통해 차원 축소를 위해 투영(projection)을 사용
- 9장에서는 최소자승문제(least-squates problem) 해결에서 선형 대수가 중심 역할을 하는 선형 회귀(linear regrssion)를 논의할 것
