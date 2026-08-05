---
layout: post
author: Iyad El Khoury
comments: true
---

Let $$(V, \lVert \cdot \rVert)$$ be a normed real vector space and $$v_1, v_2, \dots, v_n \in V$$ a family of $$n$$ unit vectors in $$V$$. A famous problem in geometry is to ask how small can the vector $$\varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$ be made, where $$\varepsilon_i \in \{-1,1\}$$ is a choice of sign for each vector $$v_i$$? Our task is thus to find some upperbound, $$f(n)$$, such that for an arbitrary family of $$n$$ unit vectors, there exists some choice of signs, $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, satisfying $$\lVert\varepsilon_1 v_1 + \dots + \varepsilon_n v_n\rVert \leq f(n)$$. I will call any theorem of this kind a *small sum* theorem.

As the space of signs, $$\{-1,1\}^n$$, is exponential in $$n$$ and the vectors $$\{v_i\}_i$$ are arbitrary, it seems quite reasonable that the correct approach to this problem would be to borrow the probabilistic method in combinatorics. Let us begin with the case where $$V = \mathbb{R}^d$$ and $$\lVert \cdot \rVert$$ is a Euclidean norm.

### The Euclidean case
Let $$(\mathbb{R}^d,\langle \cdot | \cdot \rangle)$$ be a Euclidean space, denote by $$\lVert \cdot \rVert $$ the norm induced by the scalar product $$\langle \cdot | \cdot \rangle$$ and  $$v_1, v_2, \dots, v_n \in \mathbb{R}^d$$ be unit vectors. We will consider a random choice of signs $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, or more precisely, let $$\varepsilon_i \sim \text{Unif}(-1,1)$$ be i.i.d Rademacher random varaibles. We are therefore interested in understanding the Euclidean norm of the random variable $$Z = \varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$. To exploit the bilinearity of the Euclidean scalar product, it will be simpler to consider the norm squared of $$Z$$, that is to say the quantity $$\langle Z | Z\rangle$$. Calculating the expected value of $$\lVert Z \rVert^2$$ is direct:

$$
\mathbb{E}\big[\langle Z \mid Z \rangle\big] = \sum_{i=1}^n \sum_{j=1}^n \mathbb{E}[\varepsilon_i \varepsilon_j] \langle v_i \mid v_j \rangle = \sum_{i=1}^n \lVert v_i \rVert ^2= n
$$

By the first moment method, we thus now there exists a choice of sign $$\{\bar \varepsilon _i\}_i \in \{-1,1\}^n$$ such that $$\lVert Z \rVert^2 \leq n$$. This immedieatly gives us a first result:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
For any Euclidean norm, $$\lVert \cdot \rVert$$ on $$\mathbb{R}^d$$ and unit vecotrs $$v_1,\dots,v_n\in \mathbb{R}^d$$, there exists $$\{\varepsilon_i\}_i \in \{-1,1\}^n$$ such that:

$$ 
\left\lVert \varepsilon_1 v_1 + \dots + \varepsilon_n v_n \right\rVert \leq \sqrt{n} 
$$

</div>

We may also notice that this result is tight, for example, by considering the standard Euclidean norm and the canonical unit vectors $$e_1,\dots,e_n \in \mathbb{R}^d$$, the vector $$Z = \sum _i \varepsilon _i e_i $$ is a vertex of the hypercube $$\Sigma := [-1,1]^n$$ for any choice of $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$. Therefore, in this case there is no choice of signs which obtains a norm of $$Z$$ smaller than $$\sqrt{n}$$.

### The infinity norm case
Let us denote by $$\lVert \cdot \rVert _\infty$$ the infinity norm of $$\mathbb{R}^d$$ defined by $$\lVert (x_1, \dots, x_d) \rVert _\infty = \max _i \mid x_i\mid$$. We recall that this is not a Euclidean norm, for example, Pythagorase's theorem does not hold for $$\lVert \cdot \rVert _\infty$$. To establish a *small sum* theorem for the infinity norm, it suffices to find $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$ such that a single coordinate of $$Z$$ is small. Once again, our strategy is to use a probabilistic argument, and in this case, to find a function $$f$$ such that $$\mathbb{P}[\lVert Z \rVert _\infty \leq f(n)] < 1$$.

