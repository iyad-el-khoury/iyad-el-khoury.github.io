---
layout: post
author: Iyad El Khoury
comments: true
---

Let $$(V, \lVert \cdot \rVert)$$ be a normed real vector space and $$v_1, v_2, \dots, v_n \in V$$ a family of $$n$$ unit vectors in $$V$$. A famous problem in geometry is to ask how small can the vector $$\varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$ be made, where $$\varepsilon_i \in \{-1,1\}$$ is a choice of sign for each vector $$v_i$$? Our task is thus to find some upperbound, $$f(n)$$, such that for an arbitrary family of $$n$$ unit vectors, there exists some choice of signs, $$\{\varepsilon_i\}_{i} \in \{-1,1\}$$, satisfying $$\lVert\varepsilon_1 v_1 + \dots + \varepsilon_n v_n\rVert \leq f(n)$$.

As the space of signs, $$\{-1,1\}^n$$, is exponential in $$n$$ and the vectors $$\{v_i\}_i$$ are arbitrary, it seems quite reasonable that the correct approach to this problem would be to borrow the probabilistic method in combinatorics. Let us begin with the case where $$V = \mathbb{R}^n$$ and $$\lVert \cdot \rVert$$ is the standard Euclidean norm on $$\mathbb{R}^n$$.