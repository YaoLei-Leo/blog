+++
date = '2025-05-14T15:10:48+08:00'
draft = false
title = 'LOTUS'
math = true
tags = ['LOTUS']
image = "windmill.png"
+++

## Definition of expectation
**Definition (Expectation of a discrete random variable)** 
1. The expected value of a discrete random variable $X$ whose distinct possible values are $x_1, x_2, \ldots$ is defined by
$$\mathbb E[X] = \sum_{i} x_i P(X = x_i) = \sum_{i} x_i f_X(x_i)$$
where $f_X(x)$ is the probability mass function of $X$.

2. The expected value of a continuous random variable $X$ is defined by
$$\mathbb E[X] = \int_{-\infty}^{\infty} x f_X(x) dx$$
where $f_X(x)$ is the probability density function of $X$.


## Law of unconscious statistician (LOTUS)

**Theorem (LOTUS)** 
1. If $X$ is a discrete random variable, and $g$ is a function from $\mathbb R$ to $\mathbb R$. If $Y=g(X)$, then
$$\mathbb E[Y] = \mathbb E[g(X)] = \sum_{x} g(x) P(X = x) = \sum_{x} g(x) f_X(x)$$
where $f_X(x)$ is the probability mass function (PMF) of $X$.

2. If $X$ is a continuous random variable, and $g$ is a function from $\mathbb R$ to $\mathbb R$. If $Y=g(X)$, then
$$\mathbb E[Y] = \mathbb E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x) dx$$
where $f_X(x)$ is the probability density function (PDF) of $X$.

## Why LOTUS?
**Example 1**

Let:
- $X \sim Exponential(\lambda)$
- $Y=log(X)$

If we use the definition of expectation to calculate $\mathbb E[Y]$, we can first calculate the PDF of $Y$:
$$f_Y(y) = \frac{d}{dy} P(Y \leq y) = \frac{d}{dy} P(X \leq e^y) = \frac{d}{dy} (1 - e^{-\lambda e^y})$$
$$= \lambda e^{-\lambda e^y} e^y = \lambda e^{-\lambda e^y + y}$$

Then we can calculate $\mathbb E[Y]$:
$$\mathbb E[Y] = \int_{-\infty}^{\infty} y f_Y(y) dy = \int_{-\infty}^{\infty} y \lambda e^{-\lambda e^y + y} dy$$

However, LOTUS could make it easier:
$$\mathbb E[Y] = \mathbb E[log(X)] = \int_{0}^{\infty} log(x) \lambda e^{-\lambda x} dx$$

**Example 2**

Let:
- $X \sim N(0,1)$
- $Y = sin(X)$

If we use the definition of expectation to calculate $\mathbb E[Y]$, we can first calculate the PDF of $Y$:
$$f_Y(y) = \frac{d}{dy} P(Y \leq y) = \frac{d}{dy} P(X \leq sin^{-1}(y))$$
However, there’s no closed-form PDF for $Y$ as we cannot write the analytic form of $sin^{-1}(y)$. It’s a complicated, oscillatory transformation of a normal variable. You can’t write down $f_Y(y)$ analytically. Consequently, we cannot calculate $\mathbb E[Y]$ using the definition of expectation.

However, we can use LOTUS:
$$\mathbb E[Y] = \mathbb E[sin(X)] = \int_{-\infty}^{\infty} sin(x) f_X(x) dx = \int_{-\infty}^{\infty} sin(x) \frac{1}{\sqrt{2\pi}} e^{-\frac{x^2}{2}} dx$$
This is a analytically solvable integral. The result is $0$ because the integrand is an odd function and the limits are symmetric about $0$.

## In summary
- LOTUS is a powerful tool for calculating the expected value of a function of a random variable.
- It allows us to avoid the need to find the PDF of the transformed variable.
- It can simplify the calculation of expected values for complex transformations.
- It is applicable to both discrete and continuous random variables.