---
layout: default
use_math: true
comments: true
---
<div class="row">
  <table>
    <tr>
      <td> <h5 style="float: left; margin-left:20px"><a href='/'> About Me </a></h5></td> 
      <td> <h5 style="float: left; margin-left:20px"><a href='/projects'> Projects </a></h5></td> 
      <td> <h5 style="float: left; margin-left:20px"><a href='/blog'> Blog </a></h5></td> 
    </tr>
  </table>
</div>
### Machine Learning

#### Primer with Linear Regression & Logistic Regression

The most common problem in Machine Learning is predicting a target variable given a set of observations. In case the target variable is continous ( can take arbitary real values ), 
this is what is commonly called a regression problem.

If we have a set of observations $X$ consisting of $n$ individual observation $x_i=\lbrack x_{1i} ... x_{ki} \rbrack$ and corresponding targets $Y$ consisting of 
target $y_i$ , the problem can be formulated as:

$$X^T * W = Y$$

where $\*$ denotes matrix multiplication and $W$ is a $k$ x $n$ matrix we wish to learn.

For some unseen samples, the error in prediction would be the difference between actual targets $Y$ and the predicted ones. We can use the absolute differences,
$\| y_{i_pred} - y_i \|$ or squared differences $\(y_{i_{pred}} - y_i\)^2$ as errors.

Squared difference gives increasing importance to larger errors.

<img src="https://user-images.githubusercontent.com/4285091/194720700-05bc4dfe-9e44-458d-8e10-497805559d6d.png" width="500" />



In matrix notation, $Y_{pred} = X^T * W $, hence squared error is 

$L = \(Y_\{pred\} - Y\)^T * \(Y_{pred} - Y\)$

$L = (X^T * W - Y)^T * (X^T * W - Y)$

#### Normal Equation

We can set the first order derivative to zero to get the minima,

$dL / dW = 0$

$d / dW (W^T\*X - Y^T) * (X^T * W - Y)$

$d / dW (W^T\*X\*X^T \* W - W^T\*X\*Y - Y^T\*X^T\*W + Y^T\*Y) =0$


$d / dW (W^T\*X\*X^T \* W - 2W^T\*X\*Y + Y^T\*Y) =0 $

$2 X\*X^T \* W - 2\*X\*Y  = 0 $

$ X\*Y  = X\*X^T \* W  $

$  X\*X^T \* W  = X\*Y  $

$   W  = (X\*X^T)^{-1} \* X\*Y  $

which is the normal equation. 
This is a closed form solution to find value of $W$ that minimizes $L$.

#### Gradient Descent

We can also iteratively update the weights as ( gradient descent ):

$ W = W - \eta \nabla L$

where $ \nabla L $ is the jacobian of $L$ w.r.t $W$


#### Classification & Logistic Regression

If points in $X$ lie on the hyperplane defined by a matrix $W$, then $X^T * W $ is zero.

We can use this hyperplane as a decision boundary to classify values $X^T * W > 0$ as positive labels and $X^T * W < 0$ as negative labels 


Logistic Regression makes the assumption that probability of $Y=1$ is given by logistic function of our mapping value $X^T\*W$.

$P(Y=1 \| X = x) = \frac{1}{1 + e^{X^T\*W}}  = $sigmoid$(X^T\*W)$


The log odds of a points are $ \log{\frac{P(Y = 1)}{P(Y = -1)}} = (X^T * W)$


#### Regularization

Complex models can overfit on training data. In order to restrict models from being too complex, we can add constraints on the weights. The 2 common ways are adding constraints on L1 norm of $W$: ${\|\|W\|\|}\_{1}$ or L2 norm of $W$: ${\|\|W\|\|}\_{2}$ 

Having smaller weights means that the model output changes lesser for small flactuations in the input.

Adding L1 norm to the constraint enforces sparsity, i.e the weights on non-important features are driven to zero. 

$d / dW ({\|\|W\|\|}\_{1} ) = sign(W)$


$d / dW ({\|\|W\|\|}\_{2} ) = W$

As $W$ approaches zero, the derivative of L2 norm decreases to neglibile, while for L2 it stays 1, which leads to weights being driven to zero for L1 penatly.

Adding L2 penalty still leads to a closed form solution:

$  X\*X^T \* W + \lambda\*W = X\*Y  $

$W = (X\*X^T + \lambda\*I)^{-1} \* X\*Y $


#### Netwons Method

Any function $f$ can be approximated at point $a$ as:

$f(x) = f(a) + f'(a) (x-a) + (1/2) f"(a) (x-a)^2$

at minima, 


#### SVM



#### References:
[https://cs.stackexchange.com/questions/77368/why-do-we-try-to-maximize-lagrangian-in-svms](https://cs.stackexchange.com/questions/77368/why-do-we-try-to-maximize-lagrangian-in-svms)
[https://stats.stackexchange.com/questions/451487/confusion-about-karush-kuhn-tucker-conditions-in-svm-derivation](https://stats.stackexchange.com/questions/451487/confusion-about-karush-kuhn-tucker-conditions-in-svm-derivation)
[https://see.stanford.edu/materials/aimlcs229/cs229-notes3.pdf](https://see.stanford.edu/materials/aimlcs229/cs229-notes3.pdf)
[https://www.cs.ubc.ca/~schmidtm/Documents/2005_Notes_Lasso.pdf](https://www.cs.ubc.ca/~schmidtm/Documents/2005_Notes_Lasso.pdf)


