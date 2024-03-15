---
title: "Johnson-Wilson theory"
date: 2022-04-29
draft: false
katex: true
categories: ["Stable homotopy theory"]
tags: ["Formal group laws", "cohomology", "Spectra"]
series: ["The road to Morava K-theory"]
cover:
    image: "images/"
---

It has been some time since we studied at the correlation between [formal group laws]({{<ref "posts/2021/formal-group-laws">}}), which were certain power series that looked like Taylor expansion of multiplication on a Lie group, and complex oriented cohomology theories. In particular, we learned that these two completely separate notions had a common universal object. The universal formal group law over the Lazard ring was the same as the formal group law determined by the universal complex oriented cohomology theory — complex cobordism cohomology. Ever since that time we have not encountered formal group laws in any interesting manner, but, today is the day where we do so. The continuation of studying formal group laws — and later, formal groups — will be very important in understanding the field of chromatic homotopy theory, as they are highly linked. In some sense, the algebraic geometry of formal groups corresponds to the stable homotopy theory of complex oriented cohomology theories. One very important feature of this correspondence is the concept of height. The algebraic geometry of formal groups can be filtered by a variable called height, and this — through the correspondence — gives a filtration on spectra. In this blog post we will define this concept of height, and produce some new spectra in light of this new technology. 

## Height

Recall that a formal group law over a ring $R$ is a power series $F\in R\llbracket  x, y\rrbracket$ such that

1. $F(x, y) = F(y,x)$
2. $F(x,0)=x$
3. $F(F(x,y),z)=F(x,F(y,z))$

We also have natural notions of morphisms between formal group laws, meaning that they form a category. In [the blog-post]({{<ref "posts/2021/formal-group-laws">}}) about formal group laws we mentioned that there is a logarithm construction, and that this construction gives an isomorphism between the two most basic examples of formal group laws — the additive and the multiplicative — in the case where the ring $R=\mathbb{Q}$, the rationals. An even more general fact is true: every formal group law over a $\mathbb{Q}$ are isomorphic. We can even replace the rationals with any field of characteristic zero. The natural followup question is then, what happens in positive characteristic? To make things nice for our story we use separably closed fields of characteristic $p>0$. In this situation it turns out that we have infinitely many non-isomorphic formal group laws. So, can we in some nice way classify them? The answer is yes, and it arises from trying to understand the “iterative behaviour” of the formal group laws. 

We know from the definition that for any formal group law $F$ we have $F(0,x)=x$. Denote this by $F^{(1)}(x)$. Can we say something about $F(x,x)?$ Because $F(x,0)=F(0,x)=x$ we know that $F$ has no constant terms, and that the linear term of $F$ is $x+y$. This means that $F(x,x)$ has linear term $2x$. So, if our field has characteristic $2$, then this linear term vanishes. Note that we can describe $F(x,x)$  in our new above notation as $F(F^{(1)}(x),x)$. We define this to be $F^{(2)}(x)$. If we continue the same idea, we get $F^{(3)}(x)=F(F^{(2)}(x),x)$. This has to have a linear part being $3x$, and we start to see the hints of a pattern. We can iteratively define

$$
F^{(n)}(x) = F(F^{(n-1)}(x), x)
$$

with $F^{(0)}(x) = 0$. The $n$’th part, i.e. $F^{(n)}(x)$, is a power series in one variable, called the $n$-series of $F$. Notice that the linear part of $F^{(n)}(x)$  is $nx$, since we are each time just summing together one more copy of $x$. So, if our field has characteristic $p$, then the part of $F^{(p)}(x)$ with the lowest degree has degree greater than one. In fact, it will have a degree being some power of $p$. The exponent of this power is the integer we call the height of the formal group law.  

Let’s properly type out part of an example before we write down the formal definition. Let $k=\mathbb{F}_p$ and $F=\mathbb{G}_m$, i.e. the multiplicative formal group law defined by $\mathbb{G}_m(x,y)=x+y+xy$. We have 

- $\mathbb{G}_m^{(1)}(x) = x$
- $\mathbb{G}_m^{(2)}(x) = \mathbb{G}_m(x,x)=2x+x^2$
- $\mathbb{G}_m^{(3)}(x)= \mathbb{G}_m(2x+x^2, x) = 3x+3x^2+x^3$
- $\mathbb{G}_m^{(4)}(x) = \mathbb{G}_m(3x+3x^2+x^3, x) = 4x+6x^2+4x^3 + x^4$
- $\mathbb{G}_m^{(5)}(x) = \mathbb{G}_m(4x+6x^2+4x^3+x^4, x) = 5x+10x^2+10x^3+5x^4+x^5$

If $p=2$ we see that the first non-zero entry is $x^2$. If $p=3$, it is $x^3$. If $p=5$ it is $x^5$. In each of these cases we see that the first non-zero entry is of the form $x^p$, meaning that the power of the exponent is $1$. 

The above behaviour happens for all formal group laws over a field with positive characteristic. It will not in general have $1$ as its exponent, and neither have $1$ as its coefficient. In general the first non-zero term will look like $v_n x^{p^n}$ for some $n$. Again, this integer $i$ what we mean by the height. In making the above discussion into a formal definition we need to be a bit careful, as the coefficient $v_n$ is not always invertible. But, this is easily handled by splitting the definition into two cases. 

<span style="color:orange"> **Definition:** </span> Let $k$ be a field with $char(k)=p>0$ and $F$ a formal group law over $k$. We say $F$ has height *at least* $n$ if the first non-zero term in the $p$-series $F^{(p)}(x)$ is $v_nx^{p^n}$. If in addition $v_n$ is invertible, we say $F$ has height *exactly $n$.* 

By example we have verified that the multiplicative formal group law has height exactly $1$. If we consider the additive formal group law $\mathbb{G}_a(x,y)=x+y$, we easily see that this can’t have any finite height, as we get $\mathbb{G}_a^{(p)}(x) = px = 0$. We say that $\mathbb{G}_a$ has infinite height.  

One can show that the height of a formal group law is an isomorphism invariant, hence over a field with positive characteristic we have $\mathbb{G}_m \ncong \mathbb{G}_a$, as was the case over field with characteristic zero. If we restrict our attention to algebraically closed fields with positive characteristic, then the converse is also true. That is, if two formal group laws have the same height, then they are isomorphic.  

We now know that there are formal group laws with height $1$ and $\infty$, but what about all the numbers in between? Are there formal group laws of any height? 

## Higher heights

Unfortunately, things get quite complicated when we try to study formal group laws with height greater than one — at least if we want some explicit description of the formal group law. What we will do instead is to show that they must exist. Let $F$ be a formal group law over a field of characteristic $p$. Recall from above that $v_n$  is the coefficient of $x^{p^n}$ in the $p$-series of $F$. Another view of the height variable is to look only at these $v_n$’s. We could equally well define the height to be the smallest integer $n$ such that $v_n$ is non-zero. This line of thinking will allow us to construct formal group laws of any positive height. 

For this construction we need to consider the universal case, i.e. we need to use the Lazard ring— the ring that carries the universal formal group law —  as our base. By [Quillen’s theorem]({{<ref "posts/2021/formal-group-laws">}}) we know that the Lazard ring is isomorphic to the complex cobordism ring, and  in particular 

$$
L \cong MU_* \cong \Z[t_1, t_2, \ldots],
$$

where $t_i$ has degree $2i$. Let $I$ denote the ideal in $L$ consisting of elements in positive degrees. The trick is to consider the $v_n$’s as elements in $L$, where they now lie in degree $2(p^n-1)$. We have a canonical isomorphism $(I/I^2)_ {2n} \cong \Z t_n$, which means that each $v_n$ has an image in $\Z t_{p^n-1}$ through this isomorphism. This image is $p^{p^n-1}-1$. 

Since $L$ is universal for formal group laws, we know that a map

$$
L\longrightarrow \Z \oplus (I/I^2)_ {2(p^n-1)}\cong \Z\oplus \Z t_{p^n-1}
$$

determines a formal group law. This formal group law is given by

$$
F(x,y)=x+y + \sum_{0<i<p^n}\frac{1}{p}\binom{p^n}{i} t_{p^n-1}x^i y^{p^n-i}
$$

or equivalently, by using the binomial theorem

$$
F(x,y)=x+y+\frac{t_{p^n-1}}{p}((x+y)^{p^n}-x^{p^n}-y{p^n}).
$$

By induction on $m$, the $m$-series of $F$ is given by 

$$
F^{(m)}(x) = mx+\frac{t_{p^n-1}}{p}((mx)^{p^n}-mx^{p^n})
$$

which in particular means that the coefficient of $x^{p^n}$ is given by $(p^{p^n-1}-1)t_{p^n-1}$. If we localize at the prime $p$, we can choose a new isomorphism $L_{(p)}\cong \Z_{(p)}[t_1, t_2, \ldots]$ where now each $t_{p^n-1}$ is given by $v_n$. By using this we can finally construct — purely formally — formal group laws of any height, by deciding where the generators of the Lazard ring gets mapped. 

Let $R$ be a field with characteristic $p$. A formal group law over $R$ is determined by a map $L\longrightarrow R$. We now choose the particular map that sends $t_i \mapsto 0$ for $i< p^n-1$, and $t_{p^n-1}\mapsto 1$. By construction this formal group law has height $n$. 

This is not a nice and explicit construction, as in the case of height $1$ and height $\infty,$ but it at least shows that the intermediary height actually occur among the collection of all formal group laws. There are some ways — in theory — to find formulas for intermediary height formal group laws, at least in the height $2$ case. Let’s quickly describe this without any actual formulas. 

Let $E$ be an elliptic curve over a field of characteristic $p$. We can infinitesimally thicken a neighbourhood of the identity, often called taking a formal neighbourhood. This has the structure of a formal group, that — once we choose some coordinates, whatever that means — gives us a formal group law for the operation. This formal group law depends on the structure of $E$. There are two options for the height of this associated formal group law; it is either $1$ or $2$. It is $2$ precisely when the elliptic curve is *supersingular*. What this means is not very important for us on this blog, but we have included it for the interested. 

## The Johnson-Wilson spectrum

The last thing we will do in this blog-post is to define the so-called Johnson-Wilson spectrum. Initially we wanted to construct this more explicitly using Baas-Sullivan theory, but in order to make it a bit simpler — and only use theory we have already covered — we ended up with the more modern and easy approach. 

Recall that the [Brown-Peterson spectrum]({{<ref "posts/2022/brown-peterson-cohomology">}}) had coefficients given by

$$
BP_* \cong \Z_{(p)}[v_1, v_2, \ldots],
$$

where $|v_i|=2(p^i-1)$. We want to simplify this ring a bit, and then construct a spectrum that has this new simplified ring as its coefficients.  The simplified ring is the ring

$$
\Z_{(p)}[v_1, \ldots, v_{n-1}, v_n^{\pm 1}]
$$

where we have quotiented out all but a finite set of generators, and inverted the final one. We mentioned in the post about Brown-Peterson cohomology that we have a procedure for turning a formal group law into a complex oriented cohomology theory — at least if the ring is flat. The simplified ring we just defined is luckily flat, hence the tensor product  

$$
(-)\otimes_L \Z_{(p)}[v_1, \ldots, v_{n-1}, v_n^{\pm 1}]
$$

is exact. In particular this means that the functor $CW\longrightarrow Ab_*$ defined by sending a CW-complex $X$ to the graded abelian group $MU_\ast (X)\otimes_L \Z_{(p)}[v_1, \ldots, v_{n-1}, v_n^{\pm 1}]$ is a cohomology theory! This cohomology theory is called height $n$ Johnson-Wilson theory, and by [Brown representability]({{<ref "posts/2021/a-first-look-at-spectra">}}) we know that this functor is represented by a spectrum — the height $n$ Johnson-Wilson spectrum $E(n).$ This cohomology theory in fact determines a formal group law that has height $n$. 

The importance of $E(n)$, and other similar spectra we will construct later, like Morava $E$-theory $E_n$ and Morava $K$-theory $K(n)$, will become clear in the near future. We have described the process of [localizing at a homology theory]({{<ref "posts/2021/bousfield-localization">}}). The process of localizing the category of $p$-local spectra at Johnson-Wilson theory $E(n)$ is called height $n$ chromatic localization, and is very important in understanding the structure of $Sp$. Perhaps even more for this understanding is the localization $Sp_{K(n)}$, which in some sense completely describes the [tensor-triangular]({{<ref "posts/2021/tensor-triangulated-categories">}}) structure of [the stable homotopy category]({{<ref "posts/2021/the-stable-homotopy-category">}}) $SHC.$  The spectrum $E(n)$ will also show up a lot when we start discussing my research project in more detail, but for now let’s be content on having described it, and the theory regarding heights of formal group laws.


<style>body {text-align: justify}</style>