---
layout: blog
title: The Pisano period of C-finite sequences
date: 2024-10-21 19:54:25
tags:
mathjax: true
---

## Problem definition
The Pisano period of a prime $p$, is defined as the minimum integer $\pi(p)$ satisfying $f_0\equiv f_{\pi(p)},f_1\equiv f_{\pi(p)+1}(\operatorname{mod} p)$, where $f$ is the Fibonacci sequence. It is well known that for $p\not=2,5$, $\pi(p)$ is either a divisor of $p-1$ or $2p+2$. In this article, we extend this conclusion to any C-finite sequence of the formulae $f_n\equiv af_{n-1}+f_{n-2}(\operatorname{mod} p)$, where $a\in\mathbb{Z}_p$ is a constant.

## Closed form expression

Assume $f_n$ has a general form $r^n$. Then we rewrite the recursive formulae as $r^n\equiv ar^{n-1}+r^{n-2}$, which yields a characteristic equation $r^2-ar-1\equiv 0$. Let $\lambda_1,\lambda_2$ be the characteristic roots. Assume $f_0=0,f_1=1$, W.L.O.G., We claim that:
$$f_n\equiv\frac{\lambda_1^n-\lambda_2^n}{\lambda_1-\lambda_2}$$

Proof: since $f_{n-1}\equiv\frac{\lambda_1^{n-1}-\lambda_2^{n-1}}{\lambda_1-\lambda_2}$ and $f_{n-2}\equiv\frac{\lambda_1^{n-2}-\lambda_2^{n-2}}{\lambda_1-\lambda_2}$,

$$
\begin{aligned}
af_{n-1}+f_{n-2}&\equiv\frac{a\lambda_1^{n-1}-a\lambda_2^{n-1}+\lambda_1^{n-2}-\lambda_2^{n-2}}{\lambda_1-\lambda_2}\\\\\\
&\equiv\frac{\lambda_1^{n-2}(a\lambda_1+1)-\lambda_2^{n-2}(a\lambda_2+1)}{\lambda_1-\lambda_2}\\\\\\
&\equiv\frac{\lambda_1^n-\lambda_2^n}{\lambda_1-\lambda_2}\\\\\\
&\equiv f_n
\end{aligned}
$$

## Pisano period
As aforementioned, the characteristic roots should satisfy $r^2-ar-1\equiv 0$ or $(2r-a)^2\equiv a^2+4(\operatorname{mod}p)$. If $\exists w\in\mathbb{Z}_p$ such that $w^2\equiv a^2+4(\operatorname{mod} p)$, it is straightforward to derive $2\lambda_1-a\equiv w$ and $2\lambda_2-a\equiv-w$ and thus $\lambda_1,\lambda_2\in\mathbb{Z}_p$. Then by Fermat's little theorem, $\lambda_1^{p-1}\equiv\lambda_2^{p-1}\equiv 1$ and:

$$f_{n+p-1}\equiv\frac{\lambda_1^{n+p-1}-\lambda_2^{n+p-1}}{\lambda_1-\lambda_2}\equiv\frac{\lambda_1^n-\lambda_2^n}{\lambda_1-\lambda_2}\equiv f_{n}$$

which implies that the Pisano period $\pi(p)|(p-1)$.

If $\not\exists w\in\mathbb{Z}_p$ such that $w^2\equiv a^2+4(\operatorname{mod} p)$, we claim that $\pi(p)|(2p+2)$.

Proof: since $\lambda_1,\lambda_2$ are the roots of the equation $r^2-ar-1\equiv 0$, $\lambda_1+\lambda_2\equiv a$ and $\lambda_1\lambda_2\equiv -1$.

$$(\lambda_1+\lambda_2)^p\equiv \lambda_1^{p}+\lambda_2^p\equiv a^p$$

Let $w=2\lambda_1-a$. Then:

$$(w+a)^p2^{-p}+\lambda_2^p\equiv a^p$$

Note that $\lambda_1,\lambda_2,w\not\in\mathbb{Z}_p$ and $2,a\in\mathbb{Z}_p$. Therefore, $\left(2^{-1}\right)^{p-1}\equiv a^{p-1}\equiv 1$ by Fermeat's little theorem:

$$
\begin{aligned}
&\quad (w+a)^p+2\lambda_2^p\equiv 2a^p\\\\\\
&\Rightarrow w^p+2\lambda_2^p\equiv a^p\equiv a\\\\\\
&\Rightarrow \lambda_2^p\equiv 2^{-1}(a-w^p)
\end{aligned}
$$

By [quadratic reciprocity](https://en.wikipedia.org/wiki/Quadratic_reciprocity), $w^{p-1}\equiv (a^2+4)^{\frac{p-1}{2}}\equiv -1$, then:

$$\lambda_2^p\equiv2^{-1}(a+w)\equiv \lambda_1$$

Then $\lambda_2^{p+1}\equiv \lambda_1\lambda_2\equiv -1$ and $\lambda_2^{2p+2}\equiv 1$. Similarly, we can prove $\lambda_1^{2p+2}\equiv 1$ by assuming $w=2\lambda_2-a$. Therefore:

$$f_{n+2p+2}\equiv\frac{\lambda_1^{n+2p+2}-\lambda_2^{n+2p+2}}{\lambda_1-\lambda_2}\equiv\frac{\lambda_1^n-\lambda_2^n}{\lambda_1-\lambda_2}\equiv f_n$$