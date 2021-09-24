---
title: "Homotopy groups"
date: 2020-05-16
draft: false
tags: ["Fibrations", "Homotopy groups", "Hopf fibration", "The Puppe sequence"]
categories: ["Algebraic topology", "Homotopy theory"]
series: ["The fibration series"]
katex: true
cover:
    image: "images/SuspensionS1.png"
---

This is part 3 of a series leading up to and exploring model categories. For the other parts see [the series overview]({{< ref "/series/the-fibration-series" >}}).

For an introduction to the material, the definitions, motivation and some examples, please read [part 1]({{<ref "posts/2020/fibrations">}}) and [part 2]({{<ref "posts/2020/fiber-bundles">}}) about fibrations and fiber bundles. This and the the following parts of this series will be about their usefulness, especially in computing homology and homotopy groups. This will be done through two different techniques, namely the long exact sequence of homotopy groups, and the spectral sequence associated to a fibration. In this this part, we look at the long exact sequence. This is a tool that will let us relate the homotopy groups of different kinds of spaces to each other, and ultimately, will help us compute the homotopy groups of fiberbundles from the homotopy groups of the base space, and the homotopy groups of the fibers. Forward, we always have pointed spaces, and the base spaces of our fibrations are simply connected. To be a bit more self contained, we remind ourselves what a long exact sequence is.

**Definition (l.e.s):** A long sequence of objects (in our case usually groups or pointed spaces) 

$$\cdots \longrightarrow A_{n+1} \overset{d_{n+1}} \longrightarrow A_n \overset{d_n} \longrightarrow A_{n-1} \longrightarrow \cdots $$

is called exact at $A_n$ if $\text{Ker}(d_n)=\text{Im}(d_{n+1})$ . The sequence is called exact if it is exact for every $n.$

## The Puppe sequence

There are several ways to develop the long exact sequence of homotopy groups, but we will do it through the Puppe sequence, and for that we first need to look at the loop space $\Omega X$ of a topological space $X$. This is, as the name says, the topological space consisting of all loops in $X$ , i.e. the space of all pointed maps from the pointed sircle $(S^1, \infty)$ to $X$ . We also need the notion of the homotopy fiber of a map $f: X\rightarrow Y$ . Intuitively, this is the fiber of $f$ , except we are allowed to move thing around by a homotopy. To be more precise, the homotopy fiber of a point $y\in Y$ consists of pairs $(x,\omega)$ such that $\omega$ is a path from $f(x)$ to $y$ in $Y$ . We call the collection of the fibers of all the points for the homotopy fiber of $f$, denoted $hofib(f)$.

Now, let $f:X\longrightarrow Y$ be a map of topological spaces. We can turn this into an exact sequence by including the homotopy fiber into the picture, namely $hofib(f)\rightarrow X\rightarrow Y$ . The loop space of $Y$ injects nicely into the homotopy fiber, because it consists of the paths that both start and end at the same points. We can even include $\Omega X$ , and get a sequence

$$\Omega X \rightarrow \Omega Y \rightarrow hofib(f)\rightarrow X\rightarrow Y.$$ 

Iterating this process further by doing the same construction on the map $\Omega X \rightarrow \Omega Y$ , we get a long sequence consisting of iterated loop spaces $\Omega^n X, \Omega^n Y$ and homotopy fibers. This long sequence is called the Puppe sequence, and as you may have guessed, it is going to give us the exact sequence of homotopy groups that we are after.

## The long exact sequence in homotopy

If we assume that the map in the Puppe sequence is a fibration, say $p: E\rightarrow B$ , then we get a sequence

$$\cdots \rightarrow \Omega^n X \rightarrow \Omega^n Y \rightarrow \Omega^{n-1} hofib(p) \rightarrow \cdots .$$

Taking homotopy classes of pointed maps from the zero sphere $S^0$ , we get a long exact sequence

$$\cdots \rightarrow [S^0, \Omega^n X] \rightarrow [S^0, \Omega^n Y] \rightarrow [S^0, \Omega^{n-1} hofib(p)] \rightarrow \cdots$$

On homotopy classes of pointed maps, the loop space functor $\Omega (-)$ is adjoint to the suspension functor $\Sigma (-)$. This is part of Eckmann-Hilton duality and takes some time to explain, so I will not do that here. Hence we get the sequence

$$\cdots \rightarrow [\Sigma^n S^0, X] \rightarrow [\Sigma^n S^0, Y] \rightarrow [\Sigma^{n-1} S^0, hofib(p)] \rightarrow \cdots .$$

The suspension of a space is defined to be the cartesian product with the unit interval modulo the relation that all points are equivalent at the endpoint at the interval. This is maybe more clear with a drawing of the suspension of $S^0$ , where we can see that it is in fact equal to $S^1$ .

![Error loading image](images/SuspensionS0.png)

Because it is fun to draw, I also include a drawing of the suspension of $S^1$ , to see that it is equal to $S^2$ .

![Error loading image](images/SuspensionS1.png)

This phenomenon continues, and we see that an $n$ -sphere is just the suspension of an $(n-1)$ -sphere. Hence, we have that the iterated suspension $\Sigma^n S^0 \simeq S^n$ and we get the sequence

$$\cdots \rightarrow [S^n, X] \rightarrow [S^n, Y] \rightarrow [S^{n-1}, hofib(p)] \rightarrow \cdots .$$

Since our map is a fibration, the homotopy fiber $hofib(p)$ has the same homotopy type as the usual fiber, and we can replace $[S^n, hofib(p)]$ by just $[S^n, F]$ . By this, we are done, since these spaces are the definitions of the higher homotopy groups, i.e. $\pi_n(X)\cong [S^n, X]$, thus we finally have our long exact sequence of homotopy groups

$$\cdots \rightarrow \pi_n(X) \rightarrow \pi_n(Y) \rightarrow \pi_{n-1}(F) \rightarrow \cdots .$$

## Computing some homotopy groups

Our goal for introducing this long exact sequence was to be able to compute homotopy groups of spaces, so that is what we will do. We start by computing both of the examples of fiber bundles we discussed yesterday, namely the cylinder and the Möbius band. For the cylinder we have the fiber bundle $I \rightarrow S^1\times I \rightarrow S^1$ , which gives us the exact sequence

$$0 \rightarrow \pi_1 I \rightarrow \pi_1 S^1\times I \rightarrow \pi_1 S^1 \rightarrow 0$$

Since $I$ is path connected, and $\pi_2 S^1 =0$ since the circle has the real line as it’s universal cover and any map would then extend to the universal cover since the sphere is simply connected. Since $I$ is contractible, we get that $\pi_1 I =0$ as well, which gives us that the fundamental group of the cylinder $\pi_1 S^1\times I$ is $\mathbb{Z}$ . Since the cylinder is homotopy equivalent to the circle, this is maybe no surprise. For the Möbius band, we get the exact same sequence, and then the exact same fundamental group, no surprises.

Historically, the most sought after examples were the homotopy groups of the higher dimensional spheres, since (as an understatement) both homotopy and homology are devices for counting mathematical holes. The spheres have almost all trivial homology groups, and is they would have almost all trivial homotopy groups, then these invariants would be a lot more similar. But, as shown by Hopf, this was not the case. He did so by introducing the now-called Hopf fibration, $S^1 \rightarrow S^3 \rightarrow S^2$ . This can be seen geometrically since the 3-sphere is a double cover of the space $SO(3)$ which acts on the 2-sphere by rotation. This fibration produces the exact sequence

$$\pi_3 S^1 \rightarrow \pi_3 S^3 \rightarrow \pi_3 S^2 \rightarrow \pi_2 S^1$$

where $\pi_2 S^1$ is trivial as mentioned above, and for the same reason, $\pi_3 S^1 =0$ . Hence we have an exact sequence $0 \rightarrow \pi_3 S^3 \rightarrow \pi_3 S^2 \rightarrow 0$ , which means that $\pi_3 S^3 \cong \pi_3 S^2$ , and since every group $\pi_n S^n \cong \mathbb{Z}$ , we have the first non-trivial example for homotopy groups of spheres, namely $\pi_3 S^2 \cong \mathbb{Z}$ .

Next time we introduce the Serre spectral sequence, and use it to compute cohomology groups of some interesting spaces. If we get far enough, we compute another non-trivial example of homotopy groups of spheres, namely $\pi_4 S^3$ . As a gift for bothering to read, I link an amazing artwork by my favorite Russian mathematical artist Anatoly Fomenko, called [“Homotopy groups of spheres”](http://chronologia.org/en/math_impressions/poster034.html).