---
title: Maintaining the diameter of a growing tree in $O(\log n)$ time
date: 2024-09-03 18:57:20
tags:
mathjax: true
---

A tree is a connected undirected graph with $n$ nodes and $n-1$ edges. The diameter of a tree is the largest distance between two nodes in the tree.

We define a growing tree as follows: at each moment, a new node $u$ is inserted into the tree, and $u$ is connected to some node $v$ in the original tree. What is the diameter of the new tree?

Let $L$ be the path such that the length of $L$ is the diameter of the original tree. A key observation is that if $w_1,w_2$ are the endpoints of $L$, then for the new tree, the endpoints of the new path for the new diameter must be $(u,w_1),(u,w_2)$ or $(w_1,w_2)$.

The proof is rather simple. The distance between $w_1,w_2$ is actually the length of $L$. By the definition of the tree diameter, it is also the largest distance between two nodes in the original tree. Since the distances between two nodes do not change in the original and new tree, the only candidate nodes to be the new endpoints could only be $u,w_1,w_2$ (for other nodes, since they have the same distances which are not larger than $|L|$, we could just ignore them).

Therefore, to derive the new diamter, we only need to maintain $w_1,w_2$ for each moment, and compute the distances between $(u,w_1),(u,w_2)$ and $(w_1,w_2)$ after each moment, where the largest distance is the new diameter. The distance between $(u,w_1)$ could be computed by $d(u)+d(w_1)-2d(LCA(u,w_1))$, where $d$ is the depth of the node and $LCA$ is the lowest common ancestor of two nodes, and other distances could be computed similarly. The depth of the new node $u$ could be maintained in $O(1)$ time for each moment. Maintaining and computing $LCA$ could be done in $O(\log n)$ time for each moment. As a result, we could maintain the diameter of a growing tree in $O(\log n)$ time.