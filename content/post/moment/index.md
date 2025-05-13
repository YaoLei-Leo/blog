+++
date = '2025-05-13T00:53:25+08:00'
draft = false
title = 'Moment'
math = true
tags = ['Moment']
image = "Minecraft_DH.png"
+++

For a random variable $X$, The $n$-th moments of $X$ is $E(X^n)$. Why we need moment? Let’s starts with the measurements used in describing a distribution.
- The mean, which is $\textstyle\sum_{j=1}^n m_jx_j$ , is called a measure of central tendency because it tells us something about the center of a distribution. It is the $1$-th moment of random variable X.

- The variance of a distribution, which is $Var(X)=\textstyle\sum_{j=1}^n m_j(x_j-E(X))^2$, is a measure of dispersion, meaning it is a measure of how far a set of numbers is spread out from their average value. It is the $2$-nd moment of random variable $X-μ=X-E(X)$. 

- The skewness of a distribution, which is $Skew(X)=E(\frac{X-μ}{σ})^3$, measures the level of asymmetry level of a distribution. It is the $3$-rd moment of standardized random variable $\frac{X-μ}{σ}$.

- The kurtosis of a distribution, which is $Kurt(X)=E(\frac{X-μ}{σ})^4-3$, measures the tail’s heavy level of a distribution. It is the $4$-th moment of standardized random variable $\frac{X-μ}{σ}$. The reason for subtracting 3 is to make any Normal distribution have kurtosis of 0. 

The answer is very clear now, the reason we define moment for random variable is, it could be used to measure and compare the characteristics of distributions.