---
title: The XOR sum of 4x, 4x + 1, 4x + 2 and 4x + 3 is 0 for any non-negative integer x
date: 2024-09-02 21:19:05
tags:
mathjax: true
---
In this article, we would use $\oplus$ to represent the bitwise XOR operation between two integers. We observe that: for any $x\in\mathbb N$, $(4x)\oplus(4x+1)\oplus(4x+2)\oplus(4x+3)=0$, and therefore, $\bigoplus_{i=0}^{4y-1}i=0$ for any $\mathbb N^+$.

We now illustrate the formal proof of the above observation.

We firstly write $x$ into a binary format, i.e.:

$$x=a_0+2a_1+2^2a_2+\cdots+2^na_n=(a_na_{n-1}\cdots a_0)_2,a_i\in\lbrace 0,1\rbrace$$

Let $k=4x$. Then:

$$k=2^2a_0+2^3a_1+\cdots+2^{n+2}a_n$$

$$k+1=1+2^2a_0+2^3a_1+\cdots+2^{n+2}a_n$$

$$k+2=2+2^2a_0+2^3a_1+\cdots+2^{n+2}a_n$$

$$k+3=1+2+2^2a_0+2^3a_1+\cdots+2^{n+2}a_n$$


Then the binary formats of $k,k+1,k+2,k+3$ are:

$$k=(a_na_{n-1}\cdots 00)_2$$

$$k+1=(a_na_{n-1}\cdots 01)_2$$

$$k+2=(a_na_{n-1}\cdots 10)_2$$

$$k+3=(a_na_{n-1}\cdots 11)_2$$

Since the $(n+1)$ most significant bits of all aforementioned numbers are the same, the XOR sum of this part should be 0. For the latter bits, i.e., the 2 least significant bits, it is easy to compute that:

$$(00)\oplus(01)\oplus(10)\oplus(11)=(00)$$

Therefore, $k\oplus(k+1)\oplus(k+2)\oplus(k+3)=0$, and the proof is done.