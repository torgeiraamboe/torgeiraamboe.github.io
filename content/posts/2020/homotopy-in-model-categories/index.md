---
title: "Homotopy in model categories"
date: 2020-06-07
draft: false
tags: ["Cofibrations", "Fibrations", "Homotopy", "Model categories"]
categories: ["Homotopy theory"]
series: ["The fibration series"]
katex: true
cover:
    image: "images/relation.png"
---

This is part 8 of a series leading up to and exploring model categories. For the other parts see [the series overview]({{< ref "/series/the-fibration-series" >}}). 

Last time we finally defined the model category, gave some examples and tried (kind of) to give a motivation to why they are interesting and how they set the stage for homotopy theory. The first time I read the definition I was a bit confused about the lack of mention of homotopy, or at least some prototype of it that I could connect with. This structure on a category is supposed to embody where homotopy theory works, but failed to immediately convey that to me. But, that said, we will today go through the construction of homotopy, and prove that it is an equivalence relation on maps in nice cases. These cases we mentioned in the previous part, and will be maps between objects that are both fibrant and cofibrant, which I will refer to as bifibrant.

## Abstract homotopies

We know from topology that homotopy requires some sort of interval or paths, and the abstract definition will in a way reflect that. What we are going to construct are so called cylinder objects, that imitates taking the product with the interval in regular topological homotopy. Dualy, we are going to define path objects, which will mimic the path space in topology. These two will respectively define left and right homotopies, which will be equivalence classes only on fibrant and cofibrant objects respectively. These two notions of homotopy will coincide and give the same equivalence relation on bifibrant objects. Note that in the definition we are using products $\prod$ and coproducts $\coprod$. Since we work in a model category these always exists because the product is a special case of a limit, and the coproduct is a special case of a colimit, which both exists because a model category is bicomplete.

**Definition (cylinder object):** Given an object $X$ in a model category $C$ we define the cylinder object of $X$, denoted $Cyl(X)$ to be factorization of the codiagonal map $X \coprod X \rightarrow X$ into $$X \coprod X \overset{i_1+i_2} \rightarrow Cyl(X) \overset{p} \rightarrow X,$$ where $p$ is a weak equivalence. If $X\coprod X\overset{i_1 + i_2}\rightarrow Cyl(X)$ is a cofibration, we call $Cyl(X)$ a good cylinder object, and if in addition $p$ is an acyclic fibration, we call $Cyl(X)$ a very good cylinder object.

**Definition (path object):** Given an object $X$ in a model category $C$ we define the path object of $X$, denoted $Path(X)$ to be factorization of the diagonal map $X \rightarrow X\prod X$ into $$X \overset{i}\rightarrow Path(X) \overset{(p_1,p_2)}\rightarrow X \prod X,$$ where $i$ is a weak equivalence. Similarily to the cylinder object, if $Path(X)\overset{p}\rightarrow X\prod X$ is a fibration, we call $Path(X)$ a good path object, and if in addition i is an acyclic cobration, we call $Path(X)$ a very good path object.

By the factorization axiom for model categories **(MC4)** every object has at least one very good cylinder object and one very good path object. It can be useful to use these in some cases, but in other cases we can actually be interested in cylinder and path objects that aren’t necessarily good, or very good. For example, in the Serre model structure on topological spaces, the standard cylinder object $Cyl(X)=X\times I$ is only good when $X$ is a CW-complex.

We now have objects that behave in some of the same ways as the objects used to define homotopy of topological spaces. In topological spaces, the cylinder object is as mentioned the product with the unit interval. When we then define a topological homotopy from this cylinder, we require that the homotopy restricts to the maps we are constructing a homotopy between on each end of the cylinder, and this will be what motivates how we define it in the general setting as well.

**Definition (left homotopy):** Given two maps $f,g: X\rightarrow Y$ we define a left homotopy $h:f\sim_L g$ from $f$ to $g$ to be a map $h: Cyl(X)\rightarrow Y$ such that the following diagram commutes

![Error loading image](images/left_homotopy.png)

**Definition (right homotopy):** Given two maps $f,g: X\rightarrow Y$ we define a right homotopy $h:f\sim_R g$ from $f$ to $g$ to be a map $h: X\rightarrow Path(Y)$ such that the following diagram commutes

![Error loading image](images/right_homotopy.png)

If the cylinder object used to define the left homotopy is a good cylinder object then we call the homotopy a good left homotopy, and similarly if it is a very good cylinder object we call the homotopy a very good left homotopy. The same goes for the path object used to define the right homotopy, which gives us good right homotopies and very good right homotopies.

## Equivalence relation

That homotopy is an equivalence relation is one of the most important and fundamental properties that homotopy has in the category of topological spaces, and hence it should also be important in the general setting. Before we do that, we note that we can upgrade any left homotopy $h$ to a good left homotopy by factoring the map $X\rightarrow Cyl(X)$ into $X\rightarrow Cyl(X)' \overset{\sigma}\rightarrow Cyl(X)$ by the fourth axiom for model categories **(MC4)**. Then $h\circ \sigma$ will be a good homotopy. If $Y$ is fibrant, then we can upgrade it further to a very good left homotopy by using the other factorization on $Cyl(X)\rightarrow X$ to get $Cyl(X)\rightarrow Cyl(X)'\rightarrow X$. Since we assumed $Y$ was fibrant, we have a commutative diagram

![Error loading image](images/very_good_homotopy.png)

where $T$ is a terminal object. The lift comes from the third axiom for model categories and gives the very good left homotopy we wanted. Ok, so we have the opportunity to choose good left homotopies in general, and very good homotopies for fibrant objects. We will use this to prove the following lemma.

**Lemma:** Let $X$ be a cofibrant object. Then left homotopy defines an equivalence relation on $Hom(X,Y)$.

**Proof:** Using $X$ itself as a cylinder object together with the map $f:Cyl(X)=X\rightarrow Y$ as a left homotopy shows that any map $f:X\rightarrow Y$ is left homotopic to itself. It is symmetric since we can compose with the swithing map $X\coprod X \rightarrow X\coprod X$ that just switches the components. This gives a homotopy “in the other direction”. Lastly, let $f_1\sim_L f_2$ and $f_2\sim_L f_3$ be good homotopies with cylinder objects being $Cyl(X)$ and $Cyl(X)'$ respectively. Then the pushout of the diagram $Cyl(X)' \leftarrow X \rightarrow Cyl(X)$ defines a new cylinder object and a homotopy $f_1\sim f_3$. Hence the relation is reflexive, symmetric and transitive which is the definition of an equivalence relation.

Something I have not mentioned yet is that the opposite category of a model category is again a model category. The opposite category has the same weak equivalences, and switches the fibrations and cofibrations. Hence, many proofs in model categories are easier, since we can appeal to duality. For example, since cofibrations are fibrations, fibrant objects are cofibrant and the diagonal is the codiagonal and vice versa in the opposite category, left homotopy is a right homotopy in the opposite category. Hence the same proof as above in the opposite category shows that we can upgrade to a good homotopy and that right homotopy is an equivalence relation on $Hom(X,Y)$ when $Y$ is fibrant. By the way, this duality is the Eckman-Hilton duality in the category of topological spaces, which I referenced in part 3 of the fibration series. Recall that we then switched between loop spaces and suspensions, which are related to these path objects and cylinder objects and hence are dual to each other through the opposite category.

## Relations between the two types of homotopy

When I first worked through this I was a bit uneased by the two different notions of homotopy that does not seem to be immediately identifiable with each other. But, when working with topological homotopy there is a good reason as to why we never see the two different concepts, because in both the Serre and the Strøm model structure, all objects are fibrant. Hence, by the next lemma, the existence of right homotopies always implies the existence of left homotopies in the category of topological spaces, hence we don’t ever need to bother with making the distinction.

**Lemma:** Let $f,g:X\rightarrow Y$ be two maps. If $X$ is cofibrant and $f,g$ are left homotopic then they are right homotopic. Dually, if $Y$ is fibrant and $f,g$ are right homotopic, then they are left homotopic.

**Proof:** Choose a good cylinder object $X\coprod X \overset{i_1 + i_2}\rightarrow Cyl(X) \overset{j}\rightarrow X$ and let $h:Cyl(X)\rightarrow Y$ be a left homotopy between $f$ and $g$. Choose also a good path object $Y\overset{q}\rightarrow Path(Y) \overset{(p_1, p_2)}\rightarrow Y\prod Y.$ We then have a commutative diagram

![Error loading image](images/relation.png)

which has a lift $\overline{h}$ by the third axiom of model categories **(MC3)**. Note here that we used the fact that $i_1$ is an acyclic cofibration which we have not proved, but it can be seen by the two out of three property since $X$ is assumed to be cofibrant together with the fact that it is a composition of two cofibrations. The composition $h\circ i_2:X\rightarrow Path(X)$ gives a right homotopy between $f$ and $g$ as desired. The dual statement has a dual proof.

**Definition (homotopy):** We say two maps $f,g:X\rightarrow Y$ are homotopic, denoted $f\sim g$ if they are both left homotopic and right homotopic.

If we then restrict our attention to just the bifibrant objects we have a well defined notion of homotopy that is an equivalence relation for all of the morphisms between the bifibrant objects. This will allow us next time to look at homotopy equivalences of objects, homotopy classes of maps and finally the homotopy category of a model category.