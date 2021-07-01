---
title: "Are There Knots?"
date: 2020-12-02
draft: false
tags: ["Knot theory", "Reidemeister moves", "Tricolorability"]
categories: ["Algebraic topology"]
katex: true
cover:
    image: "images/granny-tricolor.png"
---


Something I have been looking into a bit lately, due to it sadly not being taught at my university is knot theory. This is something I have always known to be a part of topology, and have known to have interesting applications in physics, medicine, chemistry and more. So to rectify the situation I thought I would prove that knots exist. It was also nice to take a brake from all the higher category theory we have been looking into lately!

A knot is defined to be an embedding of the circle $S^1$ into $\mathbb{R}^3$, so immediately we have proven our statement since the identity is an embedding. Hence we at least have one knot, called the unknot or the trivial knot, being just the circle itself. This is of course trivial, so the question “are there knots?” is better phrased as “are there other knots than the unknot?”. This question is not trivial and requires a proof, which is what we are doing today. We say two knots are the same, or are equivalent, if we can transform one into the other by transforming the space $\mathbb{R}^3$ they are embedded in. These transformations are called ambient isotopies, and corresponds to manipulating the knot without cutting or letting parts of the knot pass through itself.

# Reidemeister moves

A nice property of knot theory is that it is a very graphical and visual theory. Everything (at least for us) happens in a low dimension, so we can always draw what we mean. We defined a knot to be an embedding of the circle into Euclidean three-space, but a nice way to draw them are called knot projections, or knot diagrams. This is just the projection of the knot into the plane, where we keep track of the crossings. Lets give an example. The following knot is called the figure-eight knot (maybe you can see why).

![Error loading image](images/figure-8-knot.png)

When we talk about a knot for the rest of this post, we will mean the knot diagram of a knot. Even though we call it a knot, we still don’t know if we can deform, twist and turn this so that it becomes the unknot. A first attempt at distinguishing any knot from the unknot might be to try to count the crossings in its knot diagram. The unknot has no crossings, so any knot with crossings should be a different knot right? Sadly its not that easy. Notice that we can also have something equivalent to the unknot with any number of crossings, by simply twisting the unknot as many times as we need. Since, this simple twisting does not change the knot, we can’t use it to distinguish them either. We call this twisting the type-1 Reidemeister move, and it can be depicted by the drawing below. Remember here that we are only looking at a section of a knot, and not the whole knot.

![Error loading image](images/reidemeister-1.png)

There are two more of these moves that does not change the knot. We call these the type-2 and type-3 Reidemeister moves. The type-2 Reidemeister move can be though of as pulling back a strand that lies over another, and can be visualized as below.

![Error loading image](images/reidemeister-2.png)

The type-3 Reidemeister move can be thought of as pulling a strand over another crossing. This is maybe the most difficult move to intuitively agree that does not change the type of the knot. It can be visualized as below.

![Error loading image](images/reidemeister-3.png)

Ok, so how does these moves help us? Since they do not change the type of the knot, we can use them to get from one knot to another equivalent knot. Hence, two knots are equivalent is there is a sequence of Reidemeister moves connecting them. This fact is a famous theorem by the man Kurt Reidemeister himself.

# Tricolorability

You maybe notices that I used a word we haven’t yet defined, i.e. a strand. A strand is defined to be the part of a knot diagram going from one under-crossing to the next. This is again best seen by a drawing. I have colored one of the four strands in the figure-eight knot seen earlier.

![Error loading image](images/strand.png)

There are an equal number of strands as there are crossings. We are now ready to define the machinery that will allow us to prove that there is a knot that is not the unknot. This machinery is called tricolorability. We say a knot can be tricolored, or is tricolorable, if we can color all its strands using three colors, such that at least two colors are used and such that at each crossing, either all colors are present, or only one is present. Lets check if our only two knots, the unknot and the figure-eight knot are tricolorable. In its simplest form, i.e. just the circle, we se that the unknot is not tricolorable, as a coloring of its unique strand only has one color. We will get back to the fact that all possible knots that are equal to the unknot must also be not tricolorable. What about the figure-eight knot? We start by trying to fill it in after the rules. We chose the same color orange for the middle strand that we colored earlier. Now, to follow the rules, either all three strands present in the central crossing must be orange, or two more must be present. If we try all orange we get

![Error loading image](images/tricolor-8.png)

and we see that the last strand also has to be orange, which means we failed to use at least two colors. Ok, lets try to have three different colors present at the central crossing. We then get

![Error loading image](images/tricolor-8-2.png)

where we see that if we must follow the second rule, the last strand must be all three colors at once. This is because it must be orange at its upper end, green at the blue-orange upper crossing, and blue at the bottom crossing. We are only allowed to color each strand once so we have actually proven that the figure-eight knot is not tricolorable.

There is something we have swept under the rug here so far, and that is showing that the Reidemeister moves doesn’t affect a knots tricolorability. If it did, then tricolorability wouldn’t be an invariant of the knot type, which is bad for showing two thing are the same or that two things are different.

Since these moves are performed “inside” a knot, we must require that the beginnings and ends of the drawn strands have the same color both before and after the move. This is to make sure that we are only looking at the actual move affecting tricolorablity, and not changing something else about the knot colorwise. For the type-1 Reidemeister move, notice that we can only use one color both before and after the move, i.e.

![Error loading image](images/tricolorable-1.png)

Hence, if a knot is tricolorable, performing a type-1 Reidemeister move will not change that fact. For the Type-2 Reidemeister move, we notice that after we perform the move, we must have two separate strands, which means we can either have two different colors, or only one color. If we let both have the same color we assume that there is some other color elsewhere in the knot, not being affected by the move. We can them color the system with all same color before doing the move, so that case is fine. If we chose the two different colors, we get

![Error loading image](images/tricolorable-2.png)

which shows that the tricolorability is preserved. For the type-3 Reidemeister move we can also choose the same color everywhere, in the same way as for the type-2 move. But, if we choose to tricolor the system using different colors, we get

![Error loading image](images/tricolorable-3.png)

which still preserves the tricolorability! We have shown that Reidemeister moves does not affect the tricolorability of a knot, and hence that tricolorability is a knot invariant. This means that any knot equivalent to the unknot or the figure-eight knot is not tricolorable. This means that we cant use this machinery to show that the figure-eight knot is not the unknot, as they both are not tricolorable. But, it also mean that all we have to do to prove that knots different from the unknot exist, is to prove that there exists knots that are tricolorable! And this we can prove by example. I wont go for the standard example of a tricolorable knot, and we will instead show that the so-called Granny knot, is tricolorable. The Granny knot is the following knot:

![Error loading image](images/granny.png)

And all we have to do to prove that it is tricolorable is to find a tricoloring. This is as easy as just picking a strand to color in some color and following the rules. I then got the following coloring of the Granny knot

![Error loading image](images/granny-tricolor.png)

which by inspection satisfies all the rules of a tricoloring of the knot. Hence, we have finally showed that there are knots! So the answer to the question in the title is yes.