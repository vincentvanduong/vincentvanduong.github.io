---
layout: page
title: My Statistical Learning in Practice Notes
description: Notes on my Cambridge Part III Statistical Learning in Practice Notes
img: /assets/img/knn.png
importance: 3
---

# Purpose

This course is presented in a mathematical context, obliterating most of my intuition. So these are my notes with possibly some examples (in R 😩)


# Regression models

## General linear models (GLM's)

GLMs are usually introduced via the **exponential dispersion family**, but I find this introduction not very isntructive. Instead, let's suppose we have some data $$ X, Y $$. In real-life, we hope that this data is generated through a mechanistic process (e.g., a chemical reaction.) Depending on the context, $$ Y $$ may be **non-linear** (e.g., $$ Y $$ is a concentration of a product in ppm and $$ X $$ describes viscocity, temperature, etc. ) We want to know: how should we fit the data?

In experiemental physics we are taught to **linearize our data** -- this is what GLMs will do for us!

I'll give a few practical examples now. 

### Example 1: Predicting the probability of an event

Suppose we are given binary outcomes ($$ y = 0,1 $$) based on observations $$ X $$. Because we are scientists, a good Ansatz would be the logistic model with a linear model embedded inside:

$$ y = \frac{1}{1-e^{-X^T \beta}} $$.

Why would we do it this way? Well this ensures that our model predicts some kind of a probability (it will always predict between 0 and 1). It also works well because it is invariant if we swap the binary outcomes (i.e., if we label the events then we get the same model.) To see this, let's investigate the linear model.

$$ X^T \beta = \log{\frac{y}{1-y}} $$.

So all we need to do is perform a linear regression with covariates $$ X $$, but with linearized responses $$ \log{\frac{y}{y-1}} $$. Indeed this ensures that our model is invariant under $$y \mapsto 1-y $$ (the $$ \beta $$ term will simply pick-up a minus sign.)

It is more likely that a neural net or random forest will outperform this logistic regression. However, GLMs shine because they provide us with confidence intervals on our predictions while the former don't (they are non-parametric.)

### Example 2: Tensor notation

Loss functions, such as least squares, are often matrix equations that need to be minimised. Computing the best model parameters is then a calculus problem. However, when models become complicated -- it can involve many parameters to estimate -- the calculus problem turns multivariate. Differentiating is best performed through **Einstein Sumation Convention** (thank you physicists) so as to remove ambiguities encountered from transpositions, inverses, among other matrix operations.

Let's begin by looking a modified least squares regression:

$$l(\beta) = (Y_i - X_{ij}\beta_j)(Y_i - X_{il}\beta_l) + \lambda \beta_i R_{ij} \beta_j$$

Here $$R$$ is some positive definite kernel. Our goal is to **minimise** the loss, so we will have to set its gradient to zero. It is a straightforward calculation to obtain the gradient of the loss function by differentiating with respect to some arbitrary parameter $$\beta_k$$. 

$$\frac{\partial l}{\partial \beta_k} = -2(Y_i - X_{ij}\beta_j)X_{ij}\delta_{jk} + \lambda R_{ij}\left(\beta_j \delta_{ik} + R_{ik} \beta_i \delta_{jk}\right)$$

Note the emergence of a kronecker-delta which arises since we are differentiating with respect to an arbitrary parameter. Using the symmetry of the kernel $$ R $$ we write this as

$$\frac{\partial l}{\partial \beta_k} = -2(Y_i - X_{ij}\beta_j)X_{ik} + 2 \lambda R_{ij}\beta_j \delta_{ik} + 2R_{ik} \beta_i$$

Since this is the $$ k $$ component of the gradient, we can restore this as a vector equation:

$$ \nabla l(\beta) = -2(X^T Y - (X^T X + \lambda R)\beta))$$

Setting this to zero:

$$\beta = (X^T X + \lambda R)^{-1}(X^T Y)$$

As we can see, the Einstein Summation Convention allowed us deploy our usual differentiation techniques without having to recall special identities and relations. Moreover, it is even applicable to tensors beyond 2x2 matrices such as tensor networks found in artifical neural networks. 

### Example 3: Reading ANOVA, t-tests, and AIC (fix later)

In the real world, you can use any model your heart desires. But when it comes to deployment, which model should you choose? You can choose a parametric linear model with 2, 3, 4, or 10 parameters. You can even choose a non-parametric model such a a random forest or artifical neural network. The advantage of a parametric model is that we can obtain rigorous confidence intervals under small dispersion asymptopics. 

Let's consider 2 models: the slope + intercept versus intercept only. When performing the linear regression, we values for each parameter $$ \beta $$ involved:
1. The estimate
2. Standard error
3. t-value
4. $$ \mathbb{P}(>|t|) $$

The estimate is obtained via MLE. The standard error provides us with an interval. The t-value tells us how much the estimate varies from the null hypothesis (i.e., how many standard deviations away it is from 0). The associated p-value tells us the likelihood of observing the estimated paramter under the null hypothesis. Let's do this with an example.

Suppose that slope statistics are:
1. $$ \beta = 5 $$
2. $$ \sigma = 1 $$
3. $$ t = \frac{\beta - 0}{\sigma} = 5 $$
4. $$ \mathbb{P}{(z>|t|)} = \mathbb{P}(z>|t|) = 2(1-\Phi(\tfrac{t}{2})) $$

If the probability is low, then we gain confidence that this covariate is important in our model.

We can also compute the AIC/BIC, which incorporate MLE estimation + a complexity penalty. The one with the lower AIC/BIC will be the "better" model to deploy. 

$$ AIC = 2p - 2 \ln{\hat{L}} $$

where $$ p $$ is the number of parameters in our model and $$ \hat{L} $$ is the maximum value of our likelihood function for the model.


We can also compute the anova table between two models. It will compute likelihood ratio test between the null hypothesis (intercept only model) vs. alternate hypothesis (slope + intercept). Let $$ RSS_1, RSS_0 $$ be the **residual sum of squares** for the alternate and null hypothesis. The $$ T $$ statistic, a measurement of how much variability is accounted for between a restricted and non-restricted model is then:

$$ T = \frac{RSS_1 - RSS_0}{RSS_1 / df} $$

where $$ df = n - p $$ is the degrees of freedom. In this case $$ p = 2 $$. 
