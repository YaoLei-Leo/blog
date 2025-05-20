+++
date = '2025-05-14T15:10:48+08:00'
draft = false
title = 'Beta distribution'
math = true
tags = ['distribution']
image = "logcabin.jpg"
+++

## Beta distribution
The Beta distribution is a continuous distribution on the interval (0,1). It is a generalization of the Unif(0,1) distribution.

An random variable $X$ is said to have the Beta distribution with parameters $a$ and $b$, where $a,b > 0$, if its probability density function (PDF) is:

$$f(x)=\frac{1}{\beta(a,b)}x^{a-1}(1-x)^{b-1},\quad0<x<1$$

$\beta(a,b)$ is the beta function. It is a constant that chosen to make the PDF integrate to 1. We write this as $X \sim \text{Beta}(a,b)$.

Taking $a=b=1$, the $Beta(1,1)$ PDF is $f(x)=1$, which is same as the uniform distribution $Unif(0,1)$, the proof is shown below.

## Beta function
To make the PDF of Beta distribution integrate to 1. The constant $\beta(a,b)$ is defined as:

$$\beta(a,b)=\int_0^1 x^{a-1}(1-x)^{b-1}dx=\frac{(a-1)!(b-1)!}{(a+b-1)!}$$

$Proof.$
Let's use the induction to prove the above equation.
1. **Base Case:**

For $b=1$:
$$\beta(a,1)=\int_0^1x^{a-1}dx=\frac{1}{a}=\frac{(a-1)!(1-1)!}{(a+1-1)!}$$

2. **Recurrence Relation of the Beta Function:**

Using integration by parts on $\beta(a,b)$:
$$\beta(a,b+1)=\frac{b}{a+b}\beta(a,b)$$

3. **Inductive Step:**

Let's assume the formula holds for $b=k$, i.e., $\beta(a,k)=\frac{(a-1)!(k-1)!}{(a+k-1)!}$.

Then we have:
$$\beta(a,k+1)=\int_0^1 x^{a-1}(1-x)^{k}dx=\int_0^1 x^{a-1}(1-x)^{k}dx$$
As shown in 2, we can write:
$$\beta(a,k+1)=\frac{k}{a+k}\int_0^1 x^{a-1}(1-x)^{k-1}dx$$
$$=\frac{k}{a+k}\cdot\frac{(a-1)!(k-1)!}{(a+k-1)!}$$
$$=\frac{(a-1)!(k)!}{(a+k)!}$$
Thus, we have shown that if the formula holds for $b=k$, it also holds for $b=k+1$.

4. **Conclusion:**

By the principle of mathematical induction, the formula holds for all positive integers $b$. Symmetrically, we can also show that the formula holds for $a$ by using the same induction process.

## Beta-Binomial conjugacy
The Beta distribution is the conjugate prior of the Binomial distribution. This means that if we have a Binomial likelihood and a Beta prior, the posterior distribution will also be a Beta distribution.

Let's say we have a coin that we want to test for bias. We flip the coin $n$ times and observe $k$ heads. We can model this with a Binomial distribution, where the probability of heads is $p$. The likelihood function is given by:
$$P(X=k|p)=\binom{n}{k}p^k(1-p)^{n-k}$$
where $X$ is the number of heads observed in $n$ flips.
The likelihood function is a function of $p$, and it tells us how likely we are to observe $k$ heads given a particular value of $p$.


For example, if we have a Binomial likelihood with parameters $n$ and $k$, and a Beta prior with parameters $a$ and $b$, the posterior distribution will be:

$$f(p|X=k)=\frac{P(X=k|p)f(p)}{P(X=k)}=\frac{(_k^n)p^k(1-p)^{n-k}\cdot\frac{1}{\beta(a,b)}p^{a-1}(1-p)^{b-1}}{P(X=k)}$$
$$=\frac{(_k^n)p^k(1-p)^{n-k}\cdot\frac{1}{\beta(a,b)}p^{a-1}(1-p)^{b-1}}{\int_0^1P(X=k|p)f(p)dp}$$

It is difficult to calculate the denominator. Are we stucked here?

Acutally, the calculation is much easier than it appears. The conditional PDF $f(p|X=k)$ is a function of $p$, which means everthing that desn't depend on $p$ is a constant. We can drop all these constants and find the PDF up to a multiplicative constant (and then the normalizing constant is whatever it needs to make the PDF integrate to 1). We can drop the $(_k^n)$, $\frac{1}{\beta(a,b)},$ and the denominator $P(X=k)$. So we can write:

$$f(p|X=k)\propto p^{k+a-1}(1-p)^{n-k+b-1}$$

Which is very close to the PDF of a Beta distribution $Beta(a+k, b+n-k)$, up to a multiplicative constant. Therefore, we can conclude that the posterior distribution is:

$$f(p|X=k)\sim Beta(a+k, b+n-k)$$