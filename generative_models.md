---
layout: default
use_math: true
comments: true
---

### Deep generative models


Generative models usually takes input training samples from some distribution and tries to learn a model that represents that distribution. 


Usecases:
- Fair models
- Outlier detection, detect outliers in data using the learned distribution


Latent variable models:

- Autoencoders and Variational Autoencoders
- Generative Adversarial Networks


Latent variables: True explanatory factors that are behind the data.


### Autoencoders

Encoder and decoder
Minimize reconstruction error.


### Variational Autoencoders

Latent variable is probabilistic and defined by parameters of the distribution ( mean and variance for gaussian)

In order to control complexity, a regularization term is added, which is the KL Divergence between the inferred latent distribution and a fixed prior on the latent distribution.

A common prior on the latent distribution is a gaussian with zero mean and unit standard deviation. This avoids discontinuties in the latent space and reduces pointed / narrow distributions.


### Generative Adversarial Networks (GANs)

Generator: Start from random noise to create $X_{fake}$

Discriminator: Tries to indentify, real $X$ from $X_{fake}$.


The objective function for this problem would be:

$arg \hspace{3px} min_G \hspace{10px} arg \hspace{3px} max_D \hspace{10px}log D(G(z)) + log( 1 - D(X)) $

This is because we want to maximize discrimator performance $D()$

and then try to confuse the best discriminator with more and more realistic generated samples $G(z)$.


#### Conditional GANs

#### Cycle GANs

