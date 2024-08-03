# 7. Continuous Optimization

- This chapter describes the basic numerical methods for training ma- chine learning models.
- This chapter covers two main branches of continuous optimization unconstrained and constrained optimization.
- y convention, most objective functions in ma- chine learning are intended to be minimized
  ➡️ the best value is the **minimum value.**
- Intuitively finding the best value is like finding the valleys of the objective function, and the gradients point us uphill.
- The idea is to move downhill (opposite to the gradient) and hope to find the deepest point.

## 7.1 Optimization Using Gradient Descent
- We now consider the problem of solving for the minimum of a real-valued function
<img width="570" alt="image" src="https://github.com/user-attachments/assets/be97ae1c-9a46-4918-93c3-bc6685d96e9e">
