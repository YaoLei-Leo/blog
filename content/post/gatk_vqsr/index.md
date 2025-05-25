+++
date = '2025-05-24'
draft = false
title = "Bayes' Theory and Bayesian Inference"
math = true
tags = ['Variantional Inference']
image = ""
+++

## Law of total probability
Let's say we have a set of mutually exclusive probable events $\{B_i : i=1,2,3,...,n \}$. The sum of the probabilities of these events is equal to 1, i.e. $$\sum_i P(B_i)=1$$

Now, if we have another event $A$, we can express the probability of $A$ in terms of the probabilities of $B_i$ and the conditional probabilities of $A$ given $B_i$. This is known as the law of total probability:
$$P(A)=\sum_i P(A|B_i)P(B_i)$$

Here, as the sum of the probabilities of $B_i$ is equal to 1. The event $A$ must happen in at least one of the $B_i$ events, or the $P(A)$ is equal to 0. We can understand this as the probability of $A$ is the sum of the probabilities of $A$ happening in each of the mutually exclusive events $B_i$.

## Bayes' rule
For any specific event $B_j$, the probability of both event $A$ and $B_j$ happending is $$P(A,B_j)=P(A|B_j)P(B_j)$$

Also, we can express the same probability in terms of the conditional probability of $B_j$ given $A$:
$$P(A,B_j)=P(B_j|A)P(A)$$

Therefore, we can write get this formula:
$$P(A,B_j)=P(A|B_j)P(B_j)=P(B_j|A)P(A)$$

Here comes the Bayes' rule:
$$P(A|B_j)=\frac{P(B_j|A)P(A)}{P(B_j)} \tag{1}$$
$$or$$
$$P(B_j|A)=\frac{P(A|B_j)P(B_j)}{P(A)}$$

Using the formula (1) as example, we call the $P(A)$ as the prior probability of event $A$ happening. The $P(A|B_j)$ is the posterior probability of event $A$ given that event $B_j$ has happened. The $P(B_j|A)$ is the likelihood of event $B_j$ given that event $A$ has happened. The $P(B_j)$ is the marginal probability of event $B_j$.

## Bayesian inference
Bayesian inference is a method of statistical inference in which Bayes' theorem is used to update the probability for a hypothesis as more evidence or information becomes available. In Bayesian inference, we start with a prior distribution, which represents our beliefs about the parameters before observing any data. After observing the data, we update our beliefs using Bayes' rule to obtain the posterior distribution.

Using the formula (1) as example, $P(A)$ is the prior distribution of event $A$, when we represents our beliefs about the parameters before observing any data. The $P(B_j|A)$ is the likelihood of event $B_j$ given that event $A$ has happened. The $P(B_j)$ is the marginal distribution of event $B_j$. We update our beliefs about the $P(A)$ by observing the data $B_j$ and using Bayes' rule to get the posterior probability distribution $P(A|B_j)$.

There are many types of prior distributions, and also many types of likelihood functions. The choice of prior distribution and likelihood function depends on the problem at hand and the available data. Some combination of prior distribution and likelihood function can lead to a closed-form solution, which means we can derive the exact formula for the posterior distribution, while others may require numerical methods such as Markov Chain Monte Carlo (MCMC) to approximate the posterior distribution. Here, we first introduce the closed-form cases, and then introduce the numerical methods.

### Closed-form solutions: conjugate priors
#### Beta prior and binomial likelihood
The Beta distribution is a conjugate prior for the binomial likelihood. If we have a binomial likelihood $P(X=k|p)=\binom{n}{k}p^k(1-p)^{n-k}$, where $X$ is the number of successes in $n$ trials and $p$ is the probability of success, we can use a Beta prior $P(p|\alpha,\beta)=\frac{1}{B(\alpha,\beta)}p^{\alpha-1}(1-p)^{\beta-1}$, where $\alpha$ and $\beta$ are the shape parameters of the Beta distribution.

Using Bayes' rule, we can derive the posterior distribution:
$$P(p|X=k)=\frac{P(X=k|p)P(p)}{P(X=k)}$$
Substituting the binomial likelihood and Beta prior, we get:
$$P(p|X=k)=\frac{\binom{n}{k}p^k(1-p)^{n-k}\frac{1}{B(\alpha,\beta)}p^{\alpha-1}(1-p)^{\beta-1}}{P(X=k)} \tag{2}$$

The numerator of the equation (2) can be simplified as:
$$P(p|X=k)=\frac{1}{B(\alpha,\beta)}\binom{n}{k}p^{k+\alpha-1}(1-p)^{n-k+\beta-1}$$

Here, the posterior distribution is a function of $p$. The constant $\frac{1}{B(\alpha,\beta)}$, $(_k^n)$, and the $P(X=k)$ are all constants with respect to $p$. Therefore, we can first ignore them when we are only interested in the shape of the posterior distribution. Therefore, we can write the posterior distribution as:
$$P(p|X=k) \propto p^{k+\alpha-1}(1-p)^{n-k+\beta-1} \tag{3}$$

Here comes the magic part, the posterior distribution is similar to the PDF pf Beta distribution, with the shape parameters $\alpha' = k + \alpha$ and $\beta' = n - k + \beta$:
$$\beta(k+\alpha, n-k+\beta)=\frac{1}{B(k+\alpha,n-k+\beta)}p^{k+\alpha-1}(1-p)^{n-k+\beta}$$

But missing the Beta function $\frac{1}{B(k+\alpha,n-k+\beta)}$. Interestly, the formula (3) tells us that the posterior distribution is proportional to the $p^{k+\alpha-1}(1-p)^{n-k+\beta-1}$, the constant parts are ignored. In fact, the true posterior distribution should be:
$$P(p|X=k) = constant \cdot p^{k+\alpha-1}(1-p)^{n-k+\beta-1}$$

To get the constant. We can use the characteristics of a PDF that the integral of the PDF is equal to 1:
$$\int_0^1 P(p|X=k)dp = 1$$
This integral can be solved as: 
$$\int_0^1 p^{k+\alpha-1}(1-p)^{n-k+\beta-1}dp = B(k+\alpha, n-k+\beta)$$
Therefore, we can get the constant:
$$constant = \frac{1}{B(k+\alpha, n-k+\beta)}$$
Thus, the posterior distribution is:
$$P(p|X=k) = \frac{1}{B(k+\alpha, n-k+\beta)}p^{k+\alpha-1}(1-p)^{n-k+\beta-1}$$

Now, we can see that the posterior distribution is a Beta distribution with shape parameters $\alpha' = k + \alpha$ and $\beta' = n - k + \beta$. This is the closed-form solution for the posterior distribution when using a Beta prior and a binomial likelihood. And this is the reason why we call the Beta distribution a conjugate prior for the binomial likelihood.

#### Normal prior and normal likelihood