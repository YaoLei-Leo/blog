+++
date = '2025-05-14T14:35:45+08:00'
draft = false
title = 'Change_of_variables'
math = true
tags = ['Change of variables']
image = "House.png"
+++

**Theorem** (Change of variables in one dimension) Let $X$ be a random variable with PDF $f_X$, and let $Y=g(X)$, where $g$ is differentiable and monotonic. Then the PDF of $Y$ is given by:
$$f_Y(y)=f_X(x)|\frac{dx}{dy}|$$
where $x=g^-1(y)$. The support of Y is all $g(x)$ with $x$ in the support of $X$.

*Proof.*
1. Suppose g is strictly increasing. Then, for $y=g(x)$, the CDF of $Y$ is:
$$F_Y(y)=P(Y\leq y)=P(g(X)\leq y)=P(X\leq g^-1(y))=F_X(g^-1(y))=F_X(x)$$

Therefore, the PDF of $Y$ is
$$f_Y(y)=\frac{d}{dy}F_Y(y)=\frac{d}{dy}F_X(x)=\frac{dx}{dy}\frac{d}{dx}F_X(x)=f_X(x)\frac{dx}{dy}$$

2. Suppose g is strictly decreasing. Then, for $y=g(x)$, the CDF of $Y$ is:
$$F_Y(y)=P(Y\leq y)=P(g(X)\leq y)=P(X\geq g^-1(y))=1-P(X\leq g^-1(y))=1-F_X(g^-1(y))=1-F_X(x)$$
Therefore, the PDF of $Y$ is
$$f_Y(y)=\frac{d}{dy}F_Y(y)=-\frac{d}{dy}F_X(x)=-\frac{dx}{dy}\frac{d}{dx}F_X(x)=-f_X(x)\frac{dx}{dy}$$
In this case, the $\frac{dx}{dy}$ is negative, so we can write:
$$f_Y(y)=f_X(x)|\frac{dx}{dy}|$$
3. Combine the two cases:
$$f_Y(y)=f_X(x)|\frac{dx}{dy}|$$
where $x=g^-1(y)$. The support of Y is all $g(x)$ with $x$ in the support of $X$.