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
step size가 큰 경우 한 번 이동하는 거리가 커지므로 빠르게 수렴할 수 있다는 장점이 있다. 하지만, step size를 너무 크게 설정해버리면 최소값을 계산하도록 수렴하지 못하고 함수 값이 계속 커지는 방향으로 최적화가 진행될 수 있다.

또, 한편 step size가 너무 작은 경우 발산하지는 않을 수 있지만 최적의 $x$를 구하는데 소요되는 시간이 오래 걸린다는 단점이 있다.

아래의 그림을 통해 적절한 step size를 선택하지 못하는 경우 수렴하지 않거나 발산하는 경우를 확인해볼 수 있다.

![image](https://github.com/user-attachments/assets/8d4b1fb2-8740-4038-b481-018766d4740b)


## 참고자료
- https://angeloyeo.github.io/2020/08/16/gradient_descent.html
