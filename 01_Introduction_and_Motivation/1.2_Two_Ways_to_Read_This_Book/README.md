# 1.2 Two Ways to Read This Book

## 두 가지 학습 전략
MML을 이해하기 위한 두 가지 전략
- **bottom-up** 방식 : 기초부터 고급 개념으로 단계적인 학습
  - 장점 : 이전에 배운 개념에 의존 가능
  - 단점 : 동기부여가 부족해 기초 개념을 빨리 잊을 수 있음
- **top-down** : 실용적인 필요에서 기초 개념으로 접근
  - 장점 : 왜 특정 개념을 공부하는지 명확히 이해
  - 단점 : 지식이 불안정한 기초 위에 구축될 수 있고, 이해하기 어려운 용어를 기억해야 함.

## 책의 구성
이 책은 수학적 개념을 응용과 분리하였으며, 두 부분으로 나눠져 있음.
- 1부 : 수학적 기초를 다룸
- 2부 : 1부의 개념을 기초로 한 주요 머신 러닝 문제들(회귀 분석, 차원 축소, 밀도 추정, 분류)을 다룸
  <img width="370" alt="스크린샷 2024-06-19 오후 1 01 41" src="https://github.com/star-books-coffee/MML/assets/101961939/917111b4-e95e-4b83-beab-457b227aef32">

## 복합적인 학습 접근
- 독자들은 하향식과 상향식을 결합하여 학습.
- 기본적인 수학적 기술을 쌓은 후 응용을 통해 더 복잡한 개념에 도전

## Part 1 - 수학에 관한 내용

### 2장 : 선형대수학 (linear algebra)
- 숫자 데이터를 벡터로, 데이터 표를 행렬료 표현
- 벡터와 행렬의 기본 개념을 다룬다.

### 3장 : 해석기하학 (analytic geometry)
- 벡터 간의 유사성 측정을 위해 유사성과 거리 연산 도입

### 4장 : 행렬 분해 (matrix decomposition)
- 행렬의 기본 개념과 유용한 연산 소개
- 데이터 해석과 효율적인 학습을 위한 행렬 분해 기법

### 6장 : 확률 이론 (probability theory)
- 데이터의 노이즈(noise)와 신호(signal)을 구별하는 방법
- 예측 값에 대한 신뢰도 정량화

### 5장 & 7장 : 벡터 미적분학 (vector calculus) 및 최적화 (optimization)
- 벡터 미적분학에서 기울기(gradient) 개념을 다루고, 이를 기반으로 최적화 기법 설명
- 최적화는 머신 러닝 모델의 성능을 최대화하기 위한 파라미터 찾기

## Part 2 - 머신러닝에 관한 내용
> 챕터가 지날 수록 어려워짐

### 8장 : 머신러닝의 기초
- 머신 러닝의 세 가지 구성 요소인 `data`, `model`, `parameter estimation`을 수학적으로 설명
- 과도하게 낙관적인(optimistic) 평가를 방지하기 위한 실험 설정 가이드라인 제공
- 목표: 새로운 데이터에도 잘 작동하는 예측기(predictor) 구축

### 9장 : 선형 회귀 (linear regression)
  - $$\text{입력 } x \in \mathbb{R}^D \text{를 관찰된 값 } y \in \mathbb{R} \text{로 매핑하는 함수 찾기}$$
- 최대 우도 추정(maximum likelihood estimation), 최대 사후 확률 추정(maximum a posteriori estimation), 베이지안 선형 회귀(Bayesian linear regression) 논의

### 10장: 차원 축소 (demensionality reduction)
- 주성분 분석을 사용하여 고차원 데이터를 저차원으로 변환
- 데이터 모델링에만 관심이 있으며, 데이터 포인트와 관련된 레이블이 없다.

### 11장: 밀도 추정 (density estimation)
- 주어진 데이터셋을 설명하는 확률 분포(probability distribution) 찾기
- 가우시안 혼합 모델(Gaussian mixture model)과 파라미터 찾기 위한 반복 스키마(iterative schema) 논의
- 데이터의 저차원(low-dimensional) 표현이 아닌, 밀도 모델(density model)에 관심을 갖는다.

### 12장: 분류 (classification)
- 서포트 벡터 머신을 사용하여 정수 레이블을 가진 데이터 분류
- 회귀와 달리, 레이블이 실수값이 아닌 정수값이므로 특별한 주의 필요
