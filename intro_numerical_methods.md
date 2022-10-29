---
layout: default
use_math: true
comments: true
---

For any $m$ x $n$ matrix $A$, $A^T A $ and $A A^T$ are special in linear algebra, with following properties:

- square and symmetrical
- at least positive semidefinite (eigenvalues >= 0)
- same positive eigenvalues
- same rank as A
- Their eigenvectors can be chosen to be orthonormal. 

### Eigen values and Eigen vectors

A scalar $ \lambda$ and vector $v$ are eigenvalue and eigenvector of a matrix $A$ if $Av = \lambda v$

Applications:
- If A is a markov transition matrix, the eigenvalue 1 and its eigen vector denote the state state distribution of states
- Solutions of linear systems can be combined lienarly to form the complete solution. To approximate the soultion, we can choose only the top few eigen values.

### Matrix Diagonalization

### SVD

Any matrix $A$ can be decomposed into:

$ A = U \Sigma V^T$

where $U$ and $V$ are matrices consisting of orthonormal eigenvectors of matrices $A A^T$ and $A^T A$, $\Sigma$ is a diagonal matrix with root of eigenvalues of $A$

### Solving system of linear equations


### Root finding

Given a function $f$ for variable $x$ we aim to find roots such that $f(x) = 0$.

A popular method to approximate roots is the netwons method.

First derivative is defined as:

$ f'(X) = f(x_1) - f(x) / (x_1 - x)$

assuming we want to move along the slope (tangent) line all the way to zero, we can assign $f(x_1) = 0$

rearranging, we get:

$ x_1 = x - f(x) / f'(x)$

we can iterate over this to find the roots


### Second order methods

Second order approximation around a point $x_1$ is:

$ f(x_1 + t) = f(x_1) + f'(x_1) t + (1/2)f''(x_1)t^2$

setting the first derivative w.r.t to $t$ to zero, we get:

$ t = - f'(x_1) / (f''(x_1))$

in matrix notation:

$ T = - H(W)^{-1} \* G(W)$

where $H$ denotes Hessian and $G$ denotes gradient matrix (Jacobian).

Because of the second order equation, the approximation is a convex parabola, which means that Hessian is symmetric square matrix and positive semi-definite.



#### Positive semi-definite

A matrix $M$ that is symmetric is positive semi-definite if all its eigenvalues are non-negative, also for any vector $x$,

$ x^T \* M \* x >= 0$

Positive-definite and positive-semidefinite real matrices are at the basis of convex optimization, since, given a function of several real variables that is twice differentiable, then if its Hessian matrix (matrix of its second partial derivatives) is positive-definite at a point p, then the function is convex near p, and, conversely, if the function is convex near p, then the Hessian matrix is positive-semidefinite at p.

#### Level curves and gradients

For multi-variable function $f(x,y,z)$, its tangent plane at any point is the plane containing tangent vectors to the level curve at that point.

The gradient vector $ \triangledown f =  < f_x, f_y, f_z > $ is known to be perpendicular to this tangent plane at that point. We can use this result to solve optimization problems that involve minimizing a function $f(x,y,z)$ based on some constraint $g(x,y,z)$ which is also function of those variables. This beautifully fits into building different machine learning algorithms like Support Vector Machines.

#### Optimization with constraints

##### Lagrange Multipliers

Lagrange multipliers can be used to find the extremum of a multi-variable functions based on some constraints.
Given variables $x, y, z$ ,

Our goal is to minimize function $f(x,y,z)$ given a constraint $g(x,y,z) = c$

When two functions intersect at a single point, their gradient vectors are parallel to each other.

Hence we can write $ \triangledown f = \lambda *  \triangledown g$


#### References:

[https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote07.html](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote07.html)
