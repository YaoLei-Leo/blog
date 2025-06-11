+++
date = '2025-06-11'
draft = false
title = "Distributions in Statistics"
math = true
tags = ['Distribution']
image = "Minecraft_building.png"
+++

There are numerous distributions in statistics. The most famous one would be the norm distribution (Gaussian distribution). In this note, I will introduce them one by one, explain their characteristics, and their applications in data analysis.


# Indicator random variable
*Definition* The indicator random variable of an event $A$ is the random variable which equals 1 if $A$ occurs and 0 otherwise. We will denote the indicator random variable of $A$ by $I_A$ or $I(A)$.

# Bernouli distribution
**Definition** (Bernouli distribution) An random variable $X$ is said to have the *Bernouli distribution* with parameter $p$ if $P(X = 1) = p$ and $P(X = 0) = 1-p$, where $0<P<1$. We write this as $X ~ Bern(p)$.

# Binomial distribution

Suppose there are $n$ indepedent Bernouli trails are performed, each with same success probability $p$. Let $X$ be the number of successes. The distribution of $X$ is called the *Bionomial distribution* with parameters $n$ and $p$. We write $X \sim Bin(n,p)$ to mean that $X$ has the Bionomial distribution with parameters $n$ and $p$, where $n$ is a positive integer and $0<p<1$.

**Theorem** (Binomial PMF). If $X \sim Bim(n,p)$, then the PMF of $X$ is
$$P(X=k)=\binom{n}{k}p^k(1-p)^{n-k}$$
for $k=0,1,...,n$ (and $P(X=k)=0$ otherwise).

# Hypergeometric distribution
Consider an urn with $w$ white balls and $b$ black balls. We draw $n$ balls out of the urn at random without replacement, such that all $\binom{w+b}{n}$ samples are equally likely. Let $X$ be the number of white balls in the sample. Then $X$ is said to have the *Hypergeometric distribution* with paramters $w$, $b$, and $n$; we denote this by $X \sim HGeom(w,b,n)$.

**Theorem** (Hypergenometric PMF) If $X \sim HGeom(w,b,n)$, then the PMF of $X$ is
$$P(X=k)=\frac{\binom{w}{k}\binom{b}{n-k}}{\binom{w+b}{n}}$$
for integers $k$ satisfying $0 \le k \le w$ and $0 \le n-k \le b$, and $P(X=k)=0$ otherwise.