---
layout: blog
title: Does nearest neighbor distance approach farthest neighbor distance in high-dimensional space?
date: 2026-03-10 15:39:54
tags:
mathjax: true
---

I was reading a classical [ANN paper](https://minds.wisconsin.edu/bitstream/handle/1793/60174/TR1377.pdf?sequence=1&isAllowed=y) that discusses the cases when the distance difference between the nearest neighbor and the farthest neighbor becomes negligible in high-dimensional space. In Section 3.5.3, it provides an interesting manually constructed example, but without detailed proof steps. I was writing this blog to complement the process.

**Problem:** Let $\vec X_m=(X_1,X_2,\cdots,X_m)$ be a random $m$-dimensional vector, such that $X_1=U_1$ and $X_i=U_i+X_{i-1}/2$, where $U_i\sim \text{Uniform}(0,\sqrt{i})$ is a continuous uniform random variable. Now, we sample two random vectors $\vec P_m,\vec Q_m$ independently from the distribution of $\vec X_m$. What is the expected $L_2$ distance and variance of distance between $\vec P_m$ and $\vec Q_m$?

The conclusion in the paper is $\frac{1}{9}m^2+\frac{1}{3}m+o(m)$, but my results show the more accurate form should be $\frac{1}{9}m^2+\frac{1}{27}m+o(m)$.

**Solution:** The expected distance between $\vec P_m$ and $\vec Q_m$ could be computed as follows:

$$
E\left[||\vec P_m-\vec Q_m||_2^2\right]=E\left[\sum_{i=1}^m (P_i-Q_i)^2\right]=\sum_{i=1}^m E\left[(P_i-Q_i)^2\right]
$$

Since $Var(P_i-Q_i)=E[(P_i-Q_i)^2]-(E[P_i-Q_i])^2$ and $E[P_i-Q_i]=0$, the above formulae transforms to solving:

$$Var(P_i-Q_i)=Var(P_i)+Var(Q_i)-2Cov(P_i,Q_i)=2Var(X_i)$$

Note that $Cov(P_i,Q_i)=0$ by independence. Then, our next step is to compute $Var(X_i)$.

It is not hard to see $X_{i-1}$ and $U_i$ are independent. Therefore, $Var(X_i)=Var(U_i)+Var(X_{i-1})/4$. Since $Var(U_i)=i/12$, we have $Var(X_i)=i/12+Var(X_{i-1})/4$. By solving the above recurrence relation, we have:

$$Var(X_i)=\frac{1}{27}(1/4)^i+\frac{1}{9}i-\frac{1}{27}$$

How to solve the recurrence (I do not know how, following is GPT's answer but I verified):

- We first solve the homogeneous part of the recurrence, which is $Var(X_i)=Var(X_{i-1})/4$. The characteristic equation for this homogeneous part is $r=1/4$, so the general solution to the homogeneous part is $C(1/4)^i$ for some constant $C$.

- Next, we find a particular solution to the non-homogeneous recurrence. We can try a particular solution of the form $Var(X_i)=A*i+B$ for some constants $A$ and $B$. Substituting this into the original recurrence gives us:

$$
\begin{align}
&\quad A*i+B = \frac{1}{12}i + \frac{1}{4}(A*(i-1)+B)
\\&\Rightarrow A*i+B=\left(\frac{1}{12}+\frac{1}{4}A\right)i+\frac{1}{4}(B-A)
\end{align}
$$

- We need to match the coefficients of $i$ and the constant terms on both sides of the equation. This gives us the following system of equations:

$$
\begin{cases}
A=\frac{1}{12}+\frac{1}{4}A
\\
B=\frac{1}{4}(B-A)
\end{cases}
$$

- Then $A=\frac{1}{9}$ and $B=-\frac{1}{27}$. So the non-homogeneous solution is $Var(X_i)=\frac{1}{9}i-\frac{1}{27}$.

- Putting everything together, the general solution to the original recurrence is $Var(X_i)=C(1/4)^i+\frac{1}{9}i-\frac{1}{27}$. Since $Var(X_1)=1/12$, we can solve for $C$ to get $C=\frac{1}{27}$. Therefore, the final solution to the recurrence is:

$$Var(X_i)=\frac{1}{27}(1/4)^i+\frac{1}{9}i-\frac{1}{27}$$

Now back to our goal, we need to summarize $2Var(X_i)$ for $i=1,2,\cdots,m$ to get the expected distance between $\vec P_m$ and $\vec Q_m$:

$$
\begin{align}
E\left[\|\vec P_m-\vec Q_m\|_2^2\right]&=\sum_{i=1}^m 2Var(X_i)=\frac{2}{81}\left(1-\frac{1}{4^m}\right)+\frac{1}{9}m(m+1)-\frac{2}{27}m\\&=\frac{1}{9}m^2+\frac{1}{27}m+o(m)
\end{align}
$$

I am not writing the variance of distance here since it is much more complicated. Anyway, the difference of our results does not affect the main conclusion of the paper.