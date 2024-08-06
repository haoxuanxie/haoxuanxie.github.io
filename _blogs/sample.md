---
layout: blogs
title: Introduction to Abstract Algebra
date: 2024-08-05
categories: blog
---

(This is a sample blog post for testing.)

Abstract algebra is about generalization of number systems, e.g.:

$$\mathbb{Z}=\left\{\cdots,-1,0,1,\cdots\right\}$$

$$\mathbb{Q}=\left\{\frac{m}{n}|m\in\mathbb{Z},n\in\mathbb{Z}\backslash\left\{0\right\}\right\}$$

$$\mathbb{R}=\text{real numbers}$$

$$\mathbb{C}=\left\{x+iy|x,y\in\mathbb{R}\right\}$$

which are closed under addition and multiplication with nice properties:

(A1) $(a+b)+c=a+(b+c)$;

(A2) $(ab)c=a(bc)$;

(C1) $a+b=b+a$;

(C2) $ab=ba$;

(D1) $a(b+c)=ab+ac$;

(D2) $(a+b)c=ac+bc$.

Goal: for different "number systems", find out their common features and obtain theorems that hold for all of these generalized "number systems".

**Remark:** for matrices, (C2) property does not hold.

[TOC]

## Modular Arithmetic
**Definition:**

$$\mathbb{Z}_n:=\left\{0(\operatorname{mod} n), 1(\operatorname{mod} n),\cdots, n-1(\operatorname{mod}n)\right\}$$

or:

$$
\mathbb{Z}_n:=\left\{[0],[1],\cdots,[n-1]\right\}
$$

**Properties:**

- Addition: $[a]+[b]=\text{remainder of }(a+b)/n$;
- Multiplication: $[a]\cdot[b]=\text{remainder of }ab/n$.

## Binary Operation
**Definition:** Let $S$ be a set. A **binary operation** on $S$ is a map:

$$*:S\times S\to S$$

Let $T\subseteq S$ be a subset. We say the binary operation is **closed** in $T$ if for all $a,b\in T$, $a*b\in T$. i.e. $(T,*)$ is closed in $(S,*)$.

**Remark:** If $W\leq\mathbb{R}^n$ is a vector subspace, then $(W,+)$ is closed in $(\mathbb{R}^n,+)$.

## Group
**Definition:** A **group** $G$ is a set along with a binary operation $*:G\times G\to G$ satisfying:

(1) $(a*b)*c=a*(b*c),\forall a,b,c\in G$ (associative);

(2) $\exists e\in G, s.t. e*a=a*e=a,\forall a\in G$ (identity);

(3) $\forall a\in G$, there exists $b\in G$ such that $a*b=b*a=e$ (inverse, $b$ is often written as $a^{-1}$).

**Remark:** 

1. $(\mathbb{Z},-)$ is not a group (properties 1, 2 are violated). $(\mathbb Q^*,\times), (\mathbb R^*,\times), (\mathbb C^*,\times)$ are groups, where $*$ excludes 0.
2. $(M_{2\times 2}(\mathbb{R}),+)$ is a group. Let: 
$$GL(2,\mathbb{R})=\left\{a\in M_{2\times 2}(\mathbb{R})|\exists a^{-1}\right\}$$
then $(GL(2,\mathbb{R}),\times)$ is a group.
3. $(\mathbb{Z}_n,+)$ is a group, where $e=[0]=0(\operatorname{mod} n)$. $(\mathbb{Z}_n,\times)$ is not a group. However, let:
$$\mathbb{Z}_n^*:=\left\{[a]\in\mathbb{Z}_n|\gcd(a,n)=1\right\}$$
denoted as **the units in** $\mathbb{Z}_n$. Then $(\mathbb{Z}_n^*,\times)$ is a group.

**Remark:** (1) When there is no confusion, we will write $a*b$ as $ab$; (2) $*$ is not necessary to be commutative, and we say $(G,*)$ is **abelian** if $*$ is commutative.

## *Magma, Semigroups, Monoids
**Definition:** A **monoid** is the structure when we delete inverse property from the group operations and axions (e.g. $(\mathbb{N},+)$). A **semigroup** is the structure when we delete identity property from the monoid operations and axioms. A **magma** is the structure when we delete associativity from the semigroup axiom.

## Basic Properties of Groups
**Proposition:** Let $(G,*)$ be a group. Then:

(a) The identity element is unique: if $ae=ea=a$ and $ae'=e'a=a$ for all $a$, then $e=e'$;

(b) For each $g\in G$, $g^{-1}$ is unique;

(c) For each $a\in G$, the elements $\left\{ag|g\in G\right\}$ are distinct.

**Proof.** (a) Suppose $ae=ea=a,ae'=e'a=a,\forall a$, let $a=e'$ and $a=e$, respectively:

$$e'e=ee'=e',ee'=e'e=e$$

Then $e=e'$.

(b) Suppose $gh=hg=e,gh'=h'g=e$ for some $g$, then:

$$hgh'=eh'=h'\Rightarrow he=h=h'$$

(c) Suppose $ag=ag'$,

$$a^{-1}(ag)=a^{-1}(ag')\Rightarrow g=g'$$

**Remark:** For (c), $\left\{ga|g\in G\right\}$ has distinct elements as well.

## Order
**Definition:** The **order** of a group $G$, noted as $ord(G)$ or $|G|$, is the number of elements in $G$. If $|G|<\infty$, then $G$ is a **finite group**.

## Cayley Table
**Definition:** The rows and columns of **Cayley table** are labelled by elements in $G(|G|<\infty)$. The $(a,b)$ entry of the table is given by $a*b$.

**Proposition:** The rows and columns of a Cayley table of $(G,*)$ have distinct entries, which contains all elements in $G$.

**Remark:** For $|G|=4$, there are essentially 2 Cayley talbes, one from $(\mathbb{Z}_8^*,\times)$, another from $(\mathbb{Z}_4,+)$.

**Theorem:** If $|G|=4$, then $G$ is **isomorphic** to $(\mathbb{Z}_8^*,\times)$ or $(\mathbb{Z}_4,+)$.

## Subgroups
**Definition:** Let $(G,*)$ be a group. A nonempty subset $H\subseteq G$ is a **subgroup** of $G$ if the following holds:

(1) If $a,b\in H$, $a*b\in H$;

(2) If $a\in H$, $a^{-1}\in H$.

**Proposition:** If $(G,*)$ is a group and $H$ is a subgroup. Then $(H,*)$ is a group.

**Proof:** (Closedness) $*:H\times H\to H$ is a binary operation by (1).

(Associativity) $(a*b)*c=a*(b*c),\forall a,b,c\in H(\subseteq G)$

(Identity) Take any $a\in H$, $a^{-1}\in H$ by (2);

Therefore $a*a^{-1}=e\in H$.

(Inverse) $a^{-1}\in H,\forall a\in H$ by (2).

**Remark:** If $H\not=\left\{e\right\}\subseteq G$ is a subgroup, we call it a **nontrivial subgroup**.

## Cyclic Subgroup
**Definition:** Let $(G,*)$ be a group. A **cyclic subgroup** generated by $g\in G$ is the subgroup:

$$\langle g\rangle:=\left\{g^m|m\in\mathbb{Z}\right\}$$

where $g^m$ is defined as $\underbrace{g*g*\cdots*g}_{m}$.

**Definition:** Let $(G,*)$ be a group. We say $G$ is **cyclic** if there is a **generator** $g\in G$ such that $\langle g\rangle=G$.

## Order of an Element
**Definition:** Let $g\in G$. The **order** of $g$ is equal to the smallest positive integer $k$ such that $g^k=e$. If no such $k$ exists, we say the order of $g$ is $\infty$.

**Proposition:** If $ord(g)=k$, then $|\langle g\rangle|=k$.

**Theorem:** (Lagrange's Theorem) $\small ord(g)\large|\small|G|$ if $|G|<\infty$.

## Permutation/Symmetric Group
**Definition:** A **permutation** of $X_n=\left\{1,2,\cdots,n\right\}$ is a bijection:

$$\sigma: X_n\to X_n$$

(e.g. When $n=3$, it can be $\sigma(1)=2,\sigma(2)=3,\sigma(3)=1$)

The **symmetric/permutation group** of $n$ elements is the collection of all permutations:

$$S_n:=\left\{\sigma: X_n\to X_n|\sigma\text{ is bijective}\right\}$$

**Proposition:** $(S_n,\circ)$ ($\circ$ is the composition of functions) is a group.

**Proof:** (Associativity) This is obvious true since composition of functions is associative.

(Identity) Take $e=id:X_n\to X_n,id(x)=x,x\in X_n$.

(Inverse) Since $\sigma$ is bijective, $\sigma^{-1}$ exists.

**Remark:** Groups are often used to study "symmetry" of objects. For example, $S_n$ is used to study symmetry of $n$ objects. As another example, to describe symmetrics of $\mathbb R^n$, we study:

$$\left\{A:\mathbb{R}^n\to\mathbb{R}^n|A\text{ is a bijective linear transformation}\right\}$$

which is $GL(n,\mathbb R)$.

**Remark:** $(S_n,\circ)$ is not Abelian ($\circ$ is not commutative on $S_n$).

## Cycle Notion
**Definition:** Let $1\leq i_1<i_2<\cdots<i_k\leq n$. A **k-cycle** in $S_n$ is an element of the form:

$$
\begin{align}
(i_1,&i_2,\cdots i_k)=
\\
&\left(
\begin{matrix}
1 &\cdots &i_1 &i_2 &\cdots &i_{k-1} &i_k &\cdots &n
\\1 &\cdots &i_k &i_1 &\cdots &i_{k-2} &i_{k-1} &\cdots &n
\end{matrix}
\right)
\end{align}
$$

i.e. only the $k$ entries are swapped, and the other entries stay the same.

More generally, for all $1\leq i_1,\cdots,i_k\leq n$, where all $i_l$ are distinct, we also write a **k-cycle** $(i_1,\cdots,i_k)$ to be the permutation $\sigma(i_1)=i_2,\sigma(i_2)=i_3,\cdots,\sigma(i_k)=i_1$ and all other $\sigma(j)=j$.

**Example:**

$$\sigma=\left(
\begin{matrix}
1 &2 &3 &4 &5 &6 &7 &8
\\2 &3 &6 &1 &5 &4 &8 &7
\end{matrix}
\right)=(1,4,6,3,2)(5)(7,8)$$

**Observation:**

- All $\sigma\in S_n$ can be written as product of disjoint $k$-cycles;
- If $\sigma=(i_1,i_2,\cdots,i_k)$ is a $k$-cycle, then $ord(\sigma)=k$.

**Remark:** (1) If $\alpha$ and $\beta$ are $k$-cycles with disjoint entries, then $\alpha\beta=\beta\alpha$. Otherwise $\alpha\beta\not=\beta\alpha$ in general;

(2) The inverse of a $k$-cycle is given by:

$$(i_1,i_2,\cdots,i_{k-1},i_k)^{-1}=(i_k,i_{k-1},\cdots,i_2,i_1)$$

(3) More generally, for any $\sigma\in S_n$, 

$$\sigma=(i_1,\cdots,i_k)(j_1,\cdots,j_l)\cdots(m_1,\cdots,m_p)$$

where the cycles are disjoint,

$$\sigma^{-1}=(i_k,\cdots,i_1)(j_k,\cdots,j_1)\cdots(m_p,\cdots,m_1)$$

## Transposition
**Definition:** A 2-cycle $\tau=(i,j)\in S_n$ is called a **transposition**.

**Proposition:** Every $\sigma\in S_n$ can be expressed as product of transpositions (not necessarily disjoint).

**Proof:** $\sigma=(i_1,\cdots,i_k)(j_1,\cdots,j_k)\cdots$, each $i,j,\cdots$ cycle is disjoint. Then for any cycle, W.L.O.G.:

$$(i_1,\cdots,i_k)=(i_1,i_k)(i_1,i_{k-1})\cdots(i_1,i_3)(i_1,i_2)$$

We are done.

**Remark:** The expression of $\sigma\in S_n$ into product of transposition is not unique. e.g. $\sigma=(2,3)=(2,3)(2,3)(2,3)$. However, the number of transpositions in each expression of $\sigma$ remains even or odd.

**Proposition:** Let $\sigma=\tau_1\cdots\tau_k=\tau_1'\cdots\tau_k'$ be two expressions of $\sigma$ as product of transpositions. Then $k\equiv l(\operatorname{mod} 2)$.

**Lemma:** Proposition 1 holds for $\sigma=e$, where $k\equiv 0(\operatorname{mod} 2)$.

**Proof of proposition 1:** Suppose $\sigma=\tau_1\cdots\tau_k=\tau_1'\cdots\tau_l'$, then:

$$(\tau_1\cdots\tau_k)^{-1}(\tau_1'\cdots\tau_l')=e$$

Then:

$$\tau_k^{-1}\cdots\tau_2^{-1}\tau_1^{-1}\tau_1'\cdots\tau_l'=e$$

Since for proposition $\tau_i^2=e$:

$$\tau_k\cdots\tau_1\tau_1'\cdots\tau_l'=e$$

By lemma: $k+l\equiv 0(\operatorname{mod} 2)$.

## Even/Odd Permutation
**Definition:** $\sigma\in S_n$ is called an **even/odd permutation** if $\sigma$ is a product of even/odd number of transpositions.

## Alternating Group
**Definition:** The **alternating group** $A_n$ is the subgroup of $S_n$ given by:

$$A_n:=\left\{\sigma\in S_n|\sigma\text{ is even}\right\}$$

**Proposition:** $|A_n|=\frac{1}{2}|S_n|=\frac{n!}{2}$

**Proof:** Let $\tau\in S_n$ be a transposition, and:

$$f:A_n\to\left\{\sigma\in S_n|n\text{ is odd}\right\}$$

be $f(\sigma):=\sigma\tau$. Then $f$ is a bijective with $f^{-1}=f$. Therefore the number of odd permutations is equal to that of even permutations. Since they are disjoint, $|A_n|=\frac{n!}{2}$.

## Dihedral Group
**Definition:** The dihedral group $D_n$ is the symmetric group of an $n$-sided regular polygon for $n>1$. Let $r$ be the rotation, $s$ be the reflection. Then $D_n$ has $n$ rotations and $n$ reflections, so $|D_n|=2n$, and:

$$D_n=\left\{s,r|r^n=e,s^2=e,sr^l=r^{n-l}s\text{ for all } l\right\}$$

**Definition:** $r^ks$ is a reflection along axis obtained by rotating the **principal axis** by $\frac{k}{n}(180^\circ)$ counterclockwise. Therefore, 

$$D_n=\left\{e,r,r^2,\cdots,r^{n-1},s,rs,r^2s,\cdots,r^{n-1}s\right\}$$

## Product Groups
**Definition:** Let $G_1,\cdots,G_n$ be groups. The **product group**:

$$G:=\prod_{i=1}^nG_i=G_1\times\cdots\times G_n$$

is given by $G=\left\{(g_1,\cdots,g_n)|g_i\in G_i\right\}$ and multiplication is given by:

$$(g_1,\cdots,g_n)*(h_1,\cdots,h_n)=(g_1h_1,\cdots,g_nh_n)$$

## Homomorphism and Isomorphism
**Definition:** Let $(G,*),(H,*')$ be 2 groups. A **homomorphism** from $G$ to $H$ is a map:

$$\phi:G\to H$$

such that $\phi(g_1*g_2)=\phi(g_1)*'\phi(g_2)$. If $\phi$ is bijective, then $\phi$ is an isomorphism ($\phi$ preserves the multiplication rule of $G$ and $H$).

**Examples:** (1) $\phi:D_4\to S_4$ given by:

$$
\begin{cases}
\phi(r):=(1,2,3,4)
\\\phi(s):=(2,4)
\\\phi(rs):=(1,2)(3,4)
\end{cases}
$$

is an injective homomorphism, e.g. $\phi(r^2s)=\phi(r^2)\phi(s)$.

(2) Let $(G,*)=(\mathbb{R}^n,+),(H,*')=(\mathbb{R}^m,+)$, then any linear transformation $T:\mathbb{R}^n\to\mathbb{R}^m$ is a group homomorphism.

**Propositions:** (a) If $\phi:G\to H,\psi:H\to K$ are homomorphisms, then $\psi\circ\phi:G\to K$ is a homomorphism;

(b) If $\phi:G\to H$ is homomorphism, then $\phi(e_G)=e_H$ and $\phi(a^{-1})=(\phi(a))^{-1}$;

(c) If $\phi:G\overset{\cong}{\to}H$ is isomorphic, then $\phi^{-1}:H\to G$ satisfies $\phi^{-1}(h_1h_2)=\phi^{-1}(h_1)\phi^{-1}(h_2)$. In other words, the inverse of an isomorphism is an isomorphism.

**Proof:** (a) 

$$
\begin{align}
\psi\circ\phi(g_1*_Gg_2)&=\psi(\phi(g_1*_Gg_2))
\\&=\psi(\phi(g_1)*_H\phi(g_2))
\\&=(\psi\circ\phi(g_1))*_K(\psi\circ\phi(g_2))
\end{align}
$$

(b) $\phi(g)=\phi(e_G*_Gg)=\phi(e_G)*_H\phi(g)$, then $\phi(e_G)=e_H$ by uniqueness of identity in $H$. For the second part, since: $\phi(a^{-1}*_Ga)=\phi(a^{-1})*_H\phi(a)=e_H$, $\phi(a^{-1})=(\phi(a))^{-1}$.

(c) $\phi(\phi^{-1}(h_1h_2))=h_1h_2$.

## Kernel, Image
**Definition:** Let $\phi:G\to H$ be a homomorphism. The **kernel** of $\phi$ is defined as:

$$\ker\phi=\left\{g\in G|\phi(g)=e_H\right\}$$

The **image** of $\phi$ is defined as:

$$\operatorname{im}\phi=\phi(G)=\left\{\phi(g)|g\in G\right\}$$

**Proposition:** (a) $\ker\phi\leq G,\operatorname{im}\phi\leq H$ are subgroups;

(b) $\phi$ is an isomorphism $\Leftrightarrow$ $\begin{cases}\ker\phi=e_G\\\operatorname{im}\phi=H\end{cases}$;

(c) If $G$ is cyclic/abelian, then $\phi(G)$ is cyclic/abelian.

**Proof:** (a) Closedness: let $g_1,g_2\in\ker\phi$, then $\phi(g_1g_2)=\phi(g_1)\phi(g_2)=e_H^2=e_H$, then $g_1g_2\in\ker\phi$;

Associativity is obvious;

Identity: the identity is $e_H$;

Inverse: $\phi(g^{-1})=(\phi(g))^{-1}=e_H^{-1}=e_H$.

(b) Since $\phi$ is an isomorphism, $\phi$ is bijective. Then:

$$
\begin{cases}
\ker\phi=e_G\Leftrightarrow \phi \text{ is injective}
\\\operatorname{im}\phi=H\Leftrightarrow \phi \text{ is surjective}
\end{cases}
$$

(c) If $G$ is abelian, then for all $\phi(a),\phi(b)\in\phi(G)$,

$$\phi(a)\phi(b)=\phi(ab)=\phi(ba)=\phi(b)\phi(a)$$

**Theorem:** (Classification of cyclic groups) Let $G=\langle g\rangle$ be a cyclic group. Then:

(a) If $|G|=\infty$, $G\cong(\mathbb Z,+)$;

(b) If $|G|=n$, $G\cong(\mathbb Z_n,+)$.

**Proof:** (a) Consider the map:

$$\phi:\mathbb Z\to\langle g\rangle=\left\{gi|i\in\mathbb Z\right\}=G$$

$$a\to g^a$$

Then $\phi(a+b)=g^{a+b}=g^ag^b=\phi(a)\phi(b)$, i.e. $\phi$ is a surjective homomorphism.

Suppose $\phi$ is not injective, i.e. $\phi(m)=\phi(n),m>n$, W.L.O.G., $g^m=g^n$.

Then: $g^{m-n}=e\Rightarrow ord(g)\leq m-n$ and $ord(g)|(m-n)$.

Therefore $m=n+k\times ord(g)$, $m\equiv n(\operatorname{mod} ord(g))$. Therefore $\phi$ is injective.

Then, $\phi$ is bijective.

## Equivalence Relation
**Definition:** **Equivalence relation** satisfies properties:

(1) $a\sim a$;

(2) $a\sim b\Rightarrow b\sim a$;

(3) $a\sim b,b\sim c\Rightarrow a\sim c$.

Let $a\in S$, denote $C_a=\left\{b\in S|a\sim b\right\}$.

**Observations:** (1) If $a\sim a'$ in $S$, then $C_a=C_a'$; therefore, any element in an equivalence class $C$ is a representative of $C$.

(2) If $a\not\sim a'$, then $C_a\cap C_{a'}=\emptyset$; therefore, $S$ can be partitioned into disjoint equivalence classes $S=C_{a_1}\cup C_{a_2}\cup\cdots$, where $\left\{C_\alpha|\alpha\in A\right\}$ are equivalence classes and $C_\alpha\cap C_\beta=\emptyset$ if $\alpha\not=\beta$.

## Left Coset

**Definition:** Let $G$ be a group and $H\leq G$, define an equivalence relation on $G$ by $a\sim b\Leftrightarrow a^{-1}b\in H$. Define the **left coset** of $H$ with representative $a$ as $aH:=C_a=\left\{b\in G|b=ah,h\in H\right\}$.

**Remark:** We can also define $a\sim_Rb$ by $a\sim_Rb\Leftrightarrow ba^{-1}\in H$. The equivalence class of $\sim_R$ is called **right cosets** $Ha=\left\{ha|h\in H\right\}$.

## Lagrange Theorem

**Theorem:** Let $G$ be a finite group and $H\leq G$. Then $\small |H|\large|\small|G|$. More precisely, let:

$$m=[G:H]:=\text{number of disjoint left cosets of }H$$

Then $|H|=\frac{|G|}{m}$.

**Proof:** Since left cosets of $H$ is equal to equivalent classes of $G$, we can partition:

$$G=eH\cup a_2H\cup\cdots\cup a_mH$$

into disjoint union of equivalent classes. Then we just need to check each $a_iH$ have the same number of elements. Suppose $|H|=r$:

$$a_iH=\left\{a_ih_1,\cdots,a_ih_r\right\}$$

where $\left\{h_1,\cdots,h_r\right\}=H$.

Then for each $a_ih_x,a_ih_y\in a_iH$, if $a_ih_x=a_ih_y$, then $h_x=h_y$ and $x=y$. So the elements in $a_iH$ are distinct, and hence $|a_iH|=|H|=r$.

Therefore, $|G|=|H|+|H|+\cdots+|H|=m|H|$.

**Corollary**: Let $|G|<\infty$. Then for all $g\in G$, $\small ord(g)\large |\small |G|$.

**Proof:** Take $H:=\langle g\rangle\leq G$. Then:

$$ord(g)=|H|=|\left\{e,g,\cdots,g^{n-1}\right\}|$$

By Lagrange's Theorem: $ord(g)=\small |H|\large|\small|G|$.

## Fermat's Little Theorem
**Theorem:** Let $a\in G=\mathbb{Z}_p^*$. Then $a^{p-1}=1$ in $\mathbb Z_p$.

**Proof:** By corollary of Lagrange Theorem, for all $a\in \mathbb{Z}_p^*=G$, $\small d=ord(a)\large|\small|\mathbb Z_p^*|=p-1$.

**Theorem:** More generally, if $G=\mathbb Z_n^*$, $|G|=\phi(n)$, then $a^{\phi(n)}\equiv 1(\operatorname{mod}n)$.

## Normal Subgroup
**Definition:** $H\leq G$ is a **normal subgroup** if

$$gH=Hg,\forall g\in G$$

noted as $H\Delta G$.

**Proposition:** $A_n\Delta S_n$ for all $n$.

**Proof:** If $g\in S_n$ is odd, then since $|A_n|=\frac{|S_n|}{2}$, $|gA_n|=|A_ng|=\frac{|S_n|}{2}$, and any element in $gA_n$ and $A_ng$ is odd. Then $gA_n$ and $A_ng$ both contains all odd permutations. They are equal. Similarly we can prove the case $g$ is even.

**Theorem:** Let $H\leq G$ be a subgroup. The following statements are equivalent (TFAE):

(i) $H\Delta G$;

(ii) $\forall h\in H,g\in G,ghg^{-1}\in H$;

(iii) $gHg^{-1}=H,\forall g\in G$.

**Proof:**

(i) -> (ii): By assumption $gH=Hg,\forall g\in G$.

Then for all $h\in H,gh\in gH=Hg$ can be written as $gh=h'g$ for some $h'\in H$. Then $ghg^{-1}=h'\in H$.

(ii) -> (iii): By (ii) we get $gHg^{-1}\subseteq H$.

Then $g^{-1}gHg^{-1}g\subseteq g^{-1}Hg$, which implies $H\subseteq g^{-1}Hg$. Take inverse then $H\subseteq gHg^{-1}$.

Therefore, $H=gHg^{-1}$.

(iii) -> (i): By (iii) we get $gH=Hg,\forall g\in G$.

By definition, (i) is proved.

**Corollary:** Let $\phi:G\to H$ be a homomorphism. Then $\ker(\phi)\Delta G$.

**Proof:** By (ii) in the theorem, we only need to show 

$$\forall k\in\ker(\phi),g\in G,gkg^{-1}\in\ker(\phi)$$

Since:

$$
\begin{align}
\phi(gkg^{-1})&=\phi(g)\phi(k)\phi(g^{-1})
\\&=\phi(g)e_H(\phi(g))^{-1}
\\&=e_H
\end{align}
$$

Then $gkg^{-1}\in\ker(\phi)$.

## Quotient Group
**Definition/Theorem:** Let $G$ be a group, and $H\Delta G$ be normal. Then the left (or right) cosets of $H$ in $G$:

$$G/H:=\left\{aH|a\in G\right\}$$

forms a **quotient group** with the multiplication rule given by:

$$(aH)*(bH):=(ab)H$$

**Proof:** Check * is well-defined:

Suppose $\begin{cases}aH=a'H\\bH=b'H\end{cases}$, then:

$$a^{-1}a'=h_a\in H,b^{-1}b'=h_b\in H$$

Then $a'b'=(ah_a)(bh_b)=abh_a'h_b'\Rightarrow a'b'\in(ab)H$.

Therefore, $(a'b')H=(ab)H$.

**Remark:** If $|G|<\infty$ is finite, then: 

$$|G/H|=|\left\{\text{left cosets of } H \text{ in G}\right\}|=[G:H]=\frac{|G|}{|H|}$$

## First Isomorphism Theorem
**Theorem:** Let $\phi:G\to H$ be a group homomorphism, then:

$$G/\ker(\phi)\cong im(\phi)$$

**Proof:** Define a map:

$$\Psi:G/\ker(\phi)\to im(\phi)$$

by $\Psi(g\ker(\phi)):=\phi(g)$.

(1) $\Psi$ is well-defined: if $g\ker(\phi)=g'\ker(\phi)$, then $\Psi(g\ker(\phi))=\Psi(g'\ker(\phi))$.

To see why this is true,

$$g\ker(\phi)=g'\ker(\phi)\Leftrightarrow g^{-1}g'\in\ker(\phi)$$

Then $\phi(g^{-1}g')=e_H\Leftrightarrow \phi(g)^{-1}\phi(g')=e_H$.

Then $\phi(g)=\phi(g')$ such that $\Psi(g\ker(\phi))=\Psi(g'\ker(\phi))$.

(2) $\Psi$ is a homomorphism:

$$
\begin{align}
\Psi((g\ker(\phi))(g'\ker(\phi)))&=\Psi(gg'\ker(\phi))
\\&=\phi(gg')
\\&=\phi(g)\phi(g')
\\&=\Psi(g\ker(\phi))\Psi(g'\ker(\phi))
\end{align}
$$

(3) $\Psi$ is surjective: obvious by definition.

(4) $\Psi$ is injective: W.T.S. $\ker(\Psi)=\left\{e_{G/\ker(\phi)}\right\}$.

Suppose $g\ker(\phi)\in\ker(\Psi)$,

$$\Psi(g\ker(\phi))=e_H\Rightarrow\phi(g)=e_H$$

Then $g\in\ker\phi$.

Therefore, $g\ker(\phi)=\ker(\phi)=e_G\ker(\phi)=e_{G/\ker(\phi)}$.

Then by (1), (2), (3), (4), $\Psi$ is an isomorphism.

**Remark:** Proof in (1) already implies (4).

## *Cauchy's Theorem
**Theorem:** Suppose $|G|<\infty$ is finite and $\small p\large|\small|G|$ for some prime $p$. Then $G$ must have an element $g$ of order $p$.

## Simple Groups
**Definition:** A group $G$ is called **simple** if $G$ has no normal subgroup other than $\left\{e\right\}$ and $G$ itself.

**Remark:** If $G$ is not simple, then we have $N\Delta G$ so we can decompose $G$ into $G/N$ and $N$ to study them individually. If $|G|<\infty$ is not simple, then $|G/N|=\frac{|G|}{|N|}$, so $|G/N\times N|=|G/N|\times|N|=|G|$. However, $G\not\cong G/N\times G$ in general.

## Classification of Abelian Groups of Finite Order
**Theorem:** All finite abelian groups are of the form:

$$G\cong\mathbb{Z}_{p_1^{a_1}}\times\cdots\times\mathbb{Z}_{p_k^{a_k}}$$

where $p_1\leq\cdots\leq p_k$ are primes, $a_1,\cdots,a_k\in\mathbb{N}\backslash\left\{0\right\}$ ($p_i$ not necessarily distinct).

**Proof:** 

Step 1: Suppose $|G|=p^aq^b$, W.T.S. $G\cong G_1\times G_2$, $|G_1|=p^a=m,|G_2|=q^b=n$ and the general case follows for induction on # of prime powers.

Let $G^m=\left\{g^m|g\in G\right\},G^n=\left\{g^n|g\in G\right\},G^m,G^n\leq G$.

Claim 1. $G^m\cap G^n=\left\{e\right\}$.

Take $x\in G^m\cap G^n$, then $x=g^m=h^n$ for some $g,h\in G$.

Then $x^n=g^{mn}=e$ by Lagrange's Theorem ($|G|=mn$). Similarly $x^m=h^{nm}=e$.

Note that $\gcd(m,n)=\gcd(p^a,q^b)=1$, then:

$$\alpha m+\beta n=1$$

for some $\alpha,\beta\in\mathbb Z$.

Then $x^{\alpha m+\beta n}=(x^{m\alpha})(x^{n\beta})=x^1=e$. Then $x=e$.

Therefore, $G^m\cap G^n=\left\{e\right\}$.

Define $\phi:G^m\times G^n\to G$ by $\phi(g^m,h^n):=g^m(h^n)^{-1}$.

Claim 2. $\phi$ is an isomorphism.

$\phi$ is a homomorphism.

$\phi$ is injective: Suppose $\phi(g^m,h^n)=e$, then:

$$g^m(h^n)^{-1}=e\Rightarrow g^m=h^n=e$$

Then $\ker(\phi)=\left\{(e,e)\right\}$.

$\phi$ is surjective: Take $y\in G$,

$$y=y^1=y^{\alpha m+\beta n}=(y^\alpha)^m(y^{-\beta})^{-n}=\phi(y^\alpha,y^{-\beta})$$

Claim 3. $|G^m|=n=q^b,|G^n|=m=p^a$ so that $G\cong G^m\times G^n$.

Define $\Psi:G^n\to G^n$ by $\Psi(h^n):=(h^n)^n$, then $\Psi$ is an homomorphism. Consider $\theta:G^n\to G^n$ defined by $\theta(h^n)=(h^n)^\beta$. Then for all $h^n\in G^n$, 

$$h^n=h^{n\cdot 1}=(h^{n})^{\alpha m+\beta n}=h^{\beta n^2}=\theta(\Psi(h^n))=\Psi(\theta(h^n))$$

Then $\theta=\Psi^{-1}$ and $\Psi$ is an isomorphism.

Consider $r:=\gcd(|G^n|,n)$, then for all $x\in G^n$,

$$x^r=e\Rightarrow x^n=e\Rightarrow (x^n)^\beta=e\Rightarrow\Psi\theta(x)=e\Rightarrow x=e$$

If $r=1$, it is obviously true;

If $r\not=1$, then $r=q^z$ for some $z\leq b$. By Cauchy's Theorem, $G^n$ has an element of order $q$. Then $x^q=e,x^r=(x^q)^z=e$, then $x=e$, the order of $x$ is $1\not=q$, which is a contradiction.

Therefore, $\gcd(|G^n|,n)=1$.

Since $\small|G^n|\large|\small|G|$ by Lagrange's Theorem, $|G^n|=p^k$ for some $k$. Similarly $|G^m|=q^{k'}$ for some $k'$.

By Claim 2, $|G^m\times G^n|=|G|$, then $p^kq^{k'}=p^aq^b$. Therefore $k=a,k'=b$. Then we prove:

$$|G^m|=p^a,|G^n|=q^b$$

Step 2: Suppose $|G|=p^a$. Then for all $x\in G,ord(x)=p^i$ by Lagrange's Theorem. Let $m\in G$ be an element with maximum order $ord(m)=p^l$ in $G$, then $G\cong \langle m\rangle\times K$ for some $|K|=p^{a-l}$. The proof of this proposition is skipped.

From the proposition, we have a corollary: if $|G|=p^a$ is abelian,

$$G\cong\mathbb{Z}_{p^{b_1}}\times\mathbb{Z}_{p^{b_2}}\times\cdots\times\mathbb Z_{p^{b_l}}$$

where $\sum_{j=1}^lb_j=a$. This can be proved by induction.

**Corollary:** (Smith Normal Form) All finite abelian group $G$ is isomorphic to $A\cong\mathbb{Z}_{d_1}\times\cdots\mathbb{Z}_{d_k}$ where $d_i>1$ are integers and $d_i|d_{i+1},\forall i=1,\cdots,k-1$. Moreover if:

$$H\cong\mathbb{Z}_{e_1}\times\cdots\times\mathbb{Z}_{e_l}$$

for integers $e_i>1$ and $e_i|e_{i+1},\forall i$. Then:

$$G\cong H\Leftrightarrow l=k \wedge d_i=e_i,\forall i$$

## Rings
**Definition:** A ring $(R,+,\cdot)$ is a set equipped with 2 binary operations $+,\cdot:R\times R\to R$ such that:

(1) $(R,+)$ is an abelian group with addictive identity $0_R\in R$;

(2) $(R,\cdot)$ is associative:

$$(a\cdot b)\cdot c=a\cdot(b\cdot c),\forall a,b,c\in R$$

(3) $(R,+,\cdot)$ is distributive:

$$
\begin{cases}
a\cdot(b+c)=a\cdot b+a\cdot c
\\(a+b)\cdot c=a\cdot c+b\cdot c
\end{cases},\forall a,b,c\in R
$$

**Definition:** Let $(R,+,\cdot)$ be a ring. We say:

(a) $R$ is **unital** if $\exists 1_R\in R$ such that:

$$1_R\cdot r=r\cdot 1_R=r,\forall r\in R$$

(b) If $R$ is unital, then the **units** of $R$ are the elements:

$$u(R)=\left\{a\in R|\exists a^{-1}\in R,s.t.aa^{-1}=a^{-1}a=1_R\right\}$$

**Remark:** The additive identity $0_R\in R$ is unique in $R$. If $R$ is unital, then the multiplicative identity $1_R\in R$ is also unique.

**Proposition:**

(1) $0_R\cdot r=0_R=r\cdot 0_R$;

(2) $(-1_R)\cdot r=r\cdot(-1_R)=-r$;

(3) $(-1_R)\cdot(-r)=(-r)\cdot(-1_R)=r$.

**Proof:**

(1) $a\cdot r=(0_R+a)\cdot r=0_R\cdot r+a\cdot r$

Then $0_R\cdot r=0_R$.

(2) $0_R\cdot r=(1_R+(-1_R))\cdot r$

Then $0_R=1_R\cdot r+(-1_R)\cdot r$.

Then $-r=(-1_R)\cdot r$.

**Definition:** Let $(R_1,+_1,\cdot_1),(R_2,+_2,\cdot_2)$ be rings, then $R_1\times R_2$ is called a **product ring** with:

$$(r_1,r_2)+(r_1',r_2'):=(r_1+_1r_1',r_2+_2r_2')$$

$$(r_1,r_2)\cdot(r_1',r_2'):=(r_1\cdot_1r_1',r_2\cdot_2r_2')$$

**Definition:** Let $(R,+,\cdot)$ be a ring. A subset $S\subseteq R$ is a **subring** if:

$$+|_{S\times S}:S\times S\to S,\cdot|_{S\times S}:S\times S\to S$$

gives a ring structure of $S$. Or to say:

$$a+b\in S,-a\in S, ab\in S$$

**Proposition:** $S\subseteq R$ is a subring $\Leftrightarrow$ $\forall a,b\in S,a+b\in S,-a\in S,a\cdot b\in S$.

**Definition:** Let $R$ be a commutative unital ring. We say $R$ is a **field** if all nonzero elements of $R$ are in the units $u(R)$ of $R$. e.g. $n\mathbb Z\subseteq\mathbb Z\subseteq \mathbb Q\subseteq \mathbb R\subseteq \mathbb C$, where $n\mathbb Z$ is not unital, $\mathbb Z$ is not a field, and $\mathbb Q,\mathbb R,\mathbb C$ are fields.

## Ring Homomorphism
**Definition:** Let $R,S$ be rings. A map $\phi:R\to S$ is a **homomorphism** of rings if:

$$
\begin{cases}
\phi(a+_Rb)=\phi(a)+_S\phi(b)
\\\phi(a\cdot_Rb)=\phi(a)\cdot_S\phi(b)
\end{cases}
$$

- If $R,S$ are unital, we say a homomorphism $\phi:R\to S$ **unital** if $\phi(1_R)=1_S$.
- If $\phi$ is bijective, then $\phi$ is called a **ring isomorphism**.

**Remark:** Ring homomorphism is more restrictive than group homomorphism.

**Proposition:** Let $\phi:R\to S$ be a ring homomorphism, then:

(a) $\phi(0_R)=0_S$;

(b) $\phi(-a)=-\phi(a)$;

(c) If $\phi$ is unital and $a\in u(R)$, then $\phi(a)\in u(S)$ with $\phi(a)^{-1}=\phi(a^{-1})$;

(d) If $\phi:R\overset{\cong}{\to} S$ is an isomorphism, then $\phi^{-1}:S\to R$ is a ring isomorphism as well.

**Proof:** (a) $\phi(0_R+r)=\phi(0_R)+\phi(r)=\phi(r)$, by uniqueness of additive identity, $\phi(0_R)=0_S$.

(c) $\phi(a^{-1}a)=\phi(1_R)=1_S$, then $\phi(a^{-1})\cdot\phi(a)=1_S$ and similarly $\phi(a)\cdot\phi(a^{-1})=1_S$. Therefore, $\phi(a)$ is a unit with $\phi(a)^{-1}=\phi(a^{-1})$.

(d) Let $\alpha,\beta\in S$, then $\exists a,b\in R,s.t.\phi(a)=\alpha,\phi(b)=\beta$, W.T.S. $\phi^{-1}(\alpha\beta)=\phi^{-1}(\alpha)\phi^{-1}(\beta)$.

Now $\phi(ab)=\phi(a)\cdot\phi(b)=\alpha\cdot\beta$, then $ab=\phi^{-1}(\alpha\beta)$.

Now we check $\phi^{-1}(\alpha+\beta)=\phi^{-1}(\alpha)+\phi^{-1}(\beta)$:

$$\phi(a+b)=\phi(a)+\phi(b)=\alpha+\beta$$

Then $a+b=\phi(a+b)^{-1}$.

**Proposition:** Let $\phi:R\to S$ be a ring homomorphism, then:

$$\ker(\phi):=\left\{r\in R|\phi(r)=0_S\right\}\leq R$$

$$im(\phi):=\left\{\phi(r)|r\in R\right\}\leq S$$

**Proof:** Let $a,b\in\ker(\phi)$, then:

$$\phi(a+b)=\phi(a)+\phi(b)=0_S+0_S=0_S$$

$$\phi(-a)=-\phi(a)=-0_S=0_S$$

$$\phi(a\cdot b)=\phi(a)\cdot\phi(b)=0_S\cdot 0_S=0_S$$

Then $a+b,-a,ab\in\ker(\phi)$, and $\ker(\phi)$ is a subring of $R$.

**Remark:** In groups, we know $\ker(\phi)$ is a **normal** subgroup of $R$. We'll study **ideals**, which is the ring analogue of normal subgroups.

## Integral Domain
**Definition:** Let $R$ be a ring. A nonzero element $r\in R$ is a **zero-divisor** if $\exists s\not=0$ in $R$ such that $r\cdot s=0$ or $s\cdot r=0$.

**Definition:** If $R$ has no zerodivisors, then $R$ is a **domain**. Moreover, if $R$ is a commutative ring with no zerodivisors, then $R$ is an **integral domain**.

**Remark:** 

- $\mathbb Z_m$ is integral domain $\Leftrightarrow$ $m$ is prime. 
- $\mathbb Z,\mathbb Q,\mathbb R,\mathbb C,\mathbb Z[i]$ are integral domains. 
- If $R$ is an integral domain, then so is $R[x]$.

**Proposition:** (Cancellation Property) Let $R$ be a commutative ring. Then $R$ is an integral domain. One can cancel the common factor on both sides of equation exactly when $R$ is an integral domain.

**Proof:** $ca=cb\Leftrightarrow ca+c(-b)=0\Leftrightarrow c(a-b)=0$

Then $c=0$ or $a-b=0$. Since $c\not=0$, $a-b=0$, then $a=b$.

**Overview:** The inclusion relationship is (from inner to outer):

Fields, Euclideen Domain (ED), Principal Ideal Domain (PID), Unique Factorization Domain (UFD), Integral Domain.

**Proposition:** Let $R$ be an integral domain with $|R|<\infty$. Then $R$ is a field.

**Lemma:** Let $R$ be an integral domain with $|R|<\infty$, then $R$ is unital.

**Proof:** Let $a\in R$ be nonzero. Then $\left\{a,a^2,\cdots\right\}\subseteq R$ must repeat since $|R|<\infty$. Suppose $a^m=a^n$ for some $m>n$. Claim: $1_R=a^{m-n}$, proof: for any $x$, if $xa^{m-n}=y$, then $xa^{m-n}a^n=ya^n$, then $x=y$. Therefore, $a^{m-n}=1_R$, then $R$ is unital.

**Proof of proposition:** Let $R\backslash\left\{0_R\right\}=\left\{r_1=1_R,r_2,\cdots,r_m\right\}$. Then for all $a\not=0$ in $R$, consider $\left\{ar_1,ar_2,\cdots,ar_m\right\}$. By cancellation property, there are no repetitions. Then $\exists r_l$ such that $ar_l=r_1=1_R$. Then $r_l=a^{-1}$, all $a\not=0$ are units.

## Ideal
**Definition:** Let $R$ be a ring. We say $I\subseteq R$ an ideal if:

- $I$ is an additive subgroup of $(R,+)$;
- For all $x\in R,i\in I$, we have $xi,ix\in I$.

**Remark:** We write $I\Delta R$ if $I$ is an ideal of $R$. If $I\Delta R$, then $I\leq R$ automatically (But a subring may not be ideal).

**Definition:** Let $R$ be a ring, $V\leq R$ be a subset. Then the **ideal generated by** $V$ is $\left<v\right>$, which is the smallest ideal in $R$ containing all elements in $V$.

**Definition:** Let $R$ be a commutative ring. If $R$ is unital, then:

$$\left<v_1,\cdots,v_k\right>=\left\{v_1r_1+\cdots+v_kr_k|r_i\in R\right\}$$

An ideal $I\Delta R$ is called **principal** if $I=\left<a\right>=aR=\left\{ar|r\in R\right\}$ for some $a\in R$.

**Definition:** Let $R$ be an integral domain. We say $R$ is a **principal ideal domain** if all ideals in $R$ are principal.

**Lemma:** Suppose $I_1,\cdots,I_k\Delta R$, then:

(a) $I_1+\cdots+I_k:=\left\{i_1+\cdots+i_k|i_r\in I_r\right\}\Delta R$;

(b) $\bigcap_{i=1}^kI_i\Delta R$.

**Proof:** (a) Let $(i_1+\cdots+i_k)\in I_1+\cdots+I_k$, then $-i_r\in I_r,\forall r=1,\cdots,k$.

Then $(-i_1)+(-i_2)+\cdots+(-i_r)\in I_1+\cdots+I_k$.

Since $I_1,\cdots,I_k$ are additive subgroups,

$(i_1+i_1')+\cdots+(i_k+i_k')\in I_1+\cdots+I_k$.

Then $I_1+\cdots+I_k$ is an additive subgroup. Now take any $r\in R$, then:

$$r\cdot(i_1+\cdots+i_k)=ri_1+\cdots+ri_k\in I_1+\cdots+I_k$$

**Proposition:** Let $\phi:R\to S$ be a ring homomorphism, then $\ker(\phi)\Delta R$.

**Proof:** For any $r\in R,i\in\ker(\phi)$, 

$$\phi(ri)=\phi(r)\phi(i)=\phi(r)\cdot 0_S=0_S$$

Then $ri\in\ker(\phi)$, similarly $ir\in\ker(\phi)$.

## Quotient Ring
**Proposition/Definition:** Let $R$ be a ring, and $I\Delta R$ be ideal. Consider the collection of left cosets of $(R,+)$:

$$R/I:=\left\{r+I|r\in R\right\}$$

Then $(R/I,+)$ has a group structure with the operations:

$$(r_1+I)+(r_2+I):=(r_1+r_2)+I$$

$$(r_1+I)\cdot(r_2+I):=(r_1\cdot r_2)+I$$

Then $(R/I,+,\cdot)$ is a ring, and it's called the **quotient ring of** $R$ by $I$.

**Proof:** $\cdot$ is well-defined:

If $\begin{cases}r_1+I=r_1'+I\\r_2+I=r_2'+I\end{cases}$, then:

$$r_1-r_1'\in I,r_2-r_2'\in I$$

Then let $\begin{cases}r_1'=r_1+i_1\\r_2'=r_2+i_2\end{cases}$, then:

$$r_1'r_2'=r_1r_2+r_1i_2+i_1r_2+i_1i_2$$

Then $r_1'r_2'-r_1r_2\in I$, i.e. $r_1'r_2'+I=r_1r_2+I$.

Therefore $(r_1'+I)\cdot(r_2'+I)=(r_1+I)(r_2+I)$.

$+$ is well-defined by quotient group theory;

$(R/I,+,\cdot)$ associative and distributive.

## First Isomorphism Theorem of Rings
**Theorem:** Let $\Phi:R\to S$ be a ring homomorphism. Then the map:

$$\phi:R/\ker(\Phi)\to im(\Phi)$$

defined by $\phi(r+\ker(\Phi)):=\Phi(r)$ is a well-defined ring isomorphism.

**Proof:** $\phi$ is well-defined: If $\phi(r+\ker(\Phi))=\phi(r'+\ker(\Phi))$, then $\Phi(r)=\Phi(r')$. Therefore $\Phi(r-r')=0$, and hence $r-r'\in\ker(\Phi)$.

$\phi$ is a ring homomorphism: we know $\phi$ is a group homomorphism by first isomorphism theorem of groups. Therefore, we only need to check $\phi(rr')=\phi(r)\phi(r')$.

$\phi$ is bijective as in the first isomorphism of groups.

## Chinese Remainder Theorem
**Definition:** Let $R_i$ be rings. Then the **product ring**

$$\prod_iR_i=R_1\times\cdots\times R_k$$

has a ring structure given by:

$$(r_1,\cdots,r_k)+(r_1',\cdots,r_k'):=(r_1+r_1',\cdots,r_k+r_k')$$

$$(r_1,\cdots,r_k)\cdot(r_1',\cdots,r_k')=(r_1r_1',\cdots,r_kr_k')$$

**Remark:** $R_1\times R_2$ is not an integral domain in general:

$$(r_1,0)\cdot(0,r_2)=(r_1\cdot 0,0\cdot r_2)=(0,0)$$

**Definition:** Let $R$ be a commutative ring. We say $I_1,I_2\Delta R$ **coprime** if $I_1+I_2=R$.

**Example:** Let $R=\mathbb Z$, and $I_1=\left<m\right>=m\mathbb Z,I_2=\left<n\right>=n\mathbb Z$. Then:

$$I_1+I_2:=\left\{mp+nq|p,q\in\mathbb Z\right\}=\left<\gcd(m,n)\right>$$

Then $I_1$ and $I_2$ are coprime $\Leftrightarrow$ $I_1+I_2=\mathbb Z$ $\Leftrightarrow$ $\left<\gcd(m,n)\right>=\mathbb Z$ $\Leftrightarrow$ $\gcd(m,n)=1$. This generalizes our understanding of "coprime" from $\mathbb Z$ to any commutative ring $R$. Two elements $r_1,r_2$ are coprime in $R$ if $\left<r_1\right>+\left<r_2\right>=R$.

**Theorem:** Let $R$ be a commutative unital, and $I_1,\cdots,I_k\Delta R$ s.t. $I_i,I_j$ are pairwise coprime. Then we have a ring isomorphism:

$$\phi:R/(I_1\cap\cdots\cap I_k)\to R/I_1\times\cdots\times R/I_k$$

defined by $\phi(r+I_1\cap\cdots\cap I_k):=(r+I_1,\cdots,r+I_k)$.

**Proof:** Let $\Phi:R\to R/I_1\times\cdots\times R/I_k$ be a ring homomorphism $\Phi(r):=(r+I_1,\cdots,r+I_k)$. By first isomorphism theorem, we need to show:

(1) $\ker(\Phi)=I_1\cap\cdots\cap I_k$;

(2) $im(\Phi)=R/I_1\times\cdots\times R/I_k$.

For (1), 

$$
\begin{align}
r\in\ker(\Phi)&\Leftrightarrow r+I_l=0+I_l,\forall l
\\&\Leftrightarrow r\in I_l,\forall l
\\&\Leftrightarrow r\in I_1\cap\cdots\cap I_k
\end{align}
$$

For (2), fix $j\in\left\{1,\cdots,k\right\}$. Since $R$ is unital and $I_j,I_i$ are coprime for all $i\not=j$, so we have $z_i\in I_j,w_i\in I_i$ s.t. $z_i+w_i=1$. Then:

$$1=\left(1-\prod_{i\not=j}w_i\right)+\prod_{i\not=j}w_i$$

Since all $I_i$ are ideals, $\prod_{i\not=j}w_i\in\bigcap_{i\not=j}I_i$. Then let:

$$
\begin{cases}
x_j:=\left(1-\prod_{i\not=j}w_i\right)=1-\prod_{i\not=j}(1-z_i)
\\y_j:=\prod_{i\not=j}w_i
\end{cases}
$$

For each fixed $j$, we have $1=x_j+y_j$, where $x_j\in I_j,y_j\in\bigcap_{i\not=j}I_i$.

Then we check $\Phi$ is surjective: for each $(u_1+I_1,\cdots,u_k+I_k)\in R/I_1\times\cdots\times R/I_k$, we claim that $\Phi(u_1y_1+\cdots+u_ky_k)=(u_1+I_1,\cdots,u_k+I_k)$.

Proof of claim:

$$
\begin{align}
\Phi(u_1y_1+\cdots+u_ky_k)&=(\cdots,u_1y_1+\cdots+u_ky_k+I_l,\cdots)
\\&=(\cdots,u_ly_l+I_l,\cdots)
\\&=(\cdots,u_l(1-x_l)+I_l,\cdots)
\\&=(\cdots,u_l+I_l,\cdots)
\end{align}
$$

**Corollary:** Let $p_1,\cdots,p_k$ be distinct prime numbers. Then:

$$\mathbb Z/\left<p_1^{a_1}\cdots p_n^{a_n}\right>\cong \mathbb Z/\left<p_1^{a_1}\right>\times\cdots\times\mathbb Z/\left<p_n^{a_n}\right>$$

Therefore, for each $b_i\in\mathbb Z/\left<p_i^{a_i}\right>\cong \mathbb Z_{p_i^{a_i}}$, $\exists x\in\mathbb Z$,

$$\Phi(x)=(b_1+\left<p_1^{a_1}\right>,\cdots,b_n+\left<p_n^{a_n}\right>)$$

Then $x\equiv b_i(\operatorname{mod}\mathbb Z_{p_i^{a_i}})$ for all $i$.

## Prime and Maximal Ideals
**Definition:** Let $R$ be a commutative, unital ring. We say a proper ideal $(I\not=R)$ $I\Delta R$ is:

(a) **prime** if for all $a,b\in R$ such that $ab\in I$, then we must have $a\in I$ or $b\in I$;

(b) **maximal** if for all ideals $J\Delta R$ s.t. $I\subseteq J\subseteq R$, then $J=I$ or $J=R$.

**Remark:** Let $R=\mathbb Z$. Then $p\in\mathbb Z$ is a prime number iff $I=\left<p\right>$ is a prime ideal.

**Proof:** Let $a,b\in\mathbb Z$ such that $ab\in\left<p\right>$.

$$ab\in\left<p\right>\Leftrightarrow ab=pk,k\in\mathbb Z\Leftrightarrow p|ab\Leftrightarrow a\in\left<p\right>\text{ or }b\in\left<p\right>$$

**Remark:** Let $R=\mathbb Z$. Then $\left<n\right>$ is a maximal ideal iff $n$ is prime iff $\left<n\right>$ is prime.

**Remark:** Not all prime ideals are maximal, e.g. prime $\left<x\right>\subseteq\left<2,x\right>\not=\mathbb Z[x]$.

**Proposition 1:** Let $R$ be commutative unital, and $I\Delta R$. Then:

(a) $I$ is prime $\Leftrightarrow$ $R/I$ is integral domain;

(b) $I$ is maximal $\Leftrightarrow$ $R/I$ is a field.

**Proof:** (a) Let $(a+I),(b+I)\in R/I$. Then $(a+I)\cdot(b+I)=0+I\Leftrightarrow ab\in I\Rightarrow$ If $I$ is prime, then:

$$
\begin{align}
(a+I)(b+I)=0_{R/I}&\Leftrightarrow ab\in I
\\&\Leftrightarrow a\in I\text{ or }b\in I
\\&\Leftrightarrow a+I=0_{R/I}\text{ or }b+I=0_{R/I}
\end{align}
$$

(b) Suppose $I\subseteq J\subseteq R$ for some $J\Delta R$, then $I/I\subseteq J/I\subseteq R/I$.

Lemma: $\mathbb F$ is a field iff the only ideals of $\mathbb F$ are $\left\{0\right\}$ and $\mathbb F$.

Proof of lemma: let $I\Delta\mathbb F$ be nonzero. Take $0\not=a\in I$. Then $1=a\cdot a^{-1}\in I$. Therefore, $\forall x\in\mathbb F$, $x=x\cdot 1\in I$.

Therefore, $R/I$ is a field iff $J/I\Delta R/I$ must be $\left\{0\right\}$ or $R/I$. If $J/I=\left\{0\right\}$, then $J=I$; if $J/I=R/I$, then $J=R$.

**Corollary:** Let $R$ be commutative unital. If $I\Delta R$ is maximal, then $I\Delta R$ is prime (since a field must be an integral domain).

**Definition:** Let $R$ be commutative unital. We say $a\in R$ is prime if $\left<a\right>$ is a prime ideal.

**Definition:** Let $a,b\in R$ be commutative unital. We say $a$ **divides** $b$ (or $a|b$) if $\left<b\right>\subseteq\left<a\right>$ or equivalently, $b\in\left<a\right>$ or $\exists x\in R,s.t. ax=b$. We say $a$ and $b$ are **associates** if $a|b$ and $b|a$, i.e. $\left<a\right>=\left<b\right>$.

**Lemma 1:** Suppose $R$ is an integeral domain. Then $a\sim b\Leftrightarrow\exists x\in u(R),s.t.a=xb$.

**Proof:** $(\Leftarrow)$ $a=xb\Rightarrow a\in\left<b\right>\Rightarrow\left<a\right>\subseteq\left<b\right>$, since $x^{-1}a=b$ we get $\left<b\right>\subseteq\left<a\right>$. Then $\left<a\right>=\left<b\right>$.

$(\Rightarrow)$ $\left<a\right>\subseteq\left<b\right>\Leftrightarrow a=pb$ for some $p$;

$\left<b\right>\subseteq\left<a\right>\Leftrightarrow b=qa$ for some $q$.

Then $a=pqa\Leftrightarrow pq=1$ by cancellation property. Therefore, $p\in u(R),q\in u(R)$.

## Principal Ideal Domain
**Definition:** Let $R$ be an integral domain. We call $R$ a **principal ideal domain (PID)** if all ideals $I\Delta R$ are principal, i.e. all $I$ are of the form $I=\left<a\right>$.

## Irreducible Elements and Unique Factorization Domain
**Definition:** Let $R$ be commutative unital. An element $a\in R$ is **irreducible** if the following holds: whenever $\left<a\right>\subseteq\left<b\right>\subseteq R$ for some $b\in R$, we have $\left<b\right>=\left<a\right>$ ($a\sim b$) or $\left<b\right>=R$. i.e. $\left<a\right>$ is maximal among all principal ideals of $R$.

**Lemma:** Let $R$ be an integral domain. Then $a\in R$ is irreducible iff whenever $a=xy$, we have $a\sim x$ or $a\sim y$.

**Proof:** Suppose $a=xy$, then $\left<a\right>\subseteq\left<x\right>$ and $\left<a\right>\subseteq\left<y\right>$.

$(\Rightarrow)$: since $a$ is irreducible, $\left<a\right>=\left<x\right>$ ($a\sim x$) or $\left<x\right>=R$. If $\left<x\right>=R$, then $\exists x'\in R,s.t.xx'=1\in\left<x\right>=R$. Then $x$ is a unit. Therefore $a\sim y$.

$(\Leftarrow)$: Suppose $\left<a\right>\subseteq\left<b\right>$ for some $b$.

**Proposition 1:** Let $R$ be an integral domain. If $0\not=a\in R$ is prime, then $a$ is irreducible.

**Proof:** Suppose $a=xy$, then $\left<a\right>\subseteq\left<x\right>$ and $\left<a\right>\subseteq\left<y\right>$. On the other hand, we have $a|xy\Rightarrow a|x$ or $a|y$ since $a$ is prime. W.L.O.G., assume $a|x$, then $aa'=x\Rightarrow\left<x\right>\subseteq\left<a\right>$. Then $\left<a\right>=\left<x\right>\Leftrightarrow a\sim x$.

**Proposition 2:** Let $R$ be PID. Then all irreducibles are primes.

**Proof:** Let $x\in R$ be irreducible. Then $\left<x\right>$ is maximal among all ideals of the form $\left<b\right>$. Since all ideals are of the form $\left<b\right>$ in PID. Then $\left<x\right>$ is a maximal ideal. Therefore $\left<x\right>$ is prime ideal. Then $x$ is prime.

## Factorization Domain
**Definition:** Let $R$ be an integral domain. We say $R$ is a **factorization domain** if for all $0\not=x\in R$, there exists irreducible elements $x_1,\cdots,x_r$ such that:

$$x\sim x_1x_2\cdots x_r$$

or $x=ux_1x_2\cdots x_r$ for a unit $u\in U(R)$. i.e. one can factorize any $x$ into a **finite** product of irreducibles.

**Theorem:** $R$ is PID $\Rightarrow$ $R$ is a factorization domain.

**Definition:** Let $R$ be unital commutative. We say $R$ has the **ascending chain condition on principal ideals (ACCP)** if for all $I_1\subset I_2\subset I_3\subset\cdots$ ($I_i\Delta R$ are principal ideals) there exists $N$ such that $I_N=I_{N+1}=I_{N+2}=\cdots$.

**Lemma 1:** All PID satisfy ACCP.

**Proof:** Suppose $I_1\subset I_2\subset I_3\subset\cdots$ in $R$. Consider $I:=\bigcup_{n=1}^\infty I_n$, then $I\Delta R$. So $I=\left<r\right>$ for some $r\in R$ since $R$ is PID. Then $r\in I_m$ for some $m\in\mathbb N$. Then $r\in I_n,\forall n\geq m$. Therefore $I=\left<r\right>\subseteq I_n,\forall n\geq m$. Since $I_n\subseteq I$ by definition, $I_n=I,\forall n\geq m$.

**Lemma 2:** If $R$ satisfies ACCP, then $R$ is a factorization domain.

**Proof:** Let $F:=\left\{x\in R|x\sim x_1\cdots x_r,x_i\text{ irreducible}\right\}$. Then (a) $1\in F$; (b) all irreducible $x\in R$ are in $F$; (c) $F$ is closed under multiplication. W.T.S. $R=F$.

Suppose on contrary $\exists x_0\in R\backslash F$. Then by (b) $x_0$ is reducible. Then $x_0=y_0z_0$ where $y_0,z_0$ are not units. Then $x_0\not\sim y_0$ and $x_0\not\sim z_0$ and therefore $\left<x_0\right>\not=\left<y_0\right>$ and $\left<x_0\right>\not=\left<z_0\right>$. By (c), either $y_0\in R\backslash F$ or $z_0\in R\backslash F$ (or both). W.L.O.G. let $x_1=y_0\in R\backslash F$. Then:

$$x_0=x_1z_0\Rightarrow x_0\in\left<x_1\right>\Rightarrow \left<x_0\right>\subsetneq\left<x_1\right>$$

Continue the same argument on $x_1$, we have:

$$\left<x_0\right>\subsetneq\left<x_1\right>\subsetneq\left<x_2\right>\subsetneq\cdots$$

contradicting ACCP. Then there is no such $x_0\in R\backslash F$ and we are done.

**Conclusion:** By Lemma 1 and Lemma 2, we prove the theorem. In PID, one can factorize any $x\in R$ into finite product of irreducibles.

**Proposition 1:** Let $R$ be an integral domain. Then any factorization of $x\in R$ into prime factors are unique (up to permutation and units), i.e. if:

$$x_1\cdots x_r\sim y_1\cdots y_s(x_i,y_j\text{ are primes})$$

Then (1) $r=s$, and (2) $\exists\sigma\in S_r,s.t. x_i=y_{\sigma(i)}$.

**Proof:** We will prove the following stronger statement: let $x_1,\cdots,x_r$ be primes, $y_1,\cdots,y_n$ be irreducibles s.t. $x_1x_2\cdots x_r\sim y_1y_2\cdots y_n$. Then $r=n$ and $\exists\sigma\in S_r$ s.t. $x_i\sim y_{\sigma(i)}$.

Prove by induction on $r$.

$r=0:$ then $LHS=1$, $y_1y_2\cdots y_n\sim 1$. Therefore $y_i$ are units. Since we assume $x_i,y_i$ are nonunits, we must have $n=0$.

Suppose the conclusion holds for $0\leq r\leq s-1$. Consider $r=s$ and $x_1\cdots x_{s-1}x_s\sim y_1y_2\cdots y_n$. Then $x_s|y_1y_2\cdots y_n\Rightarrow x_s|y_j$ for some $j$ $\Rightarrow y_j=x_s\cdot a$ for some $a\in R\Rightarrow y_j\sim x_s$ or $y_j\sim a$. If $y_j\sim a$, $y_j=u'a=x_sa\Rightarrow u'=x_s$. But $x_s$ is not a unit. Then $y_j\sim x_s$.

Therefore, we can cancel $x_s,y_j$ such that $x_1\cdots x_{s-1}\sim y_1\cdots y_{j-1}y_{j+1}\cdots y_n$. By induction, $s-1=n-1$ and $\exists\sigma\in S_{s-1},s.t. x_i\sim y_{\sigma(i)},\forall i=1,\cdots,s-1$.

Let $\sigma'\in S_s$ by $\sigma'(j):=\begin{cases}\sigma(j),j=1,\cdots,s-1\\\sigma(s)=i\end{cases}$.

Therefore, $x_1\cdots x_{s-1}x_s\sim y_1\cdots y_n$ implies $\exists\sigma\in S_s, s.t. x_i\sim y_{\sigma(i)},\forall i=1,\cdots,s$.

**Corollary 1:** Let $R$ be PID. Then $\forall x\in R$, $x$ can be uniquely factorized into a finite product of irreducibles (primes).

**Definition:** Let $R$ be an integral domain. We say $R$ is a **unique factorization domain (UFD)** if we have unique factorization into irreducible elements in $R$. If $R$ is PID, then $R$ is UFD.

**Conclusion:** Fields $(\mathbb Q)$ $\subsetneq$ PID $(\mathbb Q[x])$ $\subsetneq$ UFD $(\mathbb Z[x])$ $\subsetneq$ ID $(\mathbb Z[\sqrt{-5}])$.

## Euclidean Domain
**Definition:** Let $R$ be ID. An **Euclidean function** on $R$ is:

$$N:R\backslash\left\{0\right\}\to\mathbb{N}\backslash\left\{0\right\}$$

such that $\forall a,b\in R(b\not=0)$, either (1) $b|a$ or (2) $\exists q\in R,r\in R\backslash\left\{0\right\}$, such that $a=bq+r$ with $N(r)<N(b)$.

**Definition:** An ID $R$ is an **Euclidean domain** if $R$ has at least one Euclidean function. So $\mathbb Z,\mathbb F[x]$ are EDs.

**Proposition:** $\mathbb Z[i]$ is an Euclidean domain with $N(a+bi)=a^2+b^2$.

**Proof:** Let $\alpha,\beta\in\mathbb Z[i]$. Assume $\beta\not=0$. Then consider $\frac{\alpha}{\beta}=c_1+c_2i,c_1,c_2\in\mathbb Q$. Let $n_1,n_2\in\mathbb Z$ be the closest integers of $c_1,c_2\in\mathbb Q$, so that $|n_i-c_i|\leq\frac{1}{2}$, and let $q:=n_1+n_2i$. Then:

$$\frac{\alpha}{\beta}=q+((c_1-n_1)+(c_2-n_2)i)$$

Therefore:

$$\alpha=\beta q+((c_1-n_1)+(c_2-n_2)i)\beta$$

Let $r:=((c_1-n_1)+(c_2-n_2)i)\beta=\alpha-\beta q$, since $\alpha,\beta,q\in\mathbb Z[i], r\in\mathbb Z[i]$, then:

$$
\begin{align}
N(r)&=N((c_1-n_1)+(c_2-n_2)i)N(\beta)
\\&\leq\left[\left(\frac{1}{2}\right)^2+\left(\frac{1}{2}\right)^2\right]N(\beta)
\\&=\frac{1}{2}N(\beta)<N(\beta)
\end{align}
$$

**Theorem:** If $R$ is ED, then $R$ is PID. Therefore, $\mathbb Z[i]$ is PID.

**Proof:** Would be introduced in the next session.

**Observations:**

- If $m$ is not prime in $\mathbb Z$, then $m$ is not prime in $\mathbb Z[i]$;
- $u(\mathbb Z[i])=\left\{\pm 1,\pm i\right\}$. Therefore $\alpha\in u(\mathbb Z[i])\Leftrightarrow N(\alpha)=1$;
- If $N(\beta)=p$ is prime in $\mathbb Z$, then $\beta$ is prime in $\mathbb Z[i]$ since $\beta=\alpha\cdot\delta$, then $p=N(\beta)=N(\alpha)N(\delta)\Rightarrow N(\alpha)=1$ or $N(\delta)=1$. Then $\alpha$ or $\delta$ is a unit in $\mathbb Z[i]$. Then $\beta\sim\alpha$ or $\beta\sim\delta$, i.e. $\beta$ is irreducible (and prime).

**Lemma 1:** Let $p$ be a prime integer. Then either (1) $p$ is a Gaussian prime in $\mathbb Z[i]$, or (2) $p=(a+bi)(a-bi)$ for some Gaussian primes $a+bi,a-bi$.

**Proof:** Suppose $p$ is not a Gaussian prime. Then $p=\alpha\cdot\delta$ for some nonunits $\alpha,\delta$. Then:

$$p^2=N(p)=N(\alpha)N(\delta)\Rightarrow N(\delta)=N(\alpha)=p$$

Then $\alpha,\delta$ are Gaussian primes. Let $\alpha=a+bi$, then $p=a^2+b^2=N(a+bi)=N(a-bi)$, where $a^2+b^2=(a+bi)(a-bi)$. Therefore $p=(a+bi)(a-bi)$ and $a+bi,a-bi$ is a Gaussian prime.

**Lemma 2:** Let $a+bi\in\mathbb Z[i]$ with $a,b\not=0$. Then $a+bi$ is Gaussian prime iff $a^2+b^2=p, p$ is a prime integer.

**Proof:** $(\Leftarrow):$ is done in observations;

$(\Rightarrow):$ Suppose $a+bi$ is Gaussian prime, then $a-bi=\overline{a+bi}$ is also Gaussian prime.

Consider $(a+bi)(a-bi)=p_1p_2\cdots p_r$, where $p_i$ are primes in $\mathbb Z$. By $\mathbb Z[i]$ is ED, $\mathbb Z[i]$ is PID and UFD, and $r\leq 2$.

If $r=2$, $(a+bi)(a-bi)=p_1p_2$, $p_1,p_2$ must be primes. Then $p_1\sim(a\pm bi),p_2\sim(a\mp b_i)$. Therefore $p_1=u\cdot(a\pm bi)$, but $u\in\left\{\pm 1,\pm i\right\}$, contradicts. Therefore $r=1$, then $(a+bi)(a-bi)=p_1\Rightarrow a^2+b^2=p_1$ prime.

**Conclusion:** (1) If $n\in\mathbb Z$ is not a prime number in $\mathbb Z$. Then $n$ is not Gaussian prime;

(2) Prime $p\in\mathbb Z$ is either a Gaussian prime, or $p=(a+bi)(a-bi)$, where $a\pm bi$ are Gaussian primes;

(3) $a+bi\in\mathbb Z[i],a,b\not=0$ is Gaussian prime iff $a^2+b^2=p,p\in\mathbb Z$ prime number.

**Theorem:** Let $p$ be a prime integer. Then $p$ is Gaussian prime iff $p\equiv 3(\operatorname{mod} 4)$.

**Corollary:** The Gaussian primes in $\mathbb Z[i]$ must be one of the forms:

(1) $p\in\mathbb Z,p\equiv 3(\operatorname{mod}4)$;

(2) $a+bi\in\mathbb Z[i],a,b\not=0,a^2+b^2=p$;

(3) $pi\in\mathbb Z,p\equiv 3(\operatorname{mod}4)$.

**Proof:** $(\Leftarrow):$ Prove by contrapositive. If $p$ is not Gaussian prime. Then conclusion (2) says:

$$p=(a+bi)(a-bi)=a^2+b^2\equiv 0,1,\text{or }2(\operatorname{mod}4)$$

Then if $p\equiv 3(\operatorname{mod}4)$, $p$ is a Gaussian prime.

$(\Rightarrow):$ Prove by contrapositive. Suppose $p\equiv 1(\operatorname{mod}4)$. Then by Lagrange's Lemma:

$$p|m^2+1$$

for some integer $m$. Then $p|(m+i)(m-i)$. However $p\not|(m+i)$, otherwise we have $pr=m+i\Rightarrow r=\frac{m}{p}+\frac{1}{p}i$, but $\frac{1}{p}$ is not an integer. Similarly $p\not|(m-i)$. Then $p$ is not a prime in $\mathbb Z[i]$.

**Corollary 2:** (Fermat's Theorem of 2 squares) If $p=4n+1$ is a prime, then $\exists a,b\in\mathbb Z$ such that $p=a^2+b^2$.

## Dedekind-Hesse Function
**Definition:** Let $R$ be an integral domain. A **Dedekind-Hesse function** is a map:

$$N:R\backslash\left\{0\right\}\to\mathbb N\backslash\left\{0\right\}$$

s.t. $\forall a,b\in R,b\not=0$, then either (1) $b|a$; or (2) $\exists p,q,r\in R,ap=bq+r$ such that $N(r)<N(b)$.

**Remark:** Euclidean functions (Norm functions) are D-H functions.

**Theorem:** Let $R$ be ID. Then $R$ is a PID iff $R$ has a D-H function.

**Proof:** $(\Rightarrow):$ $\forall r\in R\backslash\left\{0\right\}$, define:

$$N(r):=\text{No. of irred. factors in the factorization of }r$$

This is well-defined since $R$ is UFD. Then consider $\forall a,b\in R,b\not=0$ such that $b\not|a$. Then consider:

$$\left<b\right>\subsetneq\left<a,b\right>=\left<r\right>$$

since $R$ is PID. Then (1) $\left<b\right>\subsetneq\left<r\right>$, and (2) $\exists p',q'\in R$ such that:

$$r=p'a+q'b$$

By (1), $r|b$ and $r\not\sim b$, then $N(b)>N(r)$ (Recall the definition of $N$).

(2) says $ap'=b(-q')+r$, where $N(r)<N(b)$.

$(\Leftarrow):$ Let $R$ be ID with D-H, and $I\Delta R$ for any ideal. Let $m:=\min_{I\backslash\left\{0\right\}}\left\{N(r)\right\}$ and let $b\in I\backslash\left\{0\right\}$ such that $N(b)=m$.

Claim: $I=\left<b\right>$.

Proof of claim: $\forall a\in I$, if $b|a$ then $a\in\left<b\right>$. If not, $\exists p,q,r\in R$ such that $ap=bq+r$ such that $N(r)<N(b)$. However $N(b)$ is the smallest among $N(r)$, there is a contradiction.

Therefore $I=\left<b\right>$. Then $R$ is PID.

**Corollary:** If $R$ is ED, then $R$ is PID.

## Polynomial Rings
**Theorem 1:** (Fundamental Theorem of Algebra) All irreducible (prime elements) in $\mathbb C[x]$ are associated to $x-\alpha,\alpha\in\mathbb C$.

**Remark:** If $\mathbb F$ is a field, then $\mathbb F[x]$ is PID. Then $f\in\mathbb F[x]$ is irreducible (prime) iff $\mathbb F[x]/\left<f\right>$ is a field. So we can construct new fields by studying irreducible $f(x)$.

**Proposition:** Let $\phi:R\to S$ be a unital ring homomorphism between IDs. Then the map:

$$\overset{\sim}{\phi}:R[x]\to S[x]$$

given by:

$$\overset{\sim}{\phi}\left(\sum_{i=0}^na_ix^i\right):=\sum_{i=0}^n\phi(a_i)x^i$$

is a unital ring homomorphism.

**Theorem 2:** (Reduction test) Let $f\in\mathbb Z[x]$ be a monic polynomial and $p$ is prime number such that:

$$\overset{\sim}{f}:=\phi_p(f)\in\mathbb Z_p[x]$$

is irreducible. Then $f$ is irreducible in $\mathbb Z[x]$. Example: $\phi_2(x^3+3x+7)=x^2+x+1$ in $\mathbb Z_2[x]$. And $x^2+x+1$ is irreducible in $\mathbb Z_2[x]$. Then $x^3+3x+7$ is irreducible in $\mathbb Z[x]$.

**Proof:** Suppose $f=gh\in\mathbb Z[x]$. Then $\overset{\sim}{f}=\overset{\sim}{g}\overset{\sim}{h}\in\mathbb Z_p[x]$. Since $\overset{\sim}{f}$ is irreducible, $\deg(\overset{\sim}{g})=0$ or $\deg(\overset{\sim}{h})=0$. Then:

$$\deg(g)+\deg(h)=\deg(f)=\deg(\overset{\sim}{f})$$

$$\deg(\overset{\sim}{f})=\deg(\overset{\sim}{g})+\deg(\overset{\sim}{h})$$

and:

$$\deg(\overset{\sim}{g})\leq\deg(g)$$

$$\deg(\overset{\sim}{h})\leq\deg(h)$$

Therefore:

$$\deg(g)=\deg(\overset{\sim}{g}),\deg(h)=\deg(\overset{\sim}{h})$$

Then $\deg(g)=0$ or $\deg(h)=0$.

Therefore $f$ is irreducible.

**Remark:** Converse of Theorem 2 does not hold, e.g. $f(x)=x^2+2$ is irreducible in $\mathbb Z[x]$, but $\overset{\sim}{f}(x)=x^2$ is reducible in $\mathbb Z_2[x]$.

**Theorem 3:** (Eisenstein's Criterion) Suppose $f(x)=a_nx^n+\cdots+a_1x+a_0\in\mathbb Z[x]$ satisfies $\gcd(a_n,\cdots,a_0)=1$, i.e. $f$ is primitive, and $p$ is a prime number such that:

(1) $p|a_i,\forall 0\leq i<n$;

(2) $p\not|a_n$;

(3) $p^2\not|a_0$.

Then $f(x)$ is irreducible in $\mathbb Z[x]$.

**Proof:** Use $\sim:\mathbb Z[x]\to\mathbb Z_p[x]$. Then consider $f=gh\in\mathbb Z[x]$:

$$\overset{\sim}{f}=[a_n]_px^n\in\mathbb Z_p[x]$$

Then $\overset{\sim}{f}\sim x^n$. Consider $x^n=\overset{\sim}{g}\cdot\overset{\sim}{h}\in\mathbb Z_p[x]$. Then $\overset{\sim}{g}\sim x^i, \overset{\sim}{h}\sim x^{n-i}$.

Suppose $i\not=0,n$, then the constant term of $g$ is a multiple of $p$. Similarly, the constant term of $h$ is also a multiple of $p$. Then the constant term of $f=gh$ is a multiple of $p^2$, which causes a contradiction.

Then $i=0$ or $n$. $\overset{\sim}{g}$ or $\overset{\sim}{h}$ is a constant function in $\mathbb Z_p[x]$. Then:

$$\deg(g)+\deg(h)=\deg(f)=\deg(\overset{\sim}{f})$$

by property (2). And $\deg(\overset{\sim}{g})\leq\deg(g),\deg(\overset{\sim}{h})\leq\deg(h)$. Then:

$$\deg(\overset{\sim}{g})=\deg(g),\deg(\overset{\sim}{h})=\deg(h)$$

Then $g$ or $h$ is constant. Since $f$ is primitive, $g=1$ or $h=1$. Then $f$ is irreducible.

**Theorem:** (Gauss Lemma) A nonconstant polynomial of $f\in\mathbb Z[x]$ is irreducible iff $f\in\mathbb Q[x]$ is irreducible and $f$ is primitive.

**Remark:** Let $f$ be irreducible in $\mathbb Z[x]$, then $f$ is irreducible in $\mathbb Q[x]$. Therefore $\mathbb Q[x]/\left<f\right>$ is a field and $\mathbb Q$ is a subfield of it.

**Proof:** $(\Leftarrow):$ Suppose $f\in\mathbb Z[x]$ and $f=gh,g,h\in\mathbb Z[x]$. By hypothesis, $f$ is irreducible in $\mathbb Q[x]$ and $g,h\in\mathbb Z[x]\subseteq\mathbb Q[x]$. Therefore, $\deg(g)=0$ or $\deg(h)=0$. Then $g$ or $h$ must be a constant integer.

By hypothesis again, since $f$ is primitive, this constant integer can only be $1$ or $-1$.

Then $g$ or $h$ is a unit in $\mathbb Z[x]$.

$(\Rightarrow):$ If $f$ is irreducible in $\mathbb Z[x]$, then obviously $f$ is primitive, otherwise:

$$f=a_nx^n+\cdots+a_1x+a_0$$

and $q=\gcd(a_n,\cdots,a_0)>1$, which is not a unit, and:

$$f=q\left(\frac{a_n}{q}x^n+\cdots+\frac{a_1}{q}x+\frac{a_0}{q}\right)$$

contradicting $f$ being irreducible in $\mathbb Z[x]$.

Now suppose $f=g\cdot h,g,h\in\mathbb Q[x]$. Let $\lambda\in\mathbb N$ be the smallest positive integer such that $\exists\alpha\in\mathbb Q\backslash\left\{0\right\}$ with:

$$
\begin{cases}
\alpha\cdot h\in\mathbb Z[x]
\\\lambda\cdot\alpha^{-1}\cdot g\in\mathbb Z[x]
\end{cases}
$$

Let $g':=\lambda\alpha^{-1}g,h':=\alpha h$.

Claim: $\lambda=1$. Suppose on contrary $\exists p|\lambda$, then $p|\lambda f$. This means the coefficients of $\lambda f\in\mathbb Z[x]$ are multiples of $p$.

Therefore, $p|(\lambda\alpha^{-1}g)\cdot(\alpha h)\Rightarrow p|g'h'$. Then $\overset{\sim}{g'}\cdot\overset{\sim}{h'}\equiv 0$ in $\mathbb Z_p[x]$. Then $\overset{\sim}{g'}\equiv 0$ or $\overset{\sim}{h'}\equiv 0$ in $\mathbb Z_p[x]$. Then $p|g'$ or $p|h'$ in $\mathbb Z[x]$.

Therefore, $\frac{\lambda}{p}\alpha^{-1}g\in\mathbb Z[x],\alpha h\in\mathbb Z[x]$ or $\frac{\lambda}{p}\left(\frac{\alpha}{p}\right)^{-1}g\in\mathbb Z[x],\frac{\alpha}{p}=h\in\mathbb Z[x]$, contradicting minimality of $\lambda$.

Then $p\not|\lambda$ for all prime number $p$. Therefore $\lambda=1$.

Therefore, we have $\alpha\in\mathbb Q\backslash\left\{0\right\}$ s.t. $f=(\alpha^{-1}g)(\alpha h)$, where $\alpha^{-1}g,\alpha h\in\mathbb Z[x]$.

Then $\alpha^{-1}g$ or $\alpha h$ is a unit. Since $\alpha$ is a unit, $g$ or $h$ is a unit.

**Theorem:** $\mathbb Z[x]$ is UFD.

**Proof:** Let $f\in\mathbb Z[x]$ be primitive.

Claim: $f$ can be factorized into $f=g_1\cdots g_n$, $g_i\in\mathbb Z[x]$ is primitive and irreducible.

Now use induction on $\deg(f)$.

True for $\deg(f)=0$ or $1$. So assume claim holds for $\deg(f)<k$. Then for $f$ with $\deg(f)=k$ and primitive:

if $f$ is irreducible, it holds;

if $f=h_1h_2, h_1,h_2\in\mathbb Z[x]$ are not units:

(1) $\deg(h_1)=0$ or $\deg(h_2)=0$, then $h_1$ or $h_2$ is equal to constant $\not=\pm 1$. Since $f$ is primitive, this will not hold;

(2) $\deg(h_1)>0,\deg(h_2)>0$, we can prove by induction.

Then we are done. Therefore $\mathbb Z[x]$ is a factorization domain.

To see why $\mathbb Z[x]$ is UFD, note that we can factorize any primitive $f\in\mathbb Z[x]$ into irreducibles (primitive). To see the factorization is unique, suppose:

$$f=g_1\cdots g_n=h_1\cdots h_m$$

where $g_i,h_j\in\mathbb Z[x]$ is primitive and irreducible. Then since $\mathbb Z[x]\subseteq\mathbb Q[x]$, and by Gauss Lemma, $g_i,h_j\in\mathbb Q[x]$ are irreducibles. By unique factorization of $\mathbb Q[x]$, we have $n=m$, and $\exists\sigma\in S_n$, such that $g_i\sim h_{\sigma(i)}$ in $\mathbb Q[x]$. Therefore, $g_i=h_{\sigma(i)}\cdot u$, where $u$ is a unit in $\mathbb Q[x]$. Since $g_i,h_{\sigma(i)}$ are primitive, $u\in\left\{\pm 1\right\}$. Then $g_i\sim h_{\sigma(i)}$ in $\mathbb Z[x]$.

**Remark:** If $R$ is UFD, then $R[x]$ is UFD. To prove it, use field of fractions:

$$F=Frac(R)=\left\{f(x)/g(x)\large|\small\begin{cases}f(x)\in R[x]\\g(x)\in R[x]\backslash\left\{0\right\}\end{cases}\right\}$$

and the fact that $F[x]$ is a PID (UFD).

## Fields
- Number field: a subfield of $\mathbb C$;
- Finite field: field $F$ with $|F|<\infty$;
- Function field: $Frac(\cdot)$.

## Field Extension and Degree
**Motivation:** Given $\mathbb F$, construct a "bigger" field $\mathbb K$ that "contains" $\mathbb F$, i.e. we have injective unital ring (or field) homomorphism: $i:\mathbb F\to\mathbb K$.

**Definition:** Let $\mathbb F$ and $\mathbb K$ be fields. We say $\mathbb F$ is a **subfield** of $\mathbb K$ or $\mathbb K$ is a **field extension** of $\mathbb F$ if there is an injective unital field homomorphism:

$$i:\mathbb F\to\mathbb K$$

In this case, $\mathbb K$ is a vector space over $\mathbb F$, i.e. $\exists \cdot:\mathbb F\times\mathbb K\to\mathbb K$ such that $0\cdot x=0,1\cdot x=x,\alpha\cdot(x+y)=\alpha\cdot x+\alpha\cdot y$.

The **degree of extension** is defined as $[\mathbb K:\mathbb F]:=\dim_{\mathbb F}(\mathbb K)$ as a vector space of $\mathbb F$.

**Theorem 1:** Let $\mathbb F$ be a field, and $p(x)\in\mathbb F[x]$ is irreducible, $\deg(p)=d$. Then $\mathbb K:=\mathbb F[x]/\left<p\right>$ is a field extension of $\mathbb F$ such that $[\mathbb K:\mathbb F]=d$. Moreover, $\exists\alpha\in\mathbb K$ such that $\mathbb K=\mathbb F[\alpha]:=\left\{a_n\alpha^n+\cdots+a_1\alpha+a_0|a_i\in\mathbb F\right\}$ and $p(\alpha)=0$ in $\mathbb K$.

**Example:** $\mathbb F=\mathbb Q,p(x)=x^3-2\in\mathbb Q[x]$ is irreucible by Eisenstein. Then $[\mathbb K:\mathbb Q]=3$, and:

$$K=Span_{\mathbb Q}\left\{1,\alpha,\alpha^2\right\}=\left\{a_2\alpha^2+a_1\alpha+a_0|a_i\in\mathbb Q\right\}$$

with $\alpha^3=2$. Then $\mathbb K$ is a field containing $\mathbb Q$ and a cubic root of $2$.

**Proof:** Since $p$ is irreducible $\Leftrightarrow$ $\left<p\right>$ is maximal ideal in $\mathbb F[x]$ $\Leftrightarrow$ $\mathbb K$ is a field.

Let's study $\dim_{\mathbb F}\mathbb K$: consider $\alpha:=x+\left<p\right>\in\mathbb K$.

Then:

$$\begin{align}
p(\alpha)&=b_m\alpha^m+\cdots+b_1\alpha+b_0(1_{\mathbb K})\in\mathbb K
\\&=b_m(x^m+\left<p\right>)+\cdots+b_1(x+\left<p\right>)+b_0(1+\left<p\right>)
\\&=(b_mx^m+\cdots+b_1x+b_01)+\left<p\right>
\\&=p(x)+\left<p\right>
\\&=0+\left<p\right>
\\&=0_{\mathbb K}
\end{align}$$

Then $\left\{1_{\mathbb K},\alpha,\cdots,\alpha^{m-1}\right\}$ are linearly independent in $\mathbb K$. More precisely, $\alpha^m$ is a linear combination of $\left\{\alpha^{m-1},\cdots,\alpha,1\right\}$.

Similarly, $\forall n\geq m$, $\alpha^n$ is also a linear combination of $\left\{\alpha^{m-1},\cdots,\alpha,1\right\}$.

Claim: $\left\{\alpha^{m-1},\cdots,\alpha,1\right\}$ is a basis of $\mathbb K$ over $\mathbb F$.

(1) It is a spanning set:

Take any element $k:=(c_lx^l+\cdots+c_1x+c_0)+\left<p\right>\in\mathbb K$,

$$\begin{align}k&=(c_lx^l+\left<p\right>)+\cdots+(c_1x+\left<p\right>)+(c_0+\left<p\right>)\\&=c_l\alpha^l+\cdots+c_1\alpha+c_0\end{align}$$

(2) Linearly independent:

Suppose:

$$d_{m-1}\alpha^{m-1}+\cdots+d_1\alpha+d_0\cdot 1=0_{\mathbb K}$$

for $d_i$ not all zeros in $\mathbb F$.

Then:

$$(d_{m-1}x^{m-1}+\cdots+d_1x+d_0)+\left<p\right>=0_{\mathbb K}$$

Then:

$$d_{m-1}x^{m-1}+\cdots+d_1x+d_0\in\left<p\right>$$

Hence $\exists r(x)$, $p(x)\cdot r(x)=d_{m-1}x^{m-1}+\cdots+d_1x+d_0$. However, $\deg(LHS)\geq\deg(p(x))=m,\deg(RHS)=m-1$, which causes a contradiction.

Hence $[\mathbb K:\mathbb F]=m$.

**Definition:** Let $\mathbb F$ be a field and $\mathbb L$ be a field extension of $\mathbb F$. An element $\alpha\in\mathbb L$ is:

- **algebraic** if $\exists$ a monic polynomial $p(x)\in\mathbb F[x]$ s.t. $p(\alpha)=0$;
- **transcendental** otherwise.

**Proposition 1:** Let $\beta\in\mathbb L$ be algebraic. Consider:

$$I:=\left\{f(x)\in\mathbb F[x]|f(\beta)=0\right\}$$

Then $I\Delta\mathbb F[x]$ is an ideal; and $I=\left<p\right>$ for some monic $p\in\mathbb F[x]$.

(a) $p(x)$ is a polynomial with smallest degree in $I$;

(b) $p(x)$ is irreducible.

**Proof:** (a) Division algorithm. Suppose on contrary $\exists q(x)\in I$ with $\deg(q)<\deg(p)$, then $p\not|q$. There is a contradiction;

(b) Suppose on contrary $p(x)=h_1(x)h_2(x)$, then $p(\beta)=h_1(\beta)h_2(\beta)=0$. Therefore $h_1(\beta)=0$ or $h_2(\beta)=0$. Assume $h_1(\beta)=0$, W.L.O.G., $\deg(h_1)\leq\deg(p)$. If $\deg(h_1)=\deg(p)$, $h_1\sim p$. If $\deg(h_1)<\deg(p),h_1|p$, there is a contradiction by (a).

**Definition:** Let $\mathbb F$ be a field, $\beta\in\mathbb L$ in a field extension of $\mathbb F$. The polynomial $p(x)$ appearing in proposition 1 above is called the **minimal polynomial** of $\beta$ over $\mathbb F$.

**Corollary:** Let $\mathbb F$ be a field, $\beta\in\mathbb L$ be algebraic over $\mathbb F$. Then we have an isomorphism of fields:

$$\mathbb F[\beta]\cong\mathbb F[x]/\left<p(x)\right>,\beta\to x+\left<p(x)\right>$$

Then $\mathbb F[\beta]:=\left\{a_n\beta^n+\cdots+a_1\beta+a_0|a_i\in\mathbb F,n\in\mathbb N\right\}$.

**Proof:** Construct the map:

$$\mathbb F[x]\to\mathbb F[\beta]:\sum_{i=0}^na_ix^i\to\sum_{j=0}^na_i\beta^i$$

Then the kernel of the map is precisely $I=\left<p(x)\right>$. So the result follows by the first isomorphism theorem of rings.

**Definition:** Let $\mathbb F$ be a field, $\beta\in\mathbb L$ be a field extension of $\mathbb F$ s.t. $\beta$ is algebraic over $\mathbb F$ with minimal polynomial $p(x)$ of degree $m$. Then we say $\mathbb F(\beta)=Span_{\mathbb F}\left\{1,\beta,\cdots,\beta^{m-1}\right\}$ be the field extension of $\mathbb F$ with $\beta$ adjoint to $\mathbb F$. This is the smallest field containing $\mathbb F$ and $\beta$ at the same time.

**Theorem 2:** (Tower law) Let $\mathbb F\subseteq\mathbb K\subseteq\mathbb L$ be field extensions. Then $[L:F]=[L:K][K:F]$.

**Proof:** Let $\left\{e_1,\cdots,e_n\right\}$ be a basis of $\mathbb K$ over $\mathbb F$, $\left\{f_1,\cdots,f_m\right\}$ be a basis of $\mathbb L$ over $\mathbb K$.

Claim: $\left\{e_if_j|1\leq i\leq n,1\leq j\leq m\right\}$ is a basis of $\mathbb L$ over $\mathbb K$.

Spanning set: let $x\in\mathbb L$, then $x=\sum_{j=1}^n\mu_jf_j,\mu_j\in\mathbb K$. For any $\mu_j\in\mathbb K$, we have $\sum_{i=1}^nv_{ij}e_i=\mu_j,v_{ij}\in\mathbb F$. Then:

$$x=\sum_{i=1}^n\sum_{j=1}^mv_{ij}(e_if_j),v_{ij}\in\mathbb F$$

Linear independence: suppose 

$$\sum_{i=1}^n\sum_{j=1}^m\beta_{ij}e_if_j=0,\beta_{ij}\in\mathbb F$$

then:

$$\sum_{j=1}^m\left(\sum_{i=1}^n\beta_{ij}e_i\right)f_j=0$$

By linear independence of $\left\{f_j\right\}$, we have:

$$\sum_{i=1}^n\beta_{ij}e_i=0,\forall j=1,\cdots,m$$

By linear independence of $\left\{e_i\right\}$, we have:

$$\beta_{ij}=0,\forall i,j$$

## Ruler and Compass Constructions
Basis constructions of ruler and compass:

(a) Draw a line perpendicular to a given line $l$; choose an arbitary point $x$ on $l$ and draw a circle centered at $x$ intersecting with $l$ at $a,b$; then draw circles centered at $a,b$ respectively with radius $|ab|$; connect the two intersecting points;

(b) Bisect a line segment; draw circles centered at boundary points $a,b$ respectively with radius $|ab|$; connect the two intersecting points and the line intersects with the segment at its midpoint;

(c) Draw a line parallel to $l$; draw a circle centered at $a$ over the line which intersects with the line at $x,y$; then apply (b) to find the midpoint $m$ of $x,y$; connect $a,m$ and apply (a);

Given two line segments of lengths $\alpha,\beta$:

(d) Draw a line with length $\alpha+\beta$;

(e) Draw a line with length $\alpha-\beta$;

(f) Draw a triangular with lengths $\alpha(\beta+1),(\beta+1)$;

(g) Draw a triangular with lengths $\frac{\alpha}{\beta},1$;

(h) Draw a triangular with lengths $\sqrt\alpha 1$.

**Definition:** Given $(0,0)$ and $(1,0)\in\mathbb R^2$. We say $c\in\mathbb R$ is **constructable** if we can obtain $(c,0)\in\mathbb R^2$ by using intersections of straight lines and circles.

**Example:** all $\frac{p}{q}\in\mathbb Q$ are constructable: we can get $p,q\in\mathbb N$ easily by adding $1$. Then apply (g) to get $\frac{p}{q}$. Also, $\sqrt\frac{p}{q}$ is constructable by (h).

**Proposition:** If $c\in\mathbb K$, where $\mathbb K$ is a subfield of $\mathbb R$ containing $\mathbb Q$ obtained by the field extensions:

$$\mathbb Q=K_0\subseteq K_1\subseteq K_2\subseteq\cdots\subseteq K_r=\mathbb K$$

where $[K_{i+1}:K_i]=1$ or $2$, then $c$ is constructable.

**Proof:** By induction on $r$.

$r=0,\mathbb K=K_0=\mathbb Q$ is constructable.

Suppose the proposition holds for all:

$$\mathbb Q\subseteq K_0\subseteq\cdots\subseteq K_m=\mathbb K$$

(1) $[K_{m+1}:K_m]=1$, $K_{m+1}=K_m$ and hence all $c\in K_{m+1}=K_m$ are constructable;

(2) $[K_{m+1}:K_m]=2$, $K_{m+1}=K_m(\sqrt a)$ for $a\in K_m$. Then all $c\in K_{m+1}$ are of the form $c=p+q\sqrt a,p,q\in K_{m+1}$. Since $q\sqrt a$ is constructable by (f), $\sqrt a$ is constructable by (h), $p+q\sqrt a$ is constructable by (d), (e), $c\in K_{m+1}$ is constructable.

**Lemma:** Let $\mathbb K\subseteq R$ be a subfield.

(1) If $a,b,c,d\in\mathbb K^2\subseteq\mathbb R^2$, then the intersection of two lines $e$ satisfies $e\in\mathbb K^2$;

(2) If $a,b,c\in\mathbb K^2,r\in\mathbb K$. Then the intersections of a circle and a line (if any) $e,e'\in\mathbb K(\sqrt u)^2$ for some $u\in\mathbb K$;

(3) If $c,c'\in\mathbb K^2,r,r'\in\mathbb K$, then the intersection of 2 cycles $e,e'\in\mathbb K(\sqrt u)^2$ for $u\in\mathbb K$.

**Theorem:** The converse of proposition holds, i.e. if $c\in\mathbb R$ is constructable, then:

$$\exists\mathbb Q=K_0\subseteq K_1\subseteq\cdots\subseteq K_r=\mathbb K$$

s.t. $[K_{i+1}:K_i]=1$ or $2$ and $c\in\mathbb K$.

**Proof:** If $c\in\mathbb R$ is constructable, then it must be obtained by (1)-(3) in lemma above finitely many times.

Each time when we apply (1)-(3), the new point obtained from the old one is in $\mathbb K$ or $\mathbb K(\sqrt u)$. So starting from $K_0=\mathbb Q$, 

$$K_{i+1}=\begin{cases}K_i,\text{if the new point in in }K_i\\K_i(\sqrt u),otherwise\end{cases}$$

and hence $c\in K_r=\mathbb K$.

**Corollary:** we **cannot** trisect an angle of $60^\circ$.

**Proof:** To triset $60^\circ$, we need the coordinates $(\cos 20^\circ,\sin 20^\circ)\in\mathbb R^2$.

Consider the minimal polynomial of $\cos 20^\circ$. Note that:

$$\frac{1}{2}=\cos 60^\circ=4(\cos 20^\circ)^3-3(\cos 20^\circ)$$

Then $p(x)=x^3-\frac{3}{4}x-\frac{1}{8}\in\mathbb Q[x]$ has root $\cos 20^\circ$ and is irreducible in $\mathbb Q[x]$.

Then $[\mathbb Q(\cos 20^\circ):\mathbb Q]=3$.

Suppose on contrary $\cos 20^\circ$ is constructable then we have:

$$\mathbb Q\subseteq K_1\subseteq\cdots\subseteq K_r$$

Then $\mathbb Q\subseteq\mathbb Q(\cos 20^\circ)\subseteq K_r$. By Tower Law, 

$$[K_r:\mathbb Q]=[K_r:\mathbb Q(\cos 20^\circ)][\mathbb Q(\cos 20^\circ):\mathbb Q]$$

However, $3$ is not a factor of $2^s$, which is a contradiction.

**Corollary 2:** It is impossible to double a cube.

**Proof:** To double a cube, we need $\sqrt[3]{2}$. However $[\mathbb Q(\sqrt[3]{2}):\mathbb Q]=3$.