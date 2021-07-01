---
title: "The Warsaw Circle"
date: 2020-07-31
draft: false
tags: ["Homotopy", "Homotopy groups", "Shape theory", "Warsaw circle"]
categories: ["Algebraic topology"]
katex: true
cover:
    image: "images/warsaw_circle.png"
---

The last few posts have all been of relatively long length and have all taken some time to construct and write. I initially also wanted to produce shorter posts just discussing an example or a calculation etc, and today I tried to do just that, but failed. The post became somewhat longer than intended, but it is really informal and intuitive, so its fine in my opinion.

In a previous post we discussed both weak homotopy equivalences and regular homotopy equivalences, and we have also encountered the Whitehead theorem, which says that any weak homotopy equivalence between CW-complexes is in fact a regular homotopy equivalence. But, we did not discuss their differences, which is what we do in this post.

Anyone who have studied some topology has encountered the classical counter-example used to prove that not all connected topological spaces are path connected, namely the “topologist sine curve”. We can use this space to construct a space which is weakly contractible, i.e. weakly homotopy equivalent to a point, but not contractible, i.e. homotopy equivalent to a point. Hence this space is a counter example to Whiteheads theorem for non-CW-complexes, and shows that that assumption is crucial for the theorem to hold. Recall that a map is called a weak homotopy equivalence if it induces an isomorphism on every homotopy group, and that it is called a homotopy equivalence if there exists a homotopy inverse, i.e. some map such that their composition both ways is homotopic to the respecive identity maps.

## The what circle?

The counter-example we will construct is called the Warsaw circle, and intuitively, it is a topologist sine curve sewn together to form something similar to a circle. Or equivalently, taking a circle, removing a segment, and replacing it with the topologist sine curve.

![Error loading image](images/warsaw_circle.png)

To have a formal mathematical construction, we can construct it as 

$$S_W = \{ (x, sin(\pi/x)) \, | \, 0 < x \leq 1 \} \cup \{(0,y) \, | \, -1 \leq y \leq 1 \} \cup C $$

where $C$ is a continuous curve in the plane connecting $(1,0)$ to $(0,0)$ without intersecting the other parts of the Warsaw circle. The curious thing about this construction is that the Warsaw circle, $S_W$ is actually path connected, which the topologist sine curve is not. The problem on the topologist sine curve is that a non-zero point can’t be connected to $(0,0)$ in the curve, but on the Warsaw circle, you can just go around the other way.

Now, choose a map that sends the one-point space into the Warsaw circle. Since they are both path-connected spaces, they both have a trivial zeroth homotopy group, or equivalently just one path component. The one-point space has the rest of its homotopy groups trivial as well, and it is hopefully clear that the only possible non-zero homotopy group of the Warsaw sircle is its fundamental group.

## A shitty intro to shape theory

To show (rather non-rigouously) that the fundamental group of the Warsaw circle is trivial, we are going to use shape theory, invented (I think) by Karol Borsuk in the 60’s. One more modern interpretation of shape theory is that it is to Čech homology the same as homotopy theory is to singular homology. As such, it is sometimes called Čech homotopy theory instead of shape theory. Čech homotopy has been developed a bit further, and is a bit more general to my understanding, but still this view holds strong if we don't care about their relationship to cohomology. Anyway… Shape theory is the study of spaces that can be embedded in the Hilbert cube 

$$Q = \prod \left[-\frac{1}{n}, \frac{1}{n} \right] $$

and special maps called shape maps between them. Essentially, two spaces are shape equivalent if they are homotopy equivalent when we “thicken” them by some amount. If we thicken the Warsaw circle, it does no longer have that weird topological sine curve bit. This is because that whole infinitely tight together mess is now just a nice blob, and the thickened Warsaw circle is hence homotopy equivalent to the thickened normal circle, which is homotopy equivalent to the standard sircle $S^1$.

![Error loading image](images/warsaw_circle3.png)

Since the Warsaw circle it is not shape equivalent to a point, it cannot be homotopy equivalent to a point. To relate back to the theory hinted at, this shape equivalence says that both the Warsaw circle and the normal circle both have a non trivial first Čech homotopy group, and that they are isomorphic in the Borsuk shape category.

This is all very imprecise and non-rigorous, but if we think about what an element in the fundamental group would be if it was not trivial, it would be a path from the basepoint (the image of the one-point space) to itself, which is not the constant path. For such a path to exist, it has to travel through the topologist sine curve, which we know it cant do, since the topologist sine curve is not path connected. Hence it makes sense intuitively that there should be no such path, and hence that the fundamental group of the Warsaw circle is trivial.

This post became a bit longer than expected, and was maybe a bit less precise than I intended, but I think it was still fun and valuable.