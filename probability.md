---
layout: default
comments: true
---


### Probability Distributions

#### Expectation / Variance

#### Representation of probability distribution in terms of Moments

#### Bayes Theorem

#### Central Limit Theorem

#### Markov Chain and Stationary Distributions

Markov Chain: This is a chain of states, where each state depends on its previous state. The tranistion probability between states are defined by a transition matrix.

Initially, the probability of being in a particular state $s$ is $p_t(s)$. If we move to the next step based on the transition probability in the transition matrix, we will be at a state $s$ with a probability $p_{t+1}(s)$.

After a large number of such transitions, the probability distribution at state $t$ will the same as at $t+1$, at this point the markov chain is said to have reached a stationary distribution $\pi(s)$.

$\pi * P = \pi$

If we solve this equation, i.e find the left eigen vector of P with eigen value 1, we have found the stationary distribution.


### Sampling form a distribution

#### Inverse Transform Sampling

#### Accept Reject Sampling

we want to find probability distribution $p(s)$ w.r.t a function $f(s)$

We have numerator $f(s)$ but the denominator ( normalizing constant ) which is the integral of $f$ over  all possible values is intractable to calculate.

We can use another distribution $g(x)$ and then sample from $g$ and accept samples with a probability $f(x) / g(x)$ and reject otherwise. This actually gives us samples as if we sampled from the original distribution $p(s$)

#### Markov Chain Monte Carlo



#### Gibbs Sampling

#### Metropolis Hastings