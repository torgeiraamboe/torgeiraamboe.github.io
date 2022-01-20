
---
title: "Brown-Peterson cohomology"
date: 2022-01-20
draft: false
katex: true
categories: ["Stable homotopy theory"]
tags: ["Spectra", "Cohomology"]
---

Over the holidays sadly Edgar H. Brown passed away. He was one of the influential men behind many of the concepts this blog has featured and will feature in the future. This post is in particular focused on one of these concepts, namely Brown-Peterson cohomology and the Brown-Peterson spectrum. 

In the [last post]({{<ref "posts/2021/bousfield-localization">}}) we developed the category of $p$-local spectra, and in [the post before that]({{<ref "posts/2021/complex-cobordism-cohomology">}}) we explored complex cobordism cohomology. Today we will merge these two together, and try to understand what happens to the complex cobordism spectrum $MU$ when we travel to the $p$-local category. The spectrum $MU$ is a normal spectrum — it is not $p$-local. But, as we now know, we can create a $p$-local version of it by $p$-localizing it. We then get a spectrum $MU\wedge \Z_{(p)}$ which we simply denote by $MU_{(p)}$. This is the spectrum we want to understand today. The idea for understanding $MU_{(p)}$ will be to split it into nicer pieces which have similar — and actually better — properties. 

## Decomposing spectra

In order to break apart $MU_{(p)}$ into nicer pieces we need to understand two things: 

1. What does this mean?
2. How can we do this? 

In mathematics the concept of decomposing objects are very important. In its essence it gives us the opportunity to break apart complicated things into easier to understand — more fundamental — pieces. Take for example the fundamental theorem of finitely generated abelian groups. This gives a decomposition of a finitely generated abelian group $G$ into a direct sum of the familiar infinite cyclic groups and primary cyclic groups, i.e. $G\cong \Z^k\oplus \Z/q_1\oplus\cdots \oplus \Z/q_1$, where $q_i = p^t$ for some prime $p$. More generally we say that we can decompose $G$ into two groups $H_1$ and $H_2$ if we have an isomorphism $G\cong H_1\oplus H_2$. This is the same style of decomposition we want for $MU_{(p)}$. In the category of spectra we also have an analogue of the direct sum, namely the wedge product, $\vee$. Decomposing the spectrum $MU_{(p)}$ then means that we have an equivalence $MU_{(p)} \simeq F_1\vee F_2$ for two $p$-local spectra $F_1$  and $F_2$. Ok, that answers the first point.

The strategy we will use is to do the second point is to construct an idempotent self map $e:MU_{(p)}\longrightarrow MU_{(p)}$. This idea is inspired from ring theory where an idempotent self map of rings gives us decompositions. More precisely, given a commutative ring $R$ and an idempotent endomorphism $e:R\longrightarrow R$, we get a decomposition $R\cong eR\oplus (1-e)R$. As $MU$ is a ring spectrum we also get an induced ring structure on it $p$-localization, i.e. $MU_{(p)}$ is also a ring spectrum. If we for a moment believe that what works for rings also works for ring spectra, then constructing an idempotent map $e:MU_{(p)}\longrightarrow MU_{(p)}$ should get us a splitting $MU_{(p)}\simeq eMU_{(p)}\vee (1-e)MU_{(p)}$. It is not true that absolutely *everything* that work for rings work for ring spectra, but it is not too far off. Ring spectra[^1] can be thought of as the homotopical analogue of rings, and this analogue actually gets us quite far as we will see in the future. 

## $p$-typical formal group laws

The idempotent $e$ will come from a familiar structure, namely from the fact that $MU$ is the universal complex oriented cohomology theory. We have discussed this before, but let's recall what this means. 

<span style="color:orange"> **Lemma:** </span> Let $E$ be a complex oriented cohomology theory with orientation $x^E$. Then there exists a unique multiplicative map $f:MU\longrightarrow E$ such that $f^\ast (x^{MU})= x^E$, where $x^{MU}$ is the canonical complex orientation on $MU$. In other words, complex orientations on $E$ are in one to one correspondence with multiplicative maps $MU\longrightarrow E$. 

We also know that $MU$ carries the universal formal group law $G$ over its coefficient ring, the Lazard ring $L$. What happens then when we $p$-localize? The coefficient ring becomes $L\otimes \Z_{(p)}$ and we can ask whether we again get some sort of universal formal group law, now not for all rings but for all $\Z_{(p)}$-algebras. To reiterate the question formally: Is there a formal group law over $L\otimes \Z_{(p)}$ that is universal among $\Z_{(p)}$-algebras? The answer is yes, and it is simply the image $G_{(p)}$ of the universal group law $G$ under the canonical map $L\longrightarrow L\otimes \Z_{(p)}$. Thus also orientations on $p$-local spectra are classified by multiplicative maps $MU_{(p)}\longrightarrow E$. 

We are now going to do something that might seem very unmotivated, due to the fact that there are some tricky mathematics lying in the background that we will not cover in this post. For the interested this is called $p$-typical formal group laws. My intuition behind them is that they are nice formal group laws over $\Z_{(p)}$-algebras that have generators in exponential periodic degrees. We will see what we mean by this soon. 

Ok, take the formal group law $G_{(p)}$ over the ring $L\otimes \Z_{(p)}$ as described above. Recall that the Lazard ring $L$ is the ring $\Z[b_1, b_2, \ldots]$ where $b_i$ has degree $2i$. We construct an endomorphism $\psi:L\otimes \Z_{(p)} \longrightarrow L\otimes \Z_{(p)}$ by $\psi(b_i) = b_i$ if $i=p^k-1$ for some $k$, and $\psi(b_i)=0$ otherwise. The image of $\psi$ is a subring $V\subset L\otimes \Z_{(p)}$, more specifically it is the subring $\Z_{(p)}[v_1, v_2, \ldots ]$ where $v_i$ has degree $2(p^i-1)$. This is the periodicity in degrees we mentioned above. This ring carries a formal group law $G^p$ that is universal among $p$-typical formal group laws. This means that among $p$-typical formal group laws, $V$ acts like the Lazard ring does for all formal group laws. Because of this $V$ is often denoted $L^p$ and called the $p$-typical Lazard ring.

A question we can ask is then: Is being $p$-typical a strict property? It turns out that it is not. In fact, by a theorem of Cartier, all formal group laws over a $\Z_{(p)}$-algebra is strictly isomorphic to a $p$-typical formal group law. Hence using the ring $V$ and the universal $p$-typical formal group laws gives us some advantages over using $L\otimes \Z_{(p)}$ and $G_{(p)}$ as we now have nice periodic behavior and a nicely defined ring more similar to the Lazard ring. We don’t really understand yet why this periodic behavior is important, but we will see this in the future. Intuitively, if we choose some arbitrary even degree, then $L$ has incredibly many elements in that degree. Using $V$ allows us to pick out only one of these in an orderly exponential manner. This has the benefits of reducing the overall complexity of the theory immensely. Almost all cohomology theories we will work with in the future has some kind of periodic property, an it all stems from the ones just described. 


## The image of Quillen's self map

The important fact about the universal formal group law $G$ over the Lazard ring $L$ is that we know that there is a complex oriented spectrum that carries $G$ and has $L$ as its coefficient ring. This spectrum is as we know $MU$ — the spectrum representing complex cobordism cohomology. Now we have constructed a new ring $V$ and a new type of universal formal group law, $G^p$. We would like there to be a spectrum with the same properties as $MU$, i.e. a spectrum that carries $G^p$ and has $V$ as its coefficient ring. Is there such a spectrum? As the title of this post might spoil, the answer is yes. It is the spectrum $BP$, representing Brown-Peterson cohomology. As we discussed earlier, we will construct this by splitting $MU_{(p)}$ into pieces using an idempotent decomposition. So, the next thing we need to do is define this idempotent. 

Take the canonical orientation $x_{MU}$ on $MU$. When we $p$-localize we get an induced orientation $x_{MU_{(p)}}$ on $MU_{(p)}$. This orientation corresponds to a formal group law over $MU_{(p)}^\ast (pt) \cong L\otimes \Z_{(p)}$, which is a $\Z_{(p)}$-algebra. By the theorem of Cartier mentioned above, this formal group law is isomorphic to a $p$-typical formal group law, again over $MU_{(p)}^\ast (pt)$. This formal group law corresponds to an orientation on $MU_{(p)}$, different from $x_{MU_{(p)}}$. Orientations on $p$-local spectra are as mentioned earlier classified by maps $MU_{(p)}\longrightarrow E$, hence this new orientation gives us our map

$$
e: MU_{(p)}\longrightarrow MU_{(p)}.
$$

This map is an idempotent map, which by our intuitive reasoning in the beginning of the section corresponds to a decomposition 

$$
MU_{(p)} \cong eMU_{(p)}\vee (1-e)MU_{(p)}.
$$ 

The image of $e$, i.e. $eMU_{(p)}$ is the spectrum we define[^2] to be $BP$ — the Brown-Peterson spectrum. In the original article by Brown and Peterson they defined this spectrum even more generally, not even using $p$-localization. The method we have used here, first used by Quillen, creates a spectrum that is isomorphic after $p$-localizing the original Brown-Peterson spectrum. Since the original was created not requiring a prime $p$, the notation for the spectrum $BP$ has a tradition of omitting the reference to $p$, but we should never forget that it is always there in hiding. 

There are some other ways to construct $BP$ as well, some we can briefly describe. In the post about [formal group laws]({{<ref "posts/2021/formal-group-laws">}}) we described how we get a formal group law from any complex oriented cohomology theory. We asked the natural question: Given a formal group law, ca we construct a complex oriented cohomology theory corresponding to it? We answered briefly that this was not the case, but mentioned that with some restrictions on the formal group law that this is the case. Why do we need the restriction? 

One way of trying to construct a complex oriented cohomology theory from a formal group law is to use the universal one, $MU$. In particular, given a ring formal group law $F$ over a ring $R$ we can construct a functor $E^\ast (-):Top\longrightarrow GrAb$ by defining for a topological space $X$

$$
E^\ast (X) = R\otimes_{MU^\ast (pt)} MU^\ast (X).
$$

Here we give $R$ an $MU^\ast(pt)$-module structure via $F$, hence the tensor product makes sense and also incorporates the formal group law. This looks like it should be a cohomology theory, and we ask if this is the case? It is very close, i.e. it satisfies all but one axiom — the exactness axiom. We can't guarantee that the functor sends cofiber sequences to long exact sequences. They are sent to complexes of modules, but they might not be exact. If we think of $E^\ast(-)$ as the composition of the functors $MU^\ast(-)$ and $R\otimes (-)$ then this failure becomes apparent, as the tensor functor $R\otimes(-)$ is not exact. If we recall some homological algebra then we can get that this functor is exact, and hence that $E^\ast(-)$ as defined above is a cohomology theory, by requiring that the ring $R$ is flat [^3].

Ok, are almost at Brown-Peterson cohomology. Let $R$ be the ring $V=\Z_{(p)}[v_1, v_2, \ldots]$ as defined earlier. This ring is flat, hence the functor $X\longmapsto V\otimes_{MU^\ast(pt)}MU^\ast(X)$ is a cohomology theory. By [Brown's representability theorem]({{<ref "posts/2021/a-first-look-at-spectra">}}) — yes, the same Brown — this functor is represented by a spectrum, and this spectrum is exactly $BP$. 

You might ask: what about the other part of $MU_{(p)}$? We have now split open $MU_{(p)}$ and focused only on one of its pieces, $BP$, but what about the remaining part? It turns out that the other part is also $BP$, at least up to suspension. What we mean is that there is an equivalence 

$$
BP[x_{2i}, i\neq (p^j-1)] \simeq MU_{(p)},
$$

which in particular means $MU_{(p)}$ is glued together from many copies of $BP$, just shifted by suspension to get the generators to be correct. 

## The coefficient ring of $BP$

The first thing we need to figure out about $BP$ is its coefficient ring, $BP^\ast(pt)$. Due to the two constructions above we can do this in two ways. In the first construction we used the idempotent $e$ to construct a splitting of $MU_{(p)}$. This idempotent induces a map on cohomology, in particular on the cohomology of a point, i.e. on the coefficient rings:

$$
e^\ast(pt):MU_{(p)}^\ast(pt)\longrightarrow MU_{(p)}^\ast(pt)
$$

Since $e$ is an idempotent, $e^\ast(pt)$ will also be one. Luckily for us we have already seen this map, and it is in fact the map $\psi$ used to create the $p$-typical Lazard ring $V$ from $L\otimes \Z_{(p)}$. As the coefficient ring of $BP$ is the image of $e^\ast(pt)$, i.e. the image of $\psi$, we have 

$$
BP^\ast(pt) \cong V \cong \Z_{(p)}[v_1, v_2, \ldots]
$$

where $|v_i| = 2(p^i-1)$.  Since we know $V$ has a universal $p$-typical formal group law, we get that $BP$ is the spectrum that is universal among complex oriented spectra with $p$-typical formal group laws. This means in some sense that $BP$, not $MU_{(p)}$, is the true analogue of $MU$ among $p$-local spectra. 

We can also see that $BP$ has the $p$-typical Lazard ring as its coefficient ring by using the alternative construction mentioned above. By evaluating the functor $BP^\ast(-)$ at a point we get

$$
BP^\ast(pt) = V\otimes_{MU^\ast(pt)}MU^\ast(pt) \cong V. 
$$

This is of course the case for all spectra defined using this method, i.e. that the spectrum $E$ representing the cohomology theory $E^\ast(-) = R\otimes_{MU^\ast(pt)}MU^\ast(-)$ has coefficient ring $R$. 

## Why care about $BP$?

We have now constructed $BP$ and shown that it behaves like $MU$ in the category $Sp_{(p)}$ of $p$-local spectra. So if we are convinced that $MU$ is interesting, we should also be convinced that $BP$ is interesting. This is however as far as we have gotten, so lets mention some other things we can learn from studying $BP$. This will not be detailed and rigorous, but we will meet some of the ideas below in later posts. 

One intuitive reason for why $BP$  is interesting is that it can be thought of as a midway point between the $p$-local sphere spectrum $\mathbb{S}_ {(p)}$ and the $p$-local Eilenberg-Mac Lane spectrum $H\Z_{(p)}$. The sphere spectrum has a terribly complicated homotopy, but a easy homology, while the Eilenberg-Mac Lane spectrum has easy homotopy and terribly complicated homology. As a middle ground $BP$ has both homotopy and homology that are managable in complexity — not easy by any stretch, but not terribly complicated either. 

The Brown-Peterson spectrum also have nice rings of cooperations. Recall that cohomology operations of some cohomology theory $E^\ast$ are natural transformations $E^\ast(-)\longrightarrow E^\ast(-)$. These are represented by maps of spectra $E\longrightarrow E$, hence the ring of cohomology operations of $E$ is $E^\ast E = [E, E]$, the $E$ cohomology of $E$. Similarily we define homology cooperations of $E$ to be $E_\ast E = \pi_\ast(E\wedge E)$, the $E$ homology of $E$. These cooperations are managable for $BP$, and they have been calculated to be

$$
BP_\ast BP \cong V[t_1, t_2, \ldots]
$$

where the $t_i$’s are generators of degree $2(p^i-1)$ in  $BP_{2(p^i-1)}BP$. 

Another important feature is that we can use $BP$ to calculate the stable homotopy groups of spheres. It turns out that $BP_\ast BP$ is flat over the coefficient ring of $BP$, which we from above know is $V$. This makes $BP_\ast BP$ — by some lemmas and some constructions — into both an algebra and a coalgebra over $V$. In particular, the pair $(V, BP_\ast BP)$ has the structure of a flat Hopf algebroid. We will come back to what this means in another post, but we can think of it as a Hopf algebra with many objects. If we take the $BP$ homology of some topological space $X$, i.e. $BP_\ast X$ then this becomes a comodule over $BP_\ast BP$. The category of comodules over a flat Hopf algebroid turns out to be abelian, which means we can make sense of derived functors, in particular $Ext$. By using $Ext$ we can then construct certain spectral sequences, in particular the Adams-Novikov spectral sequence

$$
Ext^{\ast,\ast}_ {BP_\ast BP}(BP_\ast(pt), BP_\ast(pt)) \implies \pi_\ast \mathbb{S}_{(p)}
$$

that converges to the homotopy groups of the $p$-local sphere spectrum. This is essentially just studying the $p$-torsion part of the stable homotopy groups of spheres, so doing this for all $p$ gives us the whole stable homotopy groups. 

This was for now all I wanted to say about Brown-Peterson cohomology and the Brown-Peterson spectrum. Next time we will use it to construct new spectra and new homology theories which are even easier to manage than $BP$. This will eventually lead us to two spectrums $E(n)$ and $K(n)$ which will be our main focus for a couple of years. My PhD project is about understanding certain relationships between these two spectra, so I think we will be very familiar with them after some time!  

[^1]: If we want to be really precise with this analogue we should use $\mathbb{E}_\infty$ ring spectra here, but that is a story for another day. 

[^2]: We are cheating a bit here. The map is actually only an idempotent up to homotopy, so considering this splitting is a bit wrong. We can fix this by using the so-called telescopes of $e$ and $(1-e)$ instead, but this theory we have chosen to save for later. 

[^3]: In fact, Landweber proved that an even weaker property is sufficient, now called Landweber exactness. The result above is then formalized in the famous Landweber exact functor theorem, often called just LEFT.