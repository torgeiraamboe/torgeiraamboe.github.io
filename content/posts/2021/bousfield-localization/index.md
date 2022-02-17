---
title: "Bousfield localization"
date: 2021-12-02
draft: false
katex: true
categories: ["Stable homotopy theory", "Algebraic topology"]
tags: ["Localization", "Homology", "Spectra"]
cover:
    image: "images/Localisation.png"
---


Topology, particularly homotopy theory, is hard. The scenes where these kind of mathematics happen are immensely complicated; the category of topological spaces; the category of spectra. The problem is that there is simply too much information to try to capture by using simple tools that we can actually understand properly. Trying to classify topological spaces or spectra is a feat that many deem impossible, it is simply too difficult. 

So, how can we try to fix this? We take inspiration from other fields, where similar situations occur and then try to translate into our own situation. Take for example abelian groups. We have no classification of all abelian groups, but there are certain constructions that help us study them. We have a classification of finitely generated abelian groups, where we can decompose any abelian group $A$ into understandable pieces: a free part $\Z^r$ and a torsion part $\Z/p_1^{k_1}\oplus \ldots \oplus \Z/p_t^{k_t}$. For all abelian groups things get more complicated, but there are nice groups that have classifications, like divisible groups, which are direct sums of copies of $\mathbb{Q}$ and Prüfer groups $\Z(p^\infty)$. The general approach seems to be to split the complicated groups into smaller pieces, or to study them via some easier groups. If we just consider $\Z$ for a moment, we can for a prime $p$ study

- $\Z/p$, the $p$-torsion integers
- $\Z_{(p)}$, the $p$-local integers
- $\Z_p$, the $p$-complete integers, also called the $p$-adic integers.

All these give us various information about $\Z$ somehow centred around or away from the prime $p$. The last two actually come from a common very general framework, called localization. This framework is what will allow us to translate these ideas into topology and spectra. The main thing we want to understand in this post is $p$-localization of spectra, so let's first recall a bit what this means for the integers. 

Given the ring $\Z$ and a prime $p$ we can define the ring $\Z_{(p)}$ by inverting every prime not equal to $p$. This is the same as normal localization $[S^{-1}]\Z$ where $S=\\{\text{Prime ideals }(q)\neq (p)\\}$. The reason it is called localization is due to the corresponding geometric picture. 

Having a module $M$ over a ring $R$ is equivalent to having a quasi-coherent sheaf $\widetilde{M}$ over the [affine scheme]({{<ref "posts/2021/schemes">}}) $Spec(R)$. Letting $R=\Z$ we get that a module is just an abelian group $A$. Hence, any abelian group $A$ gives us a quasi-coherent sheaf $\widetilde{A}$ over $Spec(\Z)$. The spectrum of the integers looks as follows: 

<img src="images/2specZ.png" alt="Error loading image" width="600"/>

Inverting every prime not equal to $p$ in $A$ is the same as restricting the quasi-coherent sheaf $\widetilde{A}$ to the element $(p)$ in $Spec(\Z)$. Intuitively we "zoom in" on the sheaf over just the point $(p)$, i.e. looking at it locally at

<img src="images/plocal.png" alt="Error loading image" width="300"/>

Hence the name localization. 

<!--The image of restricting $Spec(\Z)$ to $p$ is in fact the spectrum of $\Z_{(p)}$, i.e. $Spec(\Z_{(p)})$. This is because it is a local ring, which has only one unique maximal ideal -->

## Definitions

Intuitively, localization is a formal way to invert morphisms in some category. It is a very general process. All we need is a multiplicatively closed set of maps, $W$, in our category $C$, which allows us to produce a category $C[W^{-1}]$ where all maps in $W$ now are invertible. If $C[W^{-1}]$ is a subcategory of $C$ then we say the localization is reflective. In this case localization is "projection" onto this subcategory in such a way that it is a left adjoint to the fully faithful inclusion. Bousfield localization is a generalization of reflective localization where we allow certain uniquenesses to be weakened, in particular we allow contractible choice for categories that have spaces of morphisms. We can think of this as making a process for inverting maps in a category such that we get a reflective localization on the homotopy category. We will not cover all general details of localizations and Bousfield localizations, as this is not necessary for us. We are primarily interested in Bousfield localization of spectra, which makes the situation a bit simpler as the category of spectra is a stable model category. Note that we could also use stable $\infty$-categories here. The theory is roughly the same, but in the former we have to be a bit careful with which objects we are choosing — they must often be cofibrant — while in the latter this information is hidden in the $\infty$-structure that we will not explain in this post. 

Recall that a topological [stable model category]({{<ref "posts/2021/the-stable-homotopy-category">}}) is a pointed topological model category $C$ (a model category [enriched]({{<ref "posts/2020/defining-the-cosmos-1">}}) in topological spaces) with a pair of functors $\Sigma:C\rightleftarrows C:\Omega$ that induces an auto-equivalence on the homotopy category $HoC$. Let $W$ be a collection of morphisms in $C$. 

The following three definitions are the central and most important definitions when defining and working with Bousfield localization. 

<span style="color:orange"> **Definition:** </span> We say an object $Y$ in $C$ is $W$*-local* if for all maps $w:A\longrightarrow B$ in $W$, the induced map 

$$-\circ w: Map_C(B, Y)\longrightarrow Map_C(A, Y)$$

is a weak homotopy equivalence of mapping spaces. 

<span style="color:orange"> **Definition:** </span> We say a morphism $f:A\longrightarrow B$ in $C$ is a $W$-equivalence if the induced map

$$-\circ f: Map_C(B, Y)\longrightarrow Map_C(A, Y)$$

is a weak homotopy equivalence for all $W$-local objects $Y$ in $C$. 

<span style="color:orange"> **Definition:** </span> We say an object $X$ in $C$ is $W$-acyclic if it is $W$-equivalent to a point, i.e. if the unique map $0\longrightarrow X$ induces a weak homotopy equivalence 

$$Map_C(X,Y)\simeq Map(0, Y)\simeq pt$$

for all $W$-local objects $Y$ in $C$. 

So, what do these three things mean? The names should give a rough indication. An object $Y$ is $W$-local if any morphism in $W$ looks like an equivalence from the viewpoint of $Y$. The $W$-equivalences are a broader collection of maps than $W$ that act in the same way as $W$ on $W$-local objects. The $W$-equivalences can be thought of as generated by $W$, and we do in fact have $$W\subseteq \\{W-equivalences\\}.$$ Finally, the $W$-acyclic objects are the objects that are "trivial" in the eyes of $W$-local objects. So if we restrict to $W$-local objects, we should get that any $W$-equivalence is a weak homotopy equivalence, and that any $W$-acyclic object is weakly equivalent to a point. 

We are now ready for our initial definition of Bousfield localization. 

<span style="color:orange"> **Definition:** </span> Let $C$ be a topological stable model category and $W$ a collection of morphisms in $C$. A Bousfield localization of $C$ on $W$, written $L_WC$, is the same underlying category $C$ with a new model structure defined by

- the weak equivalences being the $W$-equivalences,
- the cofibrations being the same
- the fibrations being induced, i.e. they are the maps satisfying the lifting property with respect to acyclic cofibrations.

Equivalently we can use its universal property, that the Bousfield localization of $C$ is a category $L_W C$ such that for any left Quillen functor $F:C\longrightarrow D$ whose left derived functor sends $W$ to weak equivalences in $D$, then the functor factors uniquely through $C\longrightarrow L_WC$. We can summarize with the following diagram:

<img src="images/universal.png" alt="Error loading image" width="300"/>

If we remove the word "stable" in the definition we get general Bousfield localization. We have already seen an example of this construction when constructing [the stable homotopy category]({{<ref "posts/2021/the-stable-homotopy-category">}}). In that case we had a model structure on spectra consisting of level-wise morphisms. We then considered the $\pi_\ast$-isomorphisms as weak equivalences instead, and kept the cofibrations the same. This means that the stable model structure on spectra is nothing more than Bousfield localization at the $\pi_\ast$-isomorphisms of the level-wise model structure. 

Before we move on we quickly remark that Blousfield localizations do not always exist. There are, however, certain existence theorems, putting restrictions on the size of $W$ — like requiring it to be a set —and putting certain niceness conditions on the stable model category $C$. We won't cover these in detail, as the main examples we are interested in — localization at homology theories in spectra — are proven to always exist, but we can look at localization "objectwise" instead.

<span style="color:orange"> **Definition:** </span> Let $X$ be an object in $C$. A morphism $l:X\longrightarrow Y$ is a $W$-localization of $X$ if: 

- the object $Y$ is $W$-local and
- the morphism $l$ is a $W$-equivalence.

If such a map exists, then we say $X$ has a $W$-localization, and if such maps exists for all objects in $C$ then we say $C$ has all $W$-localizations. If $C$ has all $W$-localizations, then the model category $L_WC$ exists. 

Importantly, such a localization are essentially unique, in the sense that any two $W$-localizations, $X\longrightarrow Y$ and $X\longrightarrow Y'$ of $X$, are isomorphic in the [under category]({{<ref "posts/2020/under-category">}}) of $X$ in $HoC$. Hence we can denote "the" $W$-localization as $L_WX$. This also means that $W$-localizations are the fibrant replacements in $L_WC$. 

Before we move on we introduce a constraint on $W$. This in order to make the discussion nicer and more relevant for later. The constraint is due to the following observation: given a stable model category $C$, then its homotopy category is triangulated. Hence, we must ask the important question. Is the localization $L_WC$ of a stable model category $C$ also stable? This is not true in general, hence the restrictions on $W.$ Since we are interested in stability, i.e. invariance under $\Sigma$ and $\Omega$, the restrictions we must have on $W$ are to be stable under these. Let's be a bit more precise.

Given a topological stable model category $C$ we have isomorphisms of homotopy mapping spaces

$$[\Sigma X, Y]\cong[X, \Omega Y]\cong \Omega[X, Y].$$

In particular this means that any collection of morphisms $W$ has the properties that:

- $W$-equivalences are closed under $\Sigma$, because if $Map(X, f)$ is a weak homotopy equivalence, then so is $Map(X, \Sigma f)$;
- $W$-local objects are closed under $\Omega$, because if $Map(X, w)$ is a weak homotopy equivalence, then so is $Map(\Omega(X), w)$.

These two are satisfied by any collection in a topological stable model category, but we are missing a little bit to have full stability. 

<span style="color:orange"> **Definition:** </span> Let $C$ be a topological stable model category and $W$ a collection of morphisms in $C$. We say $W$ is a stable collection if either 

- $W$-local objects are closed under $\Sigma$
- $W$-equivalences are closed under $\Omega$.

We only require one or the other as they turn out to be equivalent. These stable collections are what makes sure that the Bousfield localization of $C$ on $W$ still is a stable model category. This is important for still having triangulated homotopy categories after localization. What makes this nicer for the below discussion is that Bousfield localization of stable model categories on stable collections of maps is only dependent on the homotopy category, not the model category! 

So then, what happens to localization in the homotopy category? In the normal stable model category, the homotopy category can be identified with the subcategory of bifibrant objects and homotopy classes of morphisms. In the new localized model structure, we have more weak equivalences, meaning we get fewer objects (or isomorphism classes of objects rather). These extra objects are precisely the $W$-local ones. This means that the homotopy category $HoL_WC$ is equivalent to the full subcategory of bifibrant $W$-local objects with homotopy classes of morphisms. The inclusion $HoL_WC\longrightarrow HoC$ has a left adjoint $HoC\longrightarrow HoL_WC$ that factors as 

$$HoC\longrightarrow HoC/HoA\longrightarrow HoL_WC$$

where $HoA$ is the homotopy category of the full subcategory of $W$-acyclic objects. The latter functor is an equivalence, which means we also can think about $W$-localization as killing off all the $W$-acyclic objects. Here the quotient is the Verdier quotient, which connects Bousfield localization in the stable world to "regular old" localization of triangulated categories. 

Hopefully the above discussion gives some basic insight into what a Bousfield localization is, at least in the nicer stable situation. The important takeaway is that Bousfield localization is — at least on homotopy categories — the idea of restricting to only local objects, or equivalently, killing certain trivial objects. 

We now turn to an application of the general Bousfield localization described above, namely localization at homology theories in spectra. 

## Localization at homology

We have really only covered how to construct cohomology theories from spectra, but a nice fact is that we also get homology theories from spectra. Given a spectrum $E$ we can form a homology theory $E_\ast(-)=\pi_\ast(E\wedge(-))$. This is called $E$-homology and is a homology theory on the category of spectra, not just on topological spaces. The simplest example is $\mathbb{S}$-homology, which is just [homotopy groups of spectra]({{<ref "posts/2021/the-stable-homotopy-category">}}), or "equivalently" [stable homotopy groups]({{<ref "posts/2021/stable-homotopy">}}) of topological spaces. To construct a Bousfield localization in spectra from a homology theory we need a collection of maps we want to invert. These maps are the so-called $E$-isomorphisms. 

<span style="color:orange"> **Definition:** </span> A morphism of spectra $f:A\longrightarrow B$ is said to be an $E$-isomorphism if it induces an isomorphism in $E$-homology. 

These $E$-isomorphisms form a stable collection of maps in spectra, hence the localization we do will produce a stable model category. In the general case we constructed a bigger collection of $W$-equivalences from a collection $W$, but in the case of $E$-isomorphisms we simply get back the same collection. Thus $E$-isomorphisms are usually called $E$-equivalences instead, to remind more of the general construction. Localization at this collection of maps is called localization at the homology theory $E$. We do remark that the collection of $E$-isomorphisms do not form a set, so by the above briefly mentioned existence result, localizing at these maps cant be said to exist without any argument. But, there are actual sets of maps $I$ such that the $I$-equivalences are the $E$-isomorphisms, which means in particular that Bousfield localization at an homology theory $E$ always exists. 

In spectra we have a nice definition of being $E$-local, due to the fact that $E$-isomorphisms are the $E$-equivalences. 

<span style="color:orange"> **Definition:** </span> A spectrum $X$ is said to be $E$-local if every $E$-equivalence $f:A\longrightarrow B$ induces a homotopy equivalence $Map(f, X):Map(B, X)\longrightarrow Map(A, X)$ on mapping spectra. 

This means we can finally define the localization of an object $X$ at $E$. 

<span style="color:orange"> **Definition:** </span> Let $X$ be a spectrum. An $E$-localization of $X$ is a morphism $f:X\longrightarrow L_E X$ such that $f$ is an $E$-equivalence and $L_E X$ is $E$-local. 

As in the general case we are sort of replacing the spectrum by something that is equivalent in the eyes of $E$, but not necessarily equivalent in the broader category. If we then only consider such $E$-local things, we get a simplification of the category, with a simplified notion of equivalence, at least if we choose $E$ to give us something we can understand properly. 

The earlier mentioned example of Bousfield localization at $\pi_\ast$-isomorphisms is also an example of localization at a homology theory. This is because $\mathbb{S}$-homology is precicely homotopy groups of spectra. This means in particular (if we forget that we have restricted to only stable model categories for a second) that we get the stable model category of spectra as the localization $Sp_\mathbb{S}$ om the level-wise model category of spectra. This means that the stable model structure is really intrinsic to the category of spectra, as the sphere spectrum is the monoidal unit. 

So we have at least one example, but as mentioned in the introduction we are in this blog post primarily interested in another localization.  

### $p$-localization

For the rest of this post we fix a prime number $p$. 

The first proper example — and for now the most important — of a Bousfield localization will be so-called $p$-localization of spectra. As we above have developed the notion of localizing spectra at homology theories, we first need to define and construct a spectrum which gives us $p$-local behaviour when localizing at it. This spectrum is called the $p$-local Moore spectrum, and is a special case of the Moore spectrum of an abelian group. We quickly look at how this spectrum is constructed. 

Let $G$ be an abelian group with free presentation

$$0\longrightarrow F_2\overset{r}\longrightarrow F_1 \longrightarrow G\longrightarrow 0.$$

Such a presentation always exists. Since $F_1$ and $F_2$ are free, we can find sets $I_1$ and $I_2$ freely generating the groups. Think of $I_1$ as the the generators of $G$ and $I_2$ as the relations on these generators. Construct a map 

$$\bigvee_{I_2}\mathbb{S}\overset{\rho}\longrightarrow \bigvee_{I_1}\mathbb{S}$$

such that $\pi_0(\rho)=r$. Such a map always exists as $[\mathbb{S}, -]$ commutes with wedges, because wedge is the coproduct in the category of pointed topological spaces. The cofiber of the map $\rho$ is denoted $M(G)$ and is called the *Moore spectrum of* $G.$

This is exactly the analogous construction as one does for Moore spaces, except now with spectra instead. Often the first reason we meet Moore spaces in an introductory algebraic topology course is to show that there are topological spaces with any group $G$ as its singular homology, i.e. some space $M$ such that 

$$\widetilde{H}_i(M;\Z) = 
\begin{cases}%
G, i=n \\\\%
0, i\neq n %
\end{cases}$$

This is also the case for the Moore spectrum, or at least the analogous thing. Recall that reduced integral singular homology is represented by the Eilenberg-Maclane spectrum $H\Z$. If $M(G)$ is to act as Moore spaces would we would need $\pi_0(M(G))=G$ and $H_i(M(G);\Z) = \pi_i(M(G)\wedge H\Z)=0$ for $i>0$. Since spectra can have negative homotopy groups, we also should also have $\pi_i(M(G))=0$ for $i<0$. All these hold for the above defined spectrum $M(G)$, making them really nice to localize at, because their localization often acts on the homotopy groups as normal algebraic localization. 

These Moore spectra are essentially unique, in the sense that changing the free presentation results in a weakly equivalent spectrum. The assignment $G\longmapsto M(G)$ is unfortunately not functorial, but the construction is still useful due to their localization properties. 

Recall that the $p$-local integers $\Z_{(p)}$ is the subgroup of the rationals $\mathbb{Q}$ where all primes except $p$ are invertible. We then get a Moore spectrum $M(\Z_{(p)})$ called the $p$-local Moore spectrum. Localization with respect to the homology theory corresponding to $M(\Z_{(p)})$ is called $p$-localization of spectra. This is a functor $$L_{(p)}:Sp\longrightarrow Sp_{(p)}=: Sp_{M(\Z_{(p)})}.$$ The category $Sp_{(p)}$, called the category of $p$-local spectra, has some really remarkable properties which we will meet in later posts. We have mentioned a few of them in the outro. In certain ways it is much easier to work with, and much easier to understand. We can also get back much of the interesting information about a spectrum $X$ by looking at all of its $p$-localizations. 

So, what are the $M(\Z_{(p)})$-equivalences, the $M(\Z_{(p)})$-local objects and the $M(\Z_{(p)})$-acyclic objects? All these three can be described nicely from the following general fact. 

Given a spectrum $X$ and a Moore spectrum $M(G)$ for some abelian group $G$, we have a homological universal coefficient theorem, i.e. a short exact sequence

$$0\longrightarrow G\otimes \pi_\ast X\longrightarrow \pi_\ast(M(G)\wedge X)\longrightarrow Tor^\Z (G, \pi_{\ast-1}(X))\longrightarrow 0$$

The middle object is the $M(G)$-homology of $X$, $M(G)_ \ast(X)$. So, this short exact sequence related the $M(G)$-homology of a spectrum to tensoring its homotopy groups with $G$, sometimes called the $G$-homotopy groups. The group $\Z_{(p)}$ is torsion free, which means that $Tor^\Z(\Z_{(p)}, \pi_{\ast-1}(X)) = 0$ and consequently 

$$\pi_\ast (M(\Z_{(p)})\wedge X) \cong \Z_{(p)}\otimes \pi_\ast(X)$$

or in words, the $M(\Z_{(p)})$-homology of $X$ is the homotopy groups (or $\mathbb{S}$-homology if you like) of $X$ tensored with $\Z_{(p)}$. 

We can then describe the equivalences and the local and acyclic objects. Recall that a map $f:A\longrightarrow B$ is called an $E$-equivalence if it induces an isomorphism in $E$-homology. Hence a $M(\Z_{(p)})$-equivalence $f$ is precisely a map that induces an isomorphism

$$f_*:\Z_{(p)}\otimes \pi_\ast(X)\longrightarrow \Z_{(p)}\otimes \pi_\ast(Y)$$

of the $p$-local homotopy groups. In particular, multiplication by $p$ on a spectrum $X$ — defined by $p\cdot id_X:X\longrightarrow X$, which is well defined as $Map(X, X)$ is an abelian group, i.e. a $\Z$-module — is an $M(\Z_{(p)})$-equivalence. 

A spectrum $X$ is $M(\Z_{(p)})$-acyclic if it is $M(\Z_{(p)})$-equivalent to a point. Since $M(\Z_{(p)})$-equivalences are the ones inducing isomorphisms on $p$-local homotopy groups, we have that $X$ is $M(\Z_{(p)})$-acyclic precisely when all of its $p$-local homotopy groups are trivial. 

The last part is the $M(\Z_{(p)})$-local objects. In order to get the simplest form they take we introduce a definition, which will be very important in later posts as well. It is also connected to a famous open problem in stable homotopy theory, which we will most likely encounter later. 

<span style="color:orange"> **Definition:** </span> A Bousfield localization $L_E:Sp\longrightarrow Sp_E$ is called *smashing* if $L_EX \simeq L_E\mathbb{S}\wedge X$. 

We always have a map $L_E X\longrightarrow L_E\mathbb{S}\wedge X$ that is an $E$-equivalence, so a we really ask wether the object $L_E\mathbb{S}\wedge X$ is $E$-local. This depends crucially on the localized sphere. 

Why do we bring this definition into the story now? Because $p$-localization is smashing. Hence all $M(\Z_{(p)})$-local objects are of the form $M(\Z_{(p)})(\mathbb{S})\wedge X$ for some spectrum $X$. We denote $M(\Z_{(p)})(\mathbb{S}):= \mathbb{S}_{(p)}$ and call it the $p$-local sphere spectrum. Thus, all $p$-local objects are of the form $\mathbb{S}_{(p)}\wedge X$. 

The homotopy category of $p$-local spectra, $HoSp_{(p)}$, is called the $p$-local stable homotopy category. By the earlier discussion it consists of bifibrant objects (in the stable model structure on normal spectra, see [this post]({{<ref "posts/2021/the-stable-homotopy-category">}}) for the construction) on the form $\mathbb{S}_{(p)}\wedge X$, and homotopy classes of maps. Because $p$-localization is smashing, we can also describe the category $Sp_{(p)}$ as modules over the $p$-local sphere spectrum. This is because $\mathbb{S}_{(p)}\wedge X$ is an $M(\Z_{(p)})$-module together with the fact that any module over $M(\Z_{(p)})$ is $M(\Z_{(p)})$-local. This is true in general for any smashing localization, i.e. if $E$-localization is smashing, then $$Sp_E \simeq L_E(\mathbb{S})-Mod_{Sp}.$$ This can also be seen from a really cool [monad]({{<ref "posts/2020/vertical-monoids">}}) argument, that we will hopefully look at in the future. 

## Outro

We mentioned earlier that the category of $p$-local spectra has some advantageous properties over all spectra, but we have not yet seen what these are. We wont go through these in detail yet — they require their ow posts — but we simply mention a few. One of the nice thing about $Sp_{(p)}$ is that is nicely "splits" into layers. Studying these layers allows us much better understanding of $Sp_{(p)}$ than simply studying global behaviour. How do we get these layers? In the [previous post]({{<ref "posts/2021/complex-cobordism-cohomology">}}) we looked at the complex cobordism spectrum, and we can now ask ourselves: How does the $p$-local complex cobordism spectrum $MU_{(p)}$ look? It turns out that this spectrum splits into a sum of more easily understandable spectra, called Brown-Peterson spectra $BP(n)$. These are some of the first instances where we can study periodic behaviour in stable homotopy theory. From the Brown-Peterson spectra we can form even simpler spectra, called Johnson-Wilson spectra $E(n)$. Localizing the category of $p$-local spectra at $E(n)$ is called chromatic localization, and is the start of chromatic homotopy theory. The categories $Sp_{E(n)}$ are the different layers in $Sp_{(p)}$. These layers also consists of smaller pieces, $Sp_{K(n)}$, sometimes called monochromatic spectra. But here the picture stops. We can localize no further. The pieces $Sp_{K(n)}$ are the smallest bits of $Sp_{(p)}$ we can study using the localization framework. The spectra $K(n)$ are called Morava $K$-theories, and feature heavily in my phd-project. Hence we need to understand them, which we will do in a blog post soon. 

Another nice feature (really due to the same as above) is that the $p$-local stable homotopy category has a really nice tensor triangulated structure. Given a tensor triangulated category we can create something similar to [the spectrum of a ring]({{<ref "posts/2021/schemes">}}) from this category by studying certain nice subcategories. Due to the similarity with the spectrum of a ring, we also call these the (Balmer) spectrum of a tensor triangulated category. The spectrum of $HoSp_{(p)}$ is neatly described by its smallest pieces, namely $K(n)$. We will also tell this story soon, as it is really fascinating. But for now, this is it. We have described the category of $p$-local spectra, which was what we set out to do.