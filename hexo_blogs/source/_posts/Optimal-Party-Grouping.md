---
title: Optimal Party Grouping
date: 2026-03-25 17:37:37
tags:
---

## Goal
You have $n$ friends and want to invite $k$ friends for a party. You want to find such a $k$-group such that these friends, when getting together, feel least embarrassed.

I found this problem interesting and practical in my daily life. There are several views for solving the problem:
- Social network view: if you know the social connections between your friends, you can minimize the embarrassment by forming a group such that the friends in the group are most familiar with others, which corresponds to a densest subgraph problem; 
- Embedding view: if you know the embeddings (e.g., interests, identities) of your friends, you can minimize the embarrassment by forming a group with most common features, which can be transformed into a distance minimization problem.

## Solution based on social networks
<iframe
  src="/blogs/assets/group_example.pdf"
  width="100%"
  height="520"
  style="border: 1px solid #ddd; border-radius: 8px;"
>
</iframe>

[Open the PDF directly](/blogs/assets/group_example.pdf)

We can formalize the problem as: given a graph $G=(V,E)$ with a root vertex $u$ such that every other vertex is connected to $u$, find a subset $S\subseteq V$ such that $u\in S$ and $|S|=k+1$ such that the density of the subgraph induced by $S$ is maximized. The density of a subgraph is defined as $\frac{|E(S)|}{|S|}$, where $E(S)$ is the set of edges in the subgraph induced by $S$.

There is a simple greedy solution using $O(n\log n+m-km/n)$ time: each round we locate the vertex with minimum degree and remove it from the graph until only $k+1$ vertices are left. Note that $u$ will not be removed since it has the largest degree. It is straightforward to verify the correctness of the solution.

**UPD: The above greedy solution is wrong. A counterexample can be constructed by conneting $u$ with a $k$-clique and a large-enough complete bipartite graph. Then the clique will be incorrectly pruned.**

We can prove this problem is NP-hard by reducing from size-$k$ densest subgraph problem, which aims to find a densest subgraph with exactly $k$ vertices.

Let $G'$ be the target graph of the size-$k$ densest subgraph problem, which is known to be NP-hard. We construct $G$ by adding a vertex $u$ connecting every vertex in $G'$. Therefore, solving our version of problem, and then removing $u$, gives the result for size-$k$ densest subgraph problem.

## Solution based on embeddings
This is  the way I prefer more. I don't want to invite a group of friends that are already very familiar with each other, or in the same community. For example, using the above approach for my friends will result in a group of all my lab colleagues. However, how to make your friends "least embarrassed" if they are not familiar with each other? Maximizing their common interests can help.

Let's say a friend can be represented by a $d$-dimensional vector. Each dimension is within $\left\{0,1\right\}$ representing an interest. For example, let the first dimension be interests on K-pop. Then $0$ represents the friend is not interested in K-pop, while $1$ represents the friend is interested in K-pop. Then we can formalize the problem as: 

- Given a set of vectors $\left\{v_1,v_2,\cdots,v_n\right\}$, find a subset $S\subseteq V$ such that $|S|=k$ such that the sum of square distances between the vectors in $S$ is minimized. More formally:

$$
\begin{align}\min_{z_i\in\left\{0,1\right\}}\sum_{i<j}y_{ij}||v_i-v_j||^2\\
s.t.\quad y_{ij}\geq z_i+z_j-1\\
\sum_{i=1}^n z_i=k\\
y_{ij}\geq 0\\
z_i\in\left\{0,1\right\}
\end{align}$$

Here $z_i=0$ means not inviting the $i$-th friend, while $z_i=1$ means inviting the $i$-th friend. $y_{ij}$ is an auxiliary variable indicating whether both the $i$-th and $j$-th friends are invited. The above problem can be solved by integer programming solvers such as Gurobi.
