---
title: "Fibrations"
date: 2020-05-14
draft: false
tags: ["Fibrations", "Homotopy"]
categories: ["Algebraic topology", "Homotopy theory"]
series: ["The fibration series"]
math: true
cover:
    image: "images/lift.png"
---

This is part 1 of a series leading up to and exploring model categories. For the other parts see [the series overview]({{< ref "/series/the-fibration-series" >}}).


My main mathematical interest for the last couple years has been algebraic topology. I feel it suits my needs for intuition, and graphical picturing of what happens. A concept I have been learning more rigorously recently is fibrations, and how to use them in computing homotopy groups and homology groups of different spaces. There is something fun and exciting about computing the homology and homotopy groups of new spaces, as it usually requires different techniques and insight every time, and fibrations have certainly presented some new tools for my calculation toolbox. Since fibrations gives us nice tools, it would be nice to understand them better, and that is my plan for this post. As a remark, all spaces used and mentioned will be topological spaces, and all maps will be continuous.

As a short motivation to why we bother studying fibrations at all we recall one of the standard tools one usually learns in an introductory course in algebraic topology, namely the long exact sequence of relative homology groups from a pair of topological spaces $(X, A)$, where $A\subset X$. This can be thought of as coming from an injection $A \hookrightarrow X$ . Now, what map between spaces do we need in order to get a long exact sequence of homotopy groups? It turns out that we need a fibration $E \rightarrow B$ . Unfortunately fibrations do not, in my opinion, have a very clear, intuitive, and easy definition. That said, I will try my best in two different ways. The first one, which we will discuss today is as a map having a certain property. The second one, which is maybe not really a definition, but certainly paints a nice geometric picture, will be as a generalization of certain families of topological spaces parameterized by another topological space. The latter will be discussed tomorrow, as to not make the post too long.

## Definition 1

Recall that a homotopy between two functions $f,g: X \rightarrow Y$ is a map $h: X\times I \rightarrow Y$ such that $h(x,0)=f(x)$ and $h(x,1)=g(x)$ for all $x\in X$ , i.e. it is a continuous deformation between the functions. Let $p: E \rightarrow B$ be the map we are studying. The property we want the map to have for it to be a fibration is the so-called homotopy lifting property. This roughly says that given a homotopy in $B$, where we can lift one of the endpoints in the homotopy through $p$ to $E$ , then we can lift the entire homotopy up to $E$ . This is at least the picture I have when thinking about fibrations. The proper definition is of course a bit more technical, but I find it helpful to have this rough picture in mind.

**Definition (Hurewicz fibration):** A map $p:E\rightarrow B$ is called a Hurewicz fibration if for any space $X$ with a homotopy $f: X\times I \rightarrow B$ and for any map $\overline{f}_0: X\rightarrow E$ lifting $f$ at the start of the homotopy, i.e. $f(x,0)=p\circ \overline{f}_0$, there exixts a homotopy $\overline{f}:X\times I \rightarrow E$ that lifts f in the same manner as above, i.e. such that $\overline{f}_0 = \overline{f} _{|X\times \{0\}}$ .

Ok, that was a mouthful. But we see the idea of being able to pull the homotopy up to $E$ when we can lift an endpoint. It is easier visualized as a diagram:

![Error loading image](images/lift.png)

The property described as you maybe have guessed is called “the homotopy lifting property”, and a Hurewicz fibration is exactly a map that satisfies this property for all topological spaces $X$ . A bit more general notion is that of a Serre fibration, which satisfies this property for all CW-complexes instead of all topological spaces, and this is what I will refer to as a fibration. A fact about fibrations that i will not prove today atleast, is that the fibers over any point in the basespace all have the same homotopy type. Hence we usually include this when writing a fibration, i.e. we write $F\rightarrow E \overset{p}\rightarrow B$ , where $F$ denotes the fiber.

This fact that all of the fibers have the same homotopy type is the foundation of the next way to think about fibrations. But this exposition is getting quite long, and we have a lot to present to get to the next formulation, so I will save that formulation, and some examples for tomorrow. The definition given here is the standard and most general one, but for me at least, the one we are discussing tomorrow gives this definition a much clearer picture and more intuition.