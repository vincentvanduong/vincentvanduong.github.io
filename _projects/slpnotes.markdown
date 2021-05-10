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