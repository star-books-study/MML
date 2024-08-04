# 7. Continuous Optimization

- This chapter describes the basic numerical methods for training ma- chine learning models.
- This chapter covers two main branches of continuous optimization unconstrained and constrained optimization.
- y convention, most objective functions in ma- chine learning are intended to be minimized
  ➡️ the best value is the **minimum value.**
- Intuitively finding the best value is like finding the valleys of the objective function, and the gradients point us uphill.
- The idea is to move downhill (opposite to the gradient) and hope to find the deepest point.

## 7.1 Optimization Using Gradient Descent
- 이번 단원에서는 아래와 같이 실수 값을 가지는 목적 함수의 Minimum 값을 구하는 Optimization 문제를 다룰 것이다.
<img width="570" alt="image" src="https://github.com/user-attachments/assets/be97ae1c-9a46-4918-93c3-bc6685d96e9e">

- 이 때 $f$는 $f:\mathbb{R}^d \rightarrow \mathbb{R} 이고 미분 가능하며, 수리적으로 최적해를 바로 찾을 수 없는 함수라고 가정하자.
- 이런 경우에 Gradient Descent는 가장 첫 순위로 고려되어야 할 최적화 알고리즘이다.
- Gradient Descent 방법에서는 Local minimum을 찾기 위해 현재 위치에서 값이 감소하는 방향, 즉 Gradient가 음수인 쪽으로 조금씩 point를 이동시켜 더 이상 주변에 값이 감소하는 point가 없으면 local minimum이라고 판단한다. 이때 방향은 Gradient가 음수인 방향 중에서도 가장 경사가 급한 쪽으로 잡는다.


### 7.1.1 Step-size
