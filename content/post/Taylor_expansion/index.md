+++
date = '2025-05-13T20:14:20+08:00'
draft = false
title = 'Taylor Expansion / Series and Power Series'
math = true
tags = ['Expansion', 'Series']
image = "Figure.jpg"
+++

## Taylor Expansion / Series
In mathematics, the Taylor expansion / series of a function is an infinite sum of terms that are expressed in terms of the function's derivatives at a single point. For most common functions, the function and the sum of its Taylor series are equal near this point.

Suppose $f(x)$ is a real or composite function, which is a differentiable function of a neighborhood of the point $a$. The Taylor series of $f(x)$ about the point $a$ is given by:

$$f(x)=f(a)+\frac{f^{\prime}(a)}{1!}(x-a)+\frac{f^{\prime\prime}(a)}{2!}(x-a)^2+\frac{f^{\prime\prime\prime}(a)}{3!}(x-a)^3+\dots$$

Where $n!$ denotes the factorial of $n$. In the more compact sigma notation, this can be written as:
$$f(x)=\sum_{n=0}^\infin\frac{f^{(n)}(a)}{n!}(x-a)^n$$

**Example**: the power series for $e^x$ is:
$$e^x=\sum_{n=0}^\infty \frac{x^n}{n!}$$

*Proof.*
1. As the derivative of $e^x$ is itself:
$$f^{(n)}(x)=e^x$$

2. Taking the derivative at $x=0$:
$$f^{(n)}(0)=e^0=1$$

3. Using Taylor expansion, set $a=0$:
$$f(x)=\sum_{n=0}^\infin\frac{f^{(n)}(a)}{n!}(x-a)^n=\sum_{n=0}^\infin\frac{x^n}{n!}$$

**In summary**

Taylor expansion is a way to **approximate** a function using infinitely many polynomial terms.

## Power Series
A power series is an infinite series of the form:
$$\sum_{n=0}^\infty a_n(x-a)^n$$

Where:
 - $a_n$ are the coefficients of the series
 - $x$ is the variable
 - $a$ is a constant.

**Example**: the power series for $sin(x)$ is:
$$sin(x)=\sum_{n=0}^\infin\frac{(-1)^nx^{2n+1}}{(2n+1)!}=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\frac{x^7}{7!}+\frac{x^9}{9!}-\frac{x^11}{11!}+\dots$$

*Proof.*
1. Using the Taylor expansion with $a=0$:
$$f(x)=sin(x)=\sum_{n=0}^\infin\frac{f^{(n)}(0)}{n!}(x)^n$$

2. Compute the derivatives of $sin(x)$ at $x=0$:
$$f(0)=sin(0)=0$$
$$f^{(1)}(0)=cos(0)=1$$
$$f^{(2)}(0)=-sin(0)=0$$
$$f^{(3)}(0)=-cos(0)=-1$$
$$f^{(4)}(0)=sin(0)=0$$
$$f^{(5)}(0)=cos(0)=1$$
$$f^{(6)}(0)=-sin(0)=0$$
$$f^{(7)}(0)=-cos(0)=-1$$
$$\dots$$
You can see that only the odd derivatives are non-zero, and they alternate in sign.

3. Plug into the Taylor expansion:
$$f(x)=\sum_{n=0}^\infin\frac{f^{(n)}(0)}{n!}(x)^n=\sum_{n=0}^\infin\frac{(-1)^nx^{2n+1}}{(2n+1)!}$$

**In Summary**
- Every Taylor series is a power series, but not every power series is a Taylor series.
- Power series serve as a broad framework, while Taylor series are tailored (pun intended!) to approximate specific functions using their derivatives.
- The convergence of a Taylor series to its function depends on the function being analytic (i.e., equal to its Taylor series in some neighborhood).