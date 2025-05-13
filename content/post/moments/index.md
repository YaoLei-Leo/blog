+++
date = '2025-05-13T00:53:25+08:00'
draft = false
title = 'Moments in Probability'
math = true
tags = ['Moments']
image = "Minecraft_DH.png"
+++

## Moments in Probability

For a random variable $X$, The $n$-th moments of $X$ is the expectation of $X^n$, which is $\mathbb{E}[X^n]$.


Why we need moment? Let’s starts with some measures we often use to describe a distribution.

**Mean:** $\mu=\mathbb{E}[X]$. *Mean* measures the central tendency. It tells us something about the center of a distribution. It is the $1$-th moment of $X$.

**Variance:** $\sigma=\mathbb{E}[X-\mu]^2$, *Variance* measures of dispersion. It is a measure of how far a set of numbers is spread out from their average value. It is the $2$-nd moment of $X-\mu$.

**Skewness:** $Skew(X)=\mathbb{E}[\frac{X-\mu}{\sigma}]^3$. *Skewness* measures the level of asymmetry level of a distribution. It is the $3$-rd moment of standardized $X$.

**Kurtosis:**: $Kurt(X)=\mathbb{E}[\frac{X-μ}{σ}]^4-3$. *Kurtosis* measures the tail’s heavy level of a distribution. It is the $4$-th moment of standardized $X$. The reason for subtracting 3 is to make any Normal distribution have kurtosis of 0.

As we can see from the example, moment could be used to measure the characteristics of distributions.

## Sample moments

In previous section, we used some examples to introduce the moment, and why we need it. We used $\mathbb{E}[X]$, which is the $1$-st moment of $X$, to represent the mean. Back to primary school, we were taught to use $\bar{X}=\frac{1}{n}\sum_{i=1}^nx_i$ to calculate the mean of a observed data. For example, if we observe a list of $[1,3,4,2,2,6]$, the mean of this list would be $(1+3+4+2+2+6)/6=3$. Here is the question, what is the difference between $\mathbb{E}[X]$ and $\bar{X}$?

In probability, we use $\mathbb{E}[X]$ to represent the mean of a random variable $X$. In statistics, we use $\bar{X}$ to represent the mean of a observed data (sampled data, also called sample). $\mathbb{E}[X]$ is the population mean of a random variable. Let's say $X \backsim N(0,1)$, then the $\mathbb{E}[X]$ is equal to $0$. While $\bar{X}$ is the sample mean of a observed data. In the real situation, we can only observe a sample of $X$, not the whole population. Therefore, the $\bar{X}$ calculated from $\frac{1}{n}\sum_{i=1}^nx_i$ might not eactly equal to $0$. As the sample mean $\bar{X}$ is an estimate of the population mean $\mathbb{E}[X]$.

Similarly, the sample variance is defined as:
$$ S_n^2=\frac{1}{n-1}\sum_{i=1}^n(x_i-\bar{x})^2 $$
The sample variance $S_n^2$ is an estimate of the population variance $\sigma^2$. The sample variance is an unbiased estimator of the population variance. The reason for using $n-1$ instead of $n$ is to make the sample variance an unbiased estimator of the population variance. If we use $n$, then the sample variance would be biased.

Similarly, we can define the *sample skewness* as:
$$ S_n^3=\frac{1}{n}\sum_{i=1}^n(\frac{x_i-\bar{x}}{S_n})^3 $$
and the *sample kurtosis* as:
$$ S_n^4=\frac{1}{n}\sum_{i=1}^n(\frac{x_i-\bar{x}}{S_n})^4-3 $$

## Moment generating functions
**Theorem** (Moment via derivatives of the MGF). The moment generating function (MGF) of a random variable $X$ is defined as:
$$ M_X(t)=\mathbb{E}[e^{tX}] $$
Given the MGF of $X$, we can get the $n$-th moment of $X$ by taking the $n$-th derivative of the MGF and evaluating it at $t=0$: $$\mathbb{E}[X^n]=M^{(n)}(0)$$

*Proof*. 

1. Using Taylor expansion of $M_X(t)$ around $t=0$:
$$M_X(t)=\mathbb{E}[e^{tX}]=\sum_{n=0}^\infin M^{(0)}(0)\frac{t^n}{n!} \tag{1}$$

2. Using Power series expansion of $e^{tX}$:
$$e^{tX}=\sum_{n=0}^\infin \frac{(tX)^n}{n!}=\sum_{n=0}^\infin \frac{t^nX^n}{n!}$$

3. So the expectation of $e^{tX}$ is:
$$\mathbb{E}[e^{tX}]=\sum_{n=0}^\infin \frac{t^n}{n!}\mathbb{E}[X^n] \tag{2}$$

4. Comparing (1) and (2), we can get:
$$\mathbb{E}[X^n]=M^{(n)}(0)$$

This theorem is suprising in that for a continuous random variable $X$, to compute moments would seemingly require doing integrals with LOTUS, but with the MGF, it is possible to find moments by taking derivatives rather than doing integrals.