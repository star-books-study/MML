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
