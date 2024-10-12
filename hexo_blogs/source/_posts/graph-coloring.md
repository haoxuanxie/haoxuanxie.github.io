---
title: Graph coloring with densest subgraph
date: 2024-10-13 00:01:06
tags:
mathjax: true
---

## Problem definition

An undirected graph $G$ is $k$-coloring if all vertices could be colored with at most $k$ different colors, such that all adjacent vertices have different colors. For example, a $k$-clique is $k$-coloring, and a tree is 2-coloring. The densest subgraph of a graph $G$, is an induced subgraph of a vertex subset $S$ of $G$ with $n_S$ vertices and $m_S$ edges, such that its density (i.e., $\rho_{max}=\frac{2m_S}{n_S}$) is highest among all induced subgraphs. In this article, we aim to prove that for a graph $G$ whose densest subgraph has a density $\rho_{max}$, it is $\lceil\rho_{max}+1\rceil$-coloring.

## Proof

Let $G=(V,E)$ and $n=|V|,m=|E|$. We prove it by induction. When $n=1$, $\rho_{max}=0$ and the graph is 1-coloring.

Assume we have proved the case for $n=i$. For any graph $G$ such that $n=i+1$, we denote $S$ as the vertex set of its densest subgraph and assume its density is $\rho_{max}$. Then we remove the smallest degree vertex $u$ of $G$ and derives a graph with $i$ vertices, which is proved to be $\lceil\rho_{max}'+1\rceil$-coloring and $\rho_{max}'$ is the largest density of the new graph. Obviously, the degree of $u$ is no larger than $\rho_{max}$. Otherwise, the total degree of all vertices in $G$ is larger than $\rho_{max}n$, which yields a density larger than $\rho_{max}$. Therefore, $u$ can be colored with at most $\lceil\rho_{max}+1\rceil$ colors (if only considering its neighbours).

We claim that $\rho_{max}'\leq\rho_{max}$. Then $G$ is $\lceil\rho_{max}+1\rceil$-coloring (note that if a graph is $a$-coloring and $a\leq b$, then it is also $b$-coloring).

We prove it by contradiction. If $\rho_{max}'>\rho_{max}$, removing $u$ results in some induced subgraph with a larger density. However, by definition, the densest subgraph of $G$ is already the induced subgraph with the highest density. Therefore, it is impossible to find a denser subgraph by removing a vertex in $G$.

By induction, the proof is done.

## Finding a coloring scheme

We recursively remove the smallest degree vertex in $G$. Specifically, we maintain a min-heap storing the degrees of all vertices. Initially, we insert all vertices into the heap. For each round, we extract the minimum degree vertex from the heap and remove the vertex. During the remove process, we need to update the degree of its neighbors (for a simple graph, the new degree of its neighbors $d_{new}$ should be $d_{old}-1$) and adjust the heap. With a binary heap, since extracting each vertex and updating the degree of each vertex is $O(\log n)$, and there are $m$ updates in total, the time complexity would be $O(m\log n)$. With a Fibonacci heap, where ``decrease-key`` function could be done in $O(1)$, the time complexity would reduce to $O(m+n\log n)$.

We record the sequence $a_1,a_2,\cdots,a_n$ of removing vertices, i.e., the algorithm removes $a_1,a_2,\cdots,a_n$ sequentially. To construct the coloring scheme, we reversely consider each vertex: let $G'$ be an empty graph. We firstly add $a_n$ to $G'$ and color it with $1$. Then we add $a_{n-1}$ to $G'$ and its corresponding edges in $G$ connecting $a_n$ (if exist). If $a_n,a_{n-1}$ are connected, we color $a_{n-1}$ with $2$. Otherwise, it is colored with $1$. Similarly, we add $a_{n-2}$ to $G'$ and its edges to $a_{n-1},a_n$ if exist, and color $a_{n-2}$ with the minimum possible color. Repeat this process until $a_0$ is inserted into $G$ and colored. The time complexity of this process is bounded by $O(m)$.

Therefore, the total time complexity of the algorithm is bounded by $O(m+n\log n)$, and it is straightforward to prove its correctness using the similar technique in the induction proof.