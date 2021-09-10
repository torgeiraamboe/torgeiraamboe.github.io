---
title: "A first look at spectra"
date: 2021-08-20
draft: false
katex: true
categories: ["Algebraic topology", "Stable homotopy theory"]
tags: ["Spectra", "Cohomology", "Pointed topological spaces"]
cover:
    image: "images/spectrum.svg"
---

Even though this blog is not centered around a specific topic, we have during the last year looked more frequently at certain topics than others, such as (co)homology theory, homotopy theory and category theory. We will continue this trend today as we will try to find a solid reason for a particular object to exist. These objects were briefly mentioned in the earlier post on [tensor triangulated categories]({{<ref "/posts/2021/tensor-triangulated-categories">}}), namely *spectra.* These objects are hugely important to the field of algebraic topology, one reason being that they are intimately linked to cohomology. This intimate connection is the study of todays blog post[^1]. 

This post also serves as my entry into Grant Sanderson's (of [3 Blue 1 Brown](https://www.3blue1brown.com/)) contest/request for more mathematical explainer content on the internet, so be on the lookout for the other participants as well! 

## Cohomology

The language most of modern abstract mathematics use is category theory, which we have seen numerous times on this blog. Categories are important frameworks for studying all objects of a certain type at once, instead of studying them one-by-one. Categories consists of two things: objects and morphisms. The objects we are interested in today is topological spaces[^2], and to start off, the morphisms are continuous functions. These functions are dear to most mathematicians hearts because continuity is a central backbone feature of many areas of mathematics, and the topological spaces are what allows us to define continuity. Hence these are important to understand. 

One hugely successful approach to understanding topological spaces is cohomology theory. We have only seen one such theory on this blog as of yet, called singular cohomology, but this is not the only one. We have seen hints of other theories, through [vector bundles]({{<ref "/posts/2020/swans-theorem">}}) and through [cobordisms]({{<ref "/posts/2021/a-lecture-in-my-second-year">}}), but we have not seen how to make cohomology out of these constructions. We won't see this today either, but we will use the fact that there exists several different ones. For a nice list of different cohomology theories, see this [wikipedia page](https://en.wikipedia.org/wiki/List_of_cohomology_theories). 

So, as we will use these theories, lets define what we actually mean by "a cohomology theory". Some of the readers have perhaps seen such theories defined through the Eilenberg-Steenrod axioms, but here we take a similar, but different and yet equivalent route. This is to use just based topological spaces instead of pairs of topological spaces. The approach is equivalent, as each cohomology theory for pairs determines, and is determined by, a reduced cohomology theory for pointed topological spaces. 

**Definition (Reduced cohomology theory):** A reduced cohomology theory $\widetilde{E}^\ast$ is a contravariant functor from the category of pointed topological spaces, $Top_\ast$, to the category of graded abelian groups, $Ab_\ast$,satisfying the four axioms below. We let $X$ be a topological space and for simpler notation we write $f^\ast = \widetilde{E}^\ast(f)$ where $f:X\longrightarrow Y$ is a continuous map to some topological space $Y$.  

1. If $f\simeq g$ then $f^\ast = g^\ast$, i.e. homotopic maps get sent to equivalent homomorphisms
2. For any subspace $A\subseteq X$ there is a map $\partial^\ast: \widetilde{E}^\ast(X/A)\longrightarrow \widetilde{E}^{\ast+1}(A)$, called the coboundary, which is natural in $A$ and $X$. 
3. For any subspace $A\subseteq X$ there is a long exact sequence 

    $$\cdots\overset{\partial_{n-1}}\longrightarrow \widetilde{E}^n(A)\overset{i_n}\longrightarrow \widetilde{E}^n(X)\overset{q_n}\longrightarrow \widetilde{E}^n(X/A)\overset{\partial_n}\longrightarrow \widetilde{E}^{n+1}(A)\overset{i_{n+1}}\longrightarrow \cdots$$

    where $i:A\longrightarrow X$ is the inclusion map and $q:X\longrightarrow X/A$ is the quotient map. 

4. For a collection of spaces $\{X_\alpha\}_{\alpha\in \Alpha}$ the maps $i_\alpha:X_\alpha\longrightarrow \bigvee_{\alpha\in\Alpha} X_\alpha$ induces isomorphisms 

    $$\prod_{\alpha\in \Alpha} (i_\alpha)^\ast : \widetilde{E}^\ast(\bigvee_{\alpha\in\Alpha} X_\alpha)\longrightarrow \prod_{\alpha\in\Alpha}\widetilde{E}^\ast(X_\alpha).$$

If you don't understand the details of the definition, don't worry, it is not really important for us today. We have included it more for completion sake. The important part is that a reduced cohomology theory is a contravariant functor $\widetilde{E}^\ast : Top_\ast\longrightarrow Ab_\ast$. 

An important feature of reduced cohomology theories is the following result. 

**Theorem 1:** Let $\widetilde{E}^\ast$ be a reduced cohomology theory. Then for any pointed space $X$ we have an isomorphism $\widetilde{E}^\ast(X)\cong \widetilde{E}^{\ast+1}(\Sigma X)$ induced by the coboundry map. 

This is an important result for several reasons. The suspension functor is the central feature of stable homotopy theory, where the spectra — our objects of interest — is one of the main players. The above result states that reduced cohomology is stable, or invariant under suspension. Another reason for its importance will become clear soon, as we will use it as part of a construction regarding spectra. 

## Representability

For us today the most important feature of reduced cohomology theories is that they are representable. We don't yet know what this means precisely, but intuitively it means that the functor behaves very much like regular morphisms in our category. Let's see a bit more rigorously what this means. 

One of the most important functors in the whole of category theory is the hom-functors. There are two kinds of such functors — the covariant and the contravariant. These functors take some object in the category, and sends it to the set of morphisms to, or from, that object. To make this work we need to fix an object $X$, and then define the covariant hom-functor to be $\text{Hom}(X, -)$, i.e. the functor that takes an object $Y$ and sends it to the set $\text{Hom}(X, Y)$ or morphisms from $X$ into $Y$. The contravariant hom-functor is defined similarly as $\text{Hom}(-, X)$. 

As morphisms are one of the fundamental ideas of category theory, having a functor that sends objects to morphisms is very important. This also allow us the following definition. 

**Definition (Representable functor):** A functor $F:\mathcal{C}\longrightarrow Set$ for some category $\mathcal{C}$ is called representable if $F$ is naturally isomorphic to $\text{Hom}(-, X)$ for some object $X$ in $\mathcal{C}$. The object $X$ is called a representing object of $F$. 

As mentioned, the central feature (for us today) of reduced cohomology theories is that they are representable. We have defined our reduced cohomology theories to be functors into the category of graded abelian groups, so for each degree $n$ we have a corresponding "part" of our functor, i.e. $\widetilde{E}^n:Top_* \longrightarrow Ab$. The fact that these functors are representable is due to the following famous theorem. 

**Theorem (Brown representability):** Let $\widetilde{E}^\ast$ be a reduced cohomology theory. Then for each $n$, there is a pointed connected space $K_n$ such that for any pointed connected space $X$ there is a natural isomorphism $\widetilde{E}^n(X)\cong [X, K_n]$, where the set on the right is the set of homotopy classes of maps in the category of pointed topological spaces. The spaces $K_n$ are unique up to homotopy equivalence. 

We don't really need the connectedness criteria for this theorem to hold, but for the spaces $K_n$ to be unique, we do need it. The above result means that every degree of our reduced cohomology functor is representable, meaning that there is some space that represents it. We might wonder why we don't see the hom-functor in the above theorem, but remember that the set $[X, K_n]$ is the set $\text{Hom}(X, K_n)$ in the homotopy category of spaces, so this theorem in fact states that the functor is representable as defined previously. 

## A first look at spectra

When we see the result above we might wonder if we can determine a reduced cohomology theory simply by defining the collection $\\{K_n\\}_ {n\in \mathbb{Z}}$ of representing objects? The answer to this turns out to be no in general. There are no canonical way of defining the coboundary map we need in the reduced cohomology theory just by having the representing spaces. There is however a fix for this, but we need to introduce some requirements and extra structure on these collections of representing objects $\\{K_n\\}_{n\in \mathbb{Z}}$. 

Let $\widetilde{E}^\ast$ be a reduced cohomology theory, and let it be represented by the sequence of pointed connected spaces $\\{K_n\\}_{n\in \mathbb{Z}}$. Recall that this means that for any pointed connected space $X$, we have an isomorphism

$$[X, K_n] \cong \widetilde{E}^n(X)$$

Recall also from **Thorem 1** that we have an isomorphism $\widetilde{E}^n(X)\cong \widetilde{E}^{n+1}(\Sigma X)$. By the $n+1$'st part of $\widetilde{E}^\ast$ also being representable, we know that we have an isomorphism $\widetilde{E}^{n+1}(\Sigma X)\cong [\Sigma X, K_{n+1}]$. A central fact from algebraic topology is the fact that on homotopy classes of pointed continuous functions the suspension functor $\Sigma$ is adjoint to the loop space functor $\Omega$. We encountered this adjunction in [the fibration series]({{<ref "/series/the-fibration-series">}}) when we constructed the Puppe sequence. This fact means that we have a last isomorphism $[\Sigma X, K_{n+1}]\cong [X, \Omega K_{n+1}]$. Putting all these together we get

$$[X, K_n]\cong \widetilde{E}^n(X)\cong \widetilde{E}^{n+1}(\Sigma X)\cong [X, \Omega K_{n+1}],$$

which are all natural in $X$. Hence we see that also $\Omega K_{n+1}$ seems to be a representing object for $\widetilde{E}^n$, hence there should be a homotopy equivalence $K_n\longrightarrow \Omega K_{n+1}$. Due to the fact that loop space functor does not preserve connectedness very well, this is not in general a representing object, so we should not in general expect there to be a homotopy equivalence $K_n\longrightarrow \Omega K_{n+1}$. But, we can get something almost so by letting $X=K_n$ which results in an isomorphism $[K_n, K_n]\cong [K_n, \Omega K_{n+1}]$. The image of the identity map $id:K_n\longrightarrow K_n$ gives for all $n$ a map $$\alpha_n:K_n\longrightarrow \Omega K_{n+1}$$ which we call the structure maps of the collection of spaces $\\{K_n\\}_ {n\in \mathbb{Z}}$. By naturality of the sequence of isomorphisms above, we get that a map $f:X\longrightarrow K_n$ gets sent to the map $f\circ \alpha_n$ by the isomorphism. By now letting $X=S^m$ for, we see that $\alpha_n$ must be a weak homotopy equivalence. This is actually what we need to define a spectrum, more specifically an $\Omega$-spectrum. 

**Definition ($\Omega$-spectrum):** An omega spectrum $K$ is a collection $\\{K_n\\}_ {n\in\mathbb{Z}}$ of pointed connected spaces, together with weak homotopy equivalences $\alpha_n:K_n\longrightarrow \Omega K_{n+1}$.

Such an object can be visualized in the following manner, i.e. as an infinite sequence of spaces, together with structure maps to the loop space of the "shifted space"

![Error loading image](images/spectrum.svg)

So, what happens then to the earlier statement regarding the representation of the reduced cohomology theories? The failure of the spaces themselves to uniquely determine a cohomology theory is remedied by the following theorem.  

**Theorem:** An $\Omega$-spectrum $K$ determines a reduced cohomology theory $\widetilde{E}^\ast$ by defining $\widetilde{E}^n(X) = [X, K_n]$. The coboundary maps are induced by the structure maps $\alpha_n$. 

Moreover, if between two $\Omega$-spectrums $K$ and $L$ representing two reduced cohomology theories $\widetilde{E}^\ast$ and $\widetilde{F}^\ast$ there are pointed weak homotopy equivalences $$f_n:K_n\longrightarrow L_n$$ that respect the structure maps, then the maps $f_n$ induce a natural isomorphism of reduced cohomology theories $\widetilde{E}^\ast\longrightarrow \widetilde{F}^\ast.$

Hence, a reduced cohomology theory $\widetilde{E}^\ast$ determines, and is determined by, a unique (up to weak homotopy equivalence) $\Omega$-spectrum $K$. 

To give an example perhaps some of he readers are familiar with, the standard reduced singular cohomology theory with coefficients in an abelian group $G$ is represented by the so called Eilenberg-Mac Lane spectrum. This consists of the Eilenberg-Mac Lane spaces of the group $G$, often denoted $K(G, n)$ for $n\geq 0$ and of a singleton space for $n<0$. The structure maps come from an universal property of these spaces, which is that $\Omega K(G, n)$ is an $(n-1)$-Eilenberg-Mac Lane space for $G$, hence $$\Omega K(G, n)\simeq K(G, n-1).$$ We did in fact already see this connection when we studied [cofibrations and the coexact Puppe sequence]({{<ref "/posts/2020/cofibrations">}}) in the fibration series! Then we also more explicitly developed the long exact sequence in singular cohomology from a cofibration sequence. 

## Summary

So, what have we done today? We took the important category of topological spaces and tried to understand its objects using reduced cohomology theories. These we discovered were representable, which allowed us to look at maps into certain spaces. This representation was not unique, meaning that given a sequence of spaces it didn't uniquely determine a reduced cohomology theory, but if we added some extra structure, i.e. turned the sequence of spaces into an $\Omega$-spectrum, then we had a one-to-one correspondence between reduced cohomology theories and $\Omega$-spectra! 

Hopefully next time we will look into spectra more generally, and try to construct a category containing them as objects. We will then hopefully see that we need to be a bit careful by how we go about doing this. 

[^1]: This introduction, and most of the theory in his post is inspired heavily by the book "Foundations of stable homotopy theory" by Barnes and Roitzheim. 

[^2]: Note that for simplicity we define topological space to mean CW-complex. This will not affect the theory (I think) as cohomology theories of topological spaces are determined by their restriction to CW-complexes.