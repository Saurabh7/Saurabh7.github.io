---
layout: default
use_math: true
comments: true
---
### Machine Learning

##### Primer with Linear Regression

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

##### Normal Equation

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

##### Gradient Descent

We can also iteratively update the weights as ( gradient descent ):

$ W = W - \eta \nabla L$

where $ \nabla L $ is the jacobian of L w.r.t $W$




