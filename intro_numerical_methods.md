---
layout: default
use_math: true
comments: true
---


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

#### References:

[https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote07.html](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote07.html)
