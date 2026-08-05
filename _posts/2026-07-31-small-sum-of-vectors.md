---
layout: post
author: Iyad El Khoury
comments: true
---

Let $$(V, \lVert \cdot \rVert)$$ be a normed real vector space and $$v_1, v_2, \dots, v_n \in V$$ a family of $$n$$ unit vectors in $$V$$. A famous problem in geometry is to ask how small can the vector $$\varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$ be made, where $$\varepsilon_i \in \{-1,1\}$$ is a choice of sign for each vector $$v_i$$? Our task is thus to find some upperbound, $$f(n)$$, such that for an arbitrary family of $$n$$ unit vectors, there exists some choice of signs, $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, satisfying $$\lVert\varepsilon_1 v_1 + \dots + \varepsilon_n v_n\rVert \leq f(n)$$.

As the space of signs, $$\{-1,1\}^n$$, is exponential in $$n$$ and the vectors $$\{v_i\}_i$$ are arbitrary, it seems quite reasonable that the correct approach to this problem would be to borrow the probabilistic method in combinatorics. Let us begin with the case where $$V = \mathbb{R}^d$$ and $$\lVert \cdot \rVert$$ is a Euclidean norm.

### The Euclidean case
Let $$(\mathbb{R}^d,\langle \cdot | \cdot \rangle)$$ be a Euclidean space, denote by $$\lVert \cdot \rVert $$ the norm induced by the scalar product $$\langle \cdot | \cdot \rangle$$ and  $$v_1, v_2, \dots, v_n \in \mathbb{R}^d$$ be unit vectors. We will consider a random choice of signs $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, or more precisely, let $$\varepsilon_i \sim \text{Unif}(-1,1)$$ be i.i.d Rademacher random varaibles. We are therefore interested in understanding the Euclidean norm of the random variable $$Z = \varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$. To exploit the bilinearity of the Euclidean scalar product, it will be simpler to consider the norm squared of $$Z$$, that is to say the quantity $$\langle Z | Z\rangle$$. Calculating the expected value of $$\lVert Z \rVert^2$$ is direct:

$$
\mathbb{E}\big[\langle Z \mid Z \rangle\big] = \sum_{i=1}^n \sum_{j=1}^n \mathbb{E}[\varepsilon_i \varepsilon_j] \langle v_i \mid v_j \rangle = \sum_{i=1}^n \lVert v_i \rVert ^2= n
$$

By the first moment method, we thus now there exists a choice of sign $$\{\bar \varepsilon _i\}_i \in \{-1,1\}^n$$ such that $$\lVert Z \rVert^2 \leq n$$. This immedieatly gives us a first result:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
There exists a choice of signs $$\{\bar\varepsilon_i\}_i \in \{-1,1\}^n$$ such that
$$
\left\lVert \bar\varepsilon_1 v_1 + \dots + \bar\varepsilon_n v_n \right\rVert \leq \sqrt{n}.
$$
</div>

