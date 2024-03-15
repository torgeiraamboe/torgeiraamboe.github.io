---
title: "Sha-algebras"
date: 2021-04-19
draft: false
tags: ["A_infinity algebras", "Homotopy", "Stasheff associahedra"]
categories: ["Homotopy theory"]
series: ["Homotopy algebras"]
math: true
cover:
    image: "images/K4_header.png"
---

This is part four in a sort of connected story about operations in mathematics that are associative up to homotopy. It will probably be beneficial to read [part 1]({{<ref "/posts/2021/homotopy-associativity">}}), [part 2]({{<ref "/posts/2021/spaces-with-operations">}}) and [part 3]({{<ref "/posts/2021/the-associating-homotopy">}}) in advance of this, but it is not required in theory. These previous posts do however build up some intuition and motivation for the object we are looking at today. To quickly recap what we already seen in these previous posts we recall that we started out by looking at how to transfer a group structure on a topological space through an isomorphism. We saw it produced the same structure, so we weakened to looking at transferring it through a homotopy equivalence instead. We then got an operation that was associative only up to homotopy, which we studied a bit through the so called Stasheff associahedra. We then introduced H-spaces and saw that some of these, in particular loop spaces, had the same type of homotopy associative operation. In the latest edition we looked at a more algebraic situation, still heavily motivated by the topology we had discussed earlier. In this situation we explicitly described a ternary operation that we proved was the associating homotopy and saw that we got a certain relation involving the associator and the boundary of the associating homotopy.

## $A_\infty$-algebras

Our goal is to formalize the property of being homotopy associative in the way we have been exploring in the previous posts. Not only that, but we want to have the object being algebraic, as it will allow us to study both algebra and topology at the same time. It is, I think, easier to assign algebraic invariants to topological objects, than topological invariants to algebraic objects. The algebra also helps us formalize topological information in a very rigorous and insightful way, so studying topology through the lens of algebraic information is often not too limiting. Ok, lets jump into the definition, and then explain afterwards how it rigorizes the different things we have discussed in these previous blog posts.

<span style="color:orange"> **Definition:** </span> An $A_\infty$*-algebra* $(A, m)$ is a graded vector space $A = \bigoplus_{i\in \mathbb{Z}} A^i$ together with a family of morphisms $m=\{m_n\}$ consisting of maps $m_n\colon A^{\otimes n}\longrightarrow A$ of degree $2-n$ such that

$$\displaystyle\sum_{r+s+t=n}(-1)^{r+st}m_{r+1+t}(id^{\otimes r}\otimes m_s \otimes id^{\otimes t}) = 0$$

for all $n, s\geq 1$ and $r, t\geq 0$. These relations are often called the Stasheff identities or the coherence relations in $A$.

This looks highly complicated and abstract, but we will see that we already are familiar with this structure and what the relations mean. To see this we investigate what happens for some low $n$‘s.

$\mathbf{n=1 :}$ The Stasheff identity then simply becomes 

$$0 = (-1)^{0+0}m_1 \cdot (m_1) = m_1^2$$

$\mathbf{n=2 :}$  This sum is a bit more complicated, but still not too bad. We have

$$0 = (-1)^{1}m_2\cdot(Id\otimes m_1)+(-1)^{0}m_1\cdot (m_2)+(-1)^{1}m_2\cdot (m_1\otimes Id)$$

which reduces to $m_1 m_2 = m_2(m_1\otimes Id + Id\otimes m_1)$.

$\mathbf{n=3 :}$ This sum is again going to be more complicated, but lets keep our tongues straight and our heads cold and do this one as well.

\begin{aligned} 
0 
&= (-1)^{2}m_3(Id\otimes Id \otimes m_1) \\\\
&\quad + (-1)^{2}m_3(Id\otimes m_1 \otimes Id) \\\\
&\quad + (-1)^{2}m_3(m_1\otimes Id \otimes Id) \\\\
&\quad + (-1)^{2}m_2(m_2\otimes Id) \\\\
&\quad + (-1)^{1}m_2(Id\otimes m_2) \\\\
&\quad + (-1)^{0}m_1(m_3)
\end{aligned}

which reduces to

$$m_2(id\otimes m_2) - m_2(m_2\otimes id) = m_3(m_1\otimes id \otimes id + id\otimes m_1 \otimes id+id\otimes id \otimes m_1) + m_1m_3.$$

We wont show the relation for $n = 4$ until the end, and we will not present the ones for $n>4$ as these get more and more complex, and less and less recognizable.

The first condition looks very familiar and is easily recognized as the cochain condition. This means that our graded vector space is a cochain complex with respect to $m_1$. The second one is then relatively easy understand when we interpret $m_1$ as a differential. It tells us that $m_1$ is a derivation with respect to $m_2$. If we apply this to an element $v_1\otimes v_2$ and remember to use the Koszul grading rule we get:

\begin{aligned}
(m_2(m_1\otimes id)+m_2(id\otimes m_1))(v_2 \otimes v_1) &= m_2(m_1\otimes id)(v_1\otimes v_2) + m_2(id\otimes m_1)(v_1\otimes v_2) \\\\
&= (-1)^{|id||v_1|}m_2(m_1(v_1)\otimes v_2) + (-1)^{|m_1||v_1|}m_2(v_1\otimes m_1(v_2))
\end{aligned}

Since the identity morphism has degree $0$ the first sign vanishes, and since $m_1$ has degree $1$ we are left with $(-1)^{|v_1|}$ as our second sign, i.e. 

$$m_2(m_1(v_1)\otimes v_2) + (-1)^{|v_1|}m_2(v_1\otimes m_1(v_2)).$$

We just figured out that $m_1$ acts as a differential, so for just a moment let it be denoted by $d$. Since $m_2$ takes two vectors and produces one vector, we can interpret this as a product. If we write $m_2(v_1\otimes v_2)=v_1\cdot v_2$ for this product, we now get a more familiar equation:

$$d(v_1\cdot v_2) = d(v_1)\cdot v_2 + (-1)^{|v_1|}v_1\cdot d(v_2)$$

which we recognize as the graded Leibniz rule.

The third condition should be recognizable by the [previous post]({{<ref "/posts/2021/the-associating-homotopy">}}) in this little series. We recognize the left hand side as the associator of $m_2$ and the right hand side as the boundary of $m_3$ where now $m_1$ is the differential. Since the right hand side is not necessarily equal to zero, we see that the product is not necessarily associative, as expected by the nature of this series. If in fact $m_3 = 0$, then we see that the associator is zero, and hence the product $m_2$ is associative. As we can see, $m_2$ is also associative if $m_1$ is zero.

As we see by the first two relations, these look an awful lot like the dg-algebras we defined last time. In fact we have just showed that an $A_\infty$-algebra where $m_3 = 0$ is a dg-algebra. This also means that we can view any dg-algebra $(A, m, d)$ as an $A_\infty$-algebra, by letting the multiplication $m$ be the map $m_2$, the differential $d$ be the map $m_1$ and letting $m_i=0$ for all $i\geq 3$. Hence, a dg-algebra is a kind of trivial, or easy version of an $A_\infty$-algebra.

## Relationship with the boundary operator

When we looked at $m_3$ being the associating homotopy of $m_2$, i.e. that $m_3$ is the homotopy that connects the two different ways of multiplying three elements two times, we defined a boundary operator 

$$\partial (-) = d(-)-(-1)^{|-|}(-)d_{A^{\otimes 3}} $$

on the complex $Hom(A^{\otimes 3}, A)$ where the different graded components are given by the degrees of the maps. We can do this more generally for higher arity maps, i.e. for a map $f\colon A^{\otimes n}\longrightarrow A$ we get

$$\partial f = df -(-1)^{|f|}d_{A^{\otimes n}}$$

where $d_{A^{\otimes n}}= \sum_{k=0}^{n}(id^{k}\otimes d\otimes id^{\otimes n-k})$. This allows us to look at $\partial m_n$ and its relation to the Stasheff identities in the following way: Consider the extremal decompositions of the number $n$ into $r+s+t$, i.e. the one where $s=n$ and the ones where $s=1$. The former gives us the part of the Stasheff identity given by $m_1(m_s)$ and the latter the sum

$$\sum_{r=0}^{n-1} (-1)^{n-1}m_n(id^{\otimes r}\otimes m_1\otimes id^{\otimes n-r-1})$$

As mentioned above, the differential is given by $m_1$, meaning that these two parts of the Stasheff identity perfectly matches the boundary operator applied to $m_n$! Hence if we want, we can reformulate the Stasheff identities as

$$\partial m_n = - \sum_{r+s+t=n}(-1)^{r+st}m_{r+s+t}(id^{\otimes r}\otimes m_s\otimes id^{\otimes t})$$

where $r,s,t\geq 1$. If we in this case let $n=3$ we see that we get exactly the scenario we had last time with the boundary of the homotopy $m_3$. In this way, the higher arity maps $m_n$ are interpreted as homotopies between certain combinations of the lower arity maps. These combinations are exactly the topological boundaries of the Stasheff associahedra. Let's round off by seeing this connection for $n=4$.

Recall that the fourth Stasheff associahedra is a pentagon

![Error loading image](images/K4_1.png)

where we interpret the vertecies as ways to multiply four elements as follows;

![Error loading image](images/K4_2.png)

or written in more appropriate notation;

![Error loading image](images/K4_3.png)

As we already know that $m_3$ gives a homotopy between $m_2(id\otimes m_2)$ and $m_2(m_2\otimes id)$, then for example $m_2(id\otimes m_3)$ gives a homotopy between $m_2(id\otimes m_2(id\otimes m_2))$ and $m_2(id\otimes m_2(m_2\otimes id))$. We can in this exact fashion also put in the homotopies that form the edges of $K4$. We then get:

![Error loading image](images/K4_4.png)

As we see in the picture we think of the center of $K4$, or the $2$-cell inside the boundary, as the map $m_4$. If we calculate the boundary, letting the vertices be enumerated from the left, going counter clockwise, we get

$$\partial m_4 = m_2(1\otimes m_3) - m_3(1\otimes 1\otimes m_2) - m_3(m_2\otimes 1\otimes 1) + m_2(m_3\otimes m_1)+m_3(1\otimes m_2\otimes 1)$$

which is exactly the Stasheff identity for $n=4$ in the earlier described boundary interpretation! This means that an $A_\infty$-algebra is really a cochain complex with a multiplication that is associative up to homotopy. This homotopy satisfies the pentagon equality up to homotopy, and so on ad infinitum. This is what gives $A_\infty$-algebras their other name, strongly homotopy associative algebras, shortened sometimes to sha-algebras. They are not widely used throughout mathematics, but they are for example useful in stable homotopy theory, string theory (in particular open string field theory) and the deformation theory of algebras.

These objects feature heavily in my master thesis, which is why I have devoted these last few blog posts to them. In my project I use these to study some properties of dg-algebras. I have about a month and a half until I hand in the thesis, so after that Ill do a blog post explaining the project in more detail, as well as the results featured in it. The next post now I think will be about another project I’m starting next semester.


<style>body {text-align: justify}</style>