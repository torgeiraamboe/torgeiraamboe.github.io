---
title: "Exotic algebraic models"
date: 2024-03-14
draft: false
katex: true
categories: ["Stable homotopy theory", "Chromatic homotopy theory"]
series: ["Adapted homology"]
tags: ["Spectra", "Homology", "Triangulated categories", "Algebraicity"]
cover:
    image: "images/chromatic_algebraic.png"
---

This blog-post is dedicated to this day, $\pi$-day (14th of march), where we celebrate $\pi_*$, the [stable homotopy groups]({{<ref "posts/2021/stable-homotopy">}}). 


As has been the case a couple of times already, when faced with an increased workload I tend to neglect writing on this blog. It is only natural that increased amounts of work in one section lead to a decreased amount of work in another — there is, after all, only a finite amount of time given to us. But, for the remainder of my PhD I will solely focus on research and outreach, hence I will hopefully have some more time to write and think. This post has been a long time coming and features the precise area of mathematics where I do most of my research, namely exotic algebraic models. I will throughout this post, and its sequels, explain what these are and connect it to almost all the previous blog posts I have made for the last couple of years. This will also set up some of the needed background for presenting my own research, which I will do once I am done writing the paper presenting it. 

Let’s start with some motivation for the problem at hand, and then dive into theory and constructions afterwards. The overarching goal of this blog-post is to justify the following claim:

>“Chromatic homotopy theory is algebraic at large primes”.



## Motivation

I have stated several times on this blog that my main mathematical interest, and thus also my research, is about finding and understanding connections between topology and algebra (I am also including geometry here). To paraphrase last year’s Abel prize winner, Dennis Sullivan, ‘mathematics consists of two seemingly distinct areas, the area of numbers and the area of shapes’. I, and also he, find the intersection of these areas to be where the most interesting mathematics happens. The kind of mathematics that hits me the hardest is the study of structure, symmetry, and connections. Mathematical structure is in my opinion best described using categories, or in the modern world, $\infty$-categories. 

So, given this information, we should perhaps expect to see that this blog post is about some connection or structural similarities between structure in topology and structure in algebra. The topological part will be some category of spectra and the algebraic part will be some derived category. A simple example we can use to get some feeling for what type of results we are after is the following. 

Let $R$ be a ring. This is in particular an algebraic object, and it has an associated derived category, $D(R)$, which naturally is a [stable $\infty$-category]({{<ref "posts/2022/stable-infinity-categories">}}). We have a construction that maps algebraic objects into topological ones, called the Eilenberg-MacLane construction. This takes a group $G$ and produces a spectrum $HG$. For a ring $R$ this produces a ring spectrum $HR$, which is a sort of homotopical version of $R.$ This construction turns out to not lose, or gain, any particularly important information, which gives us a symmetric monoidal equivalence of stable $\infty$-categories 

$$
Mod_{HR}\simeq D(R). 
$$

For example, if $R=\mathbb{Q}$, then $Mod_{H\mathbb{Q}} \simeq Sp_\mathbb{Q}$, the category of rational spectra. Hence, there is an equivalence of stable $\infty$-categories $Sp_\mathbb{Q}\simeq D(\mathbb{Q})$. This means essentially that the category of rational spectra is fully describable using only algebraic information. 

Our goal is then to see ‘how far’ we can generalize such an equivalence. The relevant questions are: does there exist another ring spectrum $S$ such that $Mod_S \simeq D(R)$ for some ring $R$? If not, is there perhaps a more complicated abelian category $\mathcal{A}$ such that $Mod_S\simeq D(\mathcal{A})?$ More generally, given some subcategory $\mathcal{C}\subseteq Sp$, does there exist an equivalence $\mathcal{C}\simeq D(\mathcal{A})?$ If yes, then $\mathcal{A}$ is called an algebraic model for $\mathcal{C}$. The above example then states that $Mod_R$ is an algebraic model for $Mod_{HR}.$

As it turns out, having an algebraic model is extremely rare. In fact, the above example is the only one — no other subcategory of spectra is equivalent to a derived category. Categories of spectra, that are not made to explicitly model algebra, are simply too complicated and have too much homotopical structure. 

<span style="color:orange" id=def-1> **Definition 1:** </span> 
Let $\mathcal{C}$ be an $\infty$-category. The homotopy category of $\mathcal{C}$, is the $1$-category $h\mathcal{C}$ obtained by $1$-truncating all the mapping spaces, i.e. letting 

$$
Hom_{h\mathcal{C}}(X,Y):= \pi_ 0Hom_ \mathcal{C}(X,Y).
$$

It is well known that if the $\infty$-category $\mathcal{C}$ is stable, then the homotopy category is triangulated. If the category $\mathcal{C}$ is a symmetric monoidal stable $\infty$-category, then the homotopy category is a [tensor-triangulated category]({{<ref "posts/2021/tensor-triangulated-categories">}}). 

For a stable $\infty$-category $\mathcal{C}$ we can then instead ask whether there is an equivalence of $1$-categories $h\mathcal{C} \simeq hD(\mathcal{A})$. This is a much weaker statement than asking for an equivalence of $\infty$-categories. If a category $\mathcal{C}$ has such an equivalence, that is not just the restriction of an equivalence of $\infty$-categories to the homotopy category, then we say $\mathcal{C}$ is exotically algebraic, with exotic algebraic model $\mathcal{A}$. 

## Examples and non-examples

We can again look at the case of modules over some ring spectrum, but now some spectrum that is not the Eilenberg-MacLane spectrum of a ring. One such fairly simple spectrum is $KU$, the spectrum representing complex topological $K$-theory. Via Bott periodicity it is a $2$-periodic spectrum, with homotopy groups $\Z[u^{\pm}]$, where $|u|$ is the Bott-class in degree $2$. 

There is an equivalence of $1$-categories $hMod_{KU}\simeq hD(\Z[u^\pm])$.

Since both $Mod_{KU}$ and $D(\Z[u^\pm])$ are stable we know that their homotopy categories are triangulated. A natural question arises: Is the above equivalence an equivalence of triangulated categories? As of right now, that question is still an open problem, but, there is a nice way to tell if such equivalences are triangulated. 

<span style="color:orange" id=def-2> **Definition 2:** </span> 
Let $\mathcal{C}$ be a stable $\infty$-category. The homotopy $2$-category, denoted $h_2\mathcal{C}$, is defined as the $2$-category with the same objects as $\mathcal{C}$, $1$-morphisms given by $\pi_0 Map(-,-)$ and $2$-morphisms given by $\pi_1Map(-,-)$. 

Another way to say this is that it is the $2$-category obtained by $3$-truncating the mapping spaces in $\mathcal{C}$. 

<span style="color:orange" id=prop-3> **Proposition 3:** </span> 
Let $\mathcal{C}$ and $\mathcal{D}$ be stable $\infty$-categories. If there is an equivalence $h_2\mathcal{C}\simeq h_2\mathcal{D}$, then the induced equivalence $h\mathcal{C}\simeq h\mathcal{D}$ is triangulated. 

The reason we don’t know whether the equivalence $hMod_{KU}\simeq hD(\Z[u^\pm])$ is triangulated, is precisely because we don’t know whether there is an equivalence $h_2 Mod_{KU}\simeq h_2 D(\Z[u^\pm])$. 

So what is an example of an equivalence that is triangulated? One example comes from an old friend of the blog, the [Johnson-Wilson spectrum]({{<ref "posts/2022/johnson-wilson-theory">}}). Recall that this is a ring spectrum $E(n)$ with coefficients $\pi_* E(n) = \Z_{(p)}[v_1, v_2, \ldots, v_{n-1}, v_{n}^{\pm}]$ that is complex oriented with associated [formal group law]({{<ref "posts/2021/formal-group-laws">}}) of height $n$. It is also implicitly dependent on a prime $p$. As for $KU$, the exotic algebraic equivalence comes from comparing $E(n)$ and $\pi_* E(n)$. Letting for example $p=3$ and $n=1$ we have an equivalence 

$$
h_2 Mod_{E(1)}\simeq h_2 D(\pi_*E(1)),
$$

meaning there is a triangulated equivalence $hMod_{E(1)}\simeq hD(\pi_* E(1))$. 

In fact, for choices of a bigger prime $p$ this equivalence gets “stronger”, in the sense that we actually loose less homotopical information. Instead of using the homotopy $2$-category we can use the more general homotopy $k$-category. 

<span style="color:orange" id=def-4> **Definition 4:** </span> 
Let $\mathcal{C}$ be a stable $\infty$-category. The homotopy $k$-category $h_k\mathcal{C}$ is obtained by $k+1$ truncating the mapping spaces of $\mathcal{C}$. 

In words this means that we “cut off” all homotopical information above dimension $k$. 

<span style="color:orange" id=lm-5> **Lemma 5:** </span> 
Let $p$ be a prime, $n$ a natural number, and $E=E(n)$ the associated Johnson—Wilson theory. If $2p-2>n$ then there is an equivalence of $(2p-2-n)$-categories

$$
h_{2p-2-n}Mod_{E(n)}\simeq h_{2p-2-n}D(\pi_*E(n)).
$$

Choosing a prime $p$ that is large compared to the chromatic height $n$ then makes this equivalence “better”. For a fixed height $n$ we can then choose a sufficiently large prime $p$ such that there is an equivalence as above. This fits in line with the claim that chromatic homotopy is algebraic at large primes. 

## Franke’s algebraicity theorem

In an earlier blogpost from last year we covered [adapted homology theories]({{<ref "posts/2023/adapted-homology">}}). These were essentially the homology theories one could obtain by sheafifying the [universal homology theory]({{<ref "posts/2023/universal-homology">}}) $y\colon \mathcal{C}\longrightarrow A(\mathcal{C})$, i.e. the Yoneda embedding into the Freyd envelope. More specifically, they are functors $H$ from a stable $\infty$-category to a locally graded abelian category with enough injectives, admitting certain lifts. 

In the previous post on [Hopf algebroids]({{<ref "posts/2023/hopf-algebroids">}}) we fixed the category $\mathcal{C}=Sp$ and constructed a class of adaped homology theories as follows: 

<span style="color:orange" id=prop-7> **Proposition 6:** </span> 
Let $R$ be a *nice*[^1] flat ring spectrum and $R_*=\pi_*(R\otimes -)$ its associated homology theory. Then 

$$
R_*\colon Sp\longrightarrow Comod_{R_*R}
$$

is an adapted homology theory. 

We will look closer at these examples later in the post, but let us first cover the general machinery that we will use: Franke’s algebraicity theorem. 

Essentially, the theorem states that a category $\mathcal{C}$, admitting a certain very nice adapted homology theory, is automatically exotically algebraic. The statement was conjectured and attempted proved in a specific setting in spectra by Jens Franke, but several years later a subtle mistake was found in the proof by Irakli Patchkoria. However, the general form of the theorem, which we now present, was proven by Patchkoria in joint work with Piotr Pstrągowski. 

<span style="color:orange" id=thm-7> **Theorem 7:** </span> 
Let $H\colon \mathcal{C}\longrightarrow \mathcal{A}$ be an adapted homology theory such that 

1. $H$ is conservative, 
2. $\mathcal{A}$ has a splitting of order $q$
3. $\mathcal{A}$ has cohomological dimension $d<q$.

Then there is an equivalence of $(q-d)$-categories 
$$h_{q-d}\mathcal{C}\simeq h_{q-d}D^{per}(\mathcal{A}),$$ 
where the latter denotes the periodic derived category of $\mathcal{A}$ (which we encountered in an [earlier blog post]({{<ref "posts/2022/periodic-torsion#the-periodic-derived-category">}})).

This is a very nice and general theorem. It allows us to take a proposed example, check a small well-defined list of criteria, and conclude with nice algebraicity statements. One of my own research results, which will be presented hopefully on this blog soon, is precisely proving that a certain homology theory satisfied the above criteria. 

Now, if I recall correctly, we have not seen any of the three above criteria on this blog before, so let’s go through them one by one. 

### Conservativity

The first condition, conservativity, is a condition on $H$ being able to detect isomorphisms in $\mathcal{C}$. In some sense, it is not allowed to ‘create’ any new isomorphisms out of non-isomorphisms. This can be defined precisely as follows. 

<span style="color:orange" id=def-8> **Definition 8:** </span> 
A functor $F\colon \mathcal{C}\longrightarrow \mathcal{D}$ is conservative if it reflects isomorphisms. In other words, given a map $f\colon X\longrightarrow Y$ in $\mathcal{C}$, then $F(f)$ is an isomorphism if and only if $f$ is an isomorphism. 

A nice example is the homotopy groups functor $\pi_*\colon Mod_R\longrightarrow Mod_{R_*}$ for a homotopy commutative ring spectrum $R$. By the examples presented earlier, this is perhaps to be expected. This is also a general phenomena in stable homotopy theory, where equivalences of spectra can be checked on homotopy groups. 

Let’s consider our favorite example $R_*\colon Sp\longrightarrow Comod_{R_*R}$. Is this conservative? No. Notice that the functor $R_*$ is a composition of two functors: 

$$
Sp\overset{R\otimes(-)}\longrightarrow Mod_R\overset{\pi_*}\longrightarrow Comod_{R_*R}
$$

We just explained that the latter functor $\pi_*$ is conservative, but the former, $R\otimes(-)$ is not. Thinking back to [Bousfield localizations]({{<ref "posts/2021/bousfield-localization">}}), we defined $R_*$-equivalences to be those maps $f\colon X\longrightarrow Y$ such that $R_*f$ was an equivalence. Since $\pi_*$ is conservative, also $R\otimes f$ is an equivalence.  But, we have also seen that Bousfield localization is not just the identity functor, so the class of $R$-equivalences cannot just be the $\pi_*$-equivalences, otherwise there would be no non-trivial Bousfield localization. 

A fix for this is then to precisely use just the $R$-equivalences, i.e. passing from $Sp$ to $Sp_R$. The induced functor $R_*\colon Sp_R\longrightarrow Comod_{R_*R}$ is then a conservative adapted homology theory! When we talk about $R$-homology for the rest of this post, this is the functor we mean. 

### Splitting

The splitting condition is a technical condition that makes sure the functor $H,$ restricted to injective objects, has a partial inverse. The only thing the theorem needs to work is this partial inverse, but as there is currently no other known way of constructing it, using the splitting condition is usually the preferred way of stating the theorem. 

<span style="color:orange" id=def-9> **Definition 9:** </span> 
Let $\mathcal{A}$ be an abelian category with a local grading $[1]$. A splitting of order $q$, is a collection of $q$ Serre subcategories $\mathcal{A}_\phi \subseteq \mathcal{A}$, where $\phi \in \Z/q$, such that 

1. $\coprod_{\phi\in \Z/q} \mathcal{A}_\phi \simeq \mathcal{A}$, i.e. the subcategories form a decomposition of $\mathcal{A}$, and
2. $[k]\mathcal{A}_ \phi\subseteq \mathcal{A}_{\phi+k \text{ mod } q}$. 

The objects in $\mathcal{A}_\phi$ are said to be of pure weight $\phi$.  

A condition of this type was first described by Franke, but it looked a bit different. Let us see this ‘original’ splitting. 

Let $p$ be an odd prime and $Ab_{(p)}$ the category of $p$-local abelian groups. This is the category of modules over the $p$-local integers, which are obtained from $\Z$ by inverting every prime except $p$. For any $M\in Mod_{\Z_{(p)}}$, there is a rational eigenspace decomposition 

$$
M\otimes \mathbb{Q} \cong \bigoplus_{j\in \Z}W_{j(p-1)}.
$$

We have a set of operations $\psi^k$ for $k\in \Z_{(p)}^\times$, called Adams operations, that act on $M$ via this decomposition in the following manner: For any $w\in W_{j(p-1)}$ we have

$$
(\psi^k\otimes Id_\mathbb{Q})(w) = k^{j(p-1)}w.
$$

We let $Ad_{(p)}$ be the category of $p$-local abelian groups together with these Adams operations. There is an auto-equivalence $T\colon Ad_{(p)}\longrightarrow Ad_{(p)}$ that sends a module $M$ to itself, but the Adams operation $\psi^k$ now acts on $TM$ as $k^{p-1}\psi^k$. 

Now we can define a category $\mathcal{A}$, consisting of collections of objects $(M_n)_ {n\in \Z}$ where $M_n\in Ad_{(p)}$ together with a specified isomorphism $T(M_n)\overset{\cong}{\longrightarrow} (M_{n+2p-2})$ for each $n$. This category is isomorphic to the sum of $2p-2$ shifted copies of $Ad_{(p)}$, which we can recognize as a full subcategory of objects $(M_n)$ such that $M_n \cong 0$ whenever $n \neq 0\mod 2p-2$. 

This precicely means that we can recognize the copies of $Ad_{(p)}$ as the pure weight $\phi$ components of a splitting of $\mathcal{A}$. In fact, there is an equivalence of categories 
$$
\mathcal{A}\simeq Comod_{E(1)_*E(1)},
$$ 
where $E(1)$ is the height $1$ [Johnson-Wilson spectrum]({{<ref "posts/2022/johnson-wilson-theory">}})! This shows that the category $Comod_{E(1)_*E(1)}$ has a splitting of order $2p-2$. 

A natural question is then, can we generalize this construction to other ring spectra? In other words, is there a sufficient condition we can place upon a ring spectrum $R$ such that the category $Comod_{R_*R}$ has a splitting of order $q$? 

The answer turns out to be yes, and it should not be that hard to convince ourselves of this. The ring spectrum $E(1)$ from the example above has homotopy groups $\pi_*E(1) \cong \Z_{(p)}[v_1^{\pm}]$ with $|v_1|=2p-2$. In other words, it is a graded ring concentrated in degrees divisible by $2p-2$. This condition allowed us to take the module category over the copy of $\Z_{(p)}$ that exists in the degree $2j(p-1)$ and construct a splitting based on these. They are precisely sewn together as a coherent whole by the shift operation $T$. The added Adams operations, which the shift $T$ acted on essentially by degree shifting, is what gives the modules the extra structure of comodules. 

We can then hope that whenever we have a nice ring spectrum $R$, such that $\pi_*R$ is concentrated in degrees divisible by $q$, that we get a similar splitting of order $q$ on $Comod_{R_*R}$. This is precisely the case. 

<span style="color:orange" id=lm-10> **Lemma 10:** </span> 
Let $R$ be a nice ring spectrum such that $\pi_*R$ is concentrated in degrees divisible by $q$ as a graded ring. Let further $\phi \in \Z/q$ and denote by $Comod_{R_*R}^\phi$ the full subcategory spanned by the graded comodules $M_*$ such that $M_n = 0$ unless $n\equiv 0\mod q$. The collection of subcategories defined by this constitutes a splitting of order $q$ of $Comod_{R_*R}$. 

Note that this also works for the category of modules over $R$, not just comodules! This will be used later. 

This means in particular that if $R$ is a nice ring spectrum such that $\pi_*R$ is concentrated in degrees divisible by $q$, then the functor 

$$
R_*\colon Sp_R\longrightarrow Comod_{R_*R}
$$

is a conservative adapted homology theory, where $Comod_{R_*R}$ has a splitting of order $q$. This looks very promising for our favorite example. 

### Cohomological dimension

There are several types of “dimensions” throughout mathematics. In algebra there is usually no very geometric definition one could make, corresponding with some sort of visual intuition. For vector spaces, this is ok, as it corresponds roughly with intuition, but what should the dimension of $\Z[x]$ be? What about $\mathbb{F}_p$, or some abelian group $G?$ There are several ways of answering these questions, all depending on what type of structure one is interested in studying. For us, the dimension will be a certain “resolution dimension”, or the longest chain of certain objects one can create starting from another. For categories of modules over a ring this is relatively straightforward. 

Let $R$ be a commutative ring and $M$ an $R$-module. The projective dimension of $M,$ denoted $p.dim(M),$ is defined as the minimal length of a finite projective resolution of $M$. If no such number exists, then we say $p.dim(M)=\infty.$

<span style="color:orange" id=def-11> **Definition 11:** </span> 
Let $R$ be a commutative ring. The global dimension of $R$ is defined as 

$$
gl.dim(R) = \sup\\{p.\dim(M)\mid M\in Mod_R\\}.
$$

The global dimension measures in a way the complexity of the representation theory of $R$. Having a finite global dimension is then a way of saying that the complexity is “manageable”. 

There is another way of approximating the projective dimension of an $R$-module, which is done using $Ext$-groups. Recall that these are the derived functors of the $Hom$-functor. 

<span style="color:orange" id=lm-12> **Lemma 12:** </span> 
Let $R$ be a commutative ring and $M$ an $R$-module. Then $Ext^n_R(M,N)=0$ for all $R$-modules, if and only if $p.dim(M)<n.$

This gives rise to another definition of a dimension for the whole category of $R$-modules, which lends itself to a better generalization. 

<span style="color:orange" id=def-13> **Definition 13:** </span> 
Let $R$ be a commutative ring. The cohomological dimension of $R$, denoted $c.dim(R)$, is defined to be the minimal integer $d$ such that all $Ext$-groups vanish above $d$, i.e., $Ext_R^n(M,N)=0$ for all $n>d$ and $M,N\in Mod_R.$ 

These two notions of dimensions do in fact coincide. 

<span style="color:orange" id=lm-14> **Lemma 14:** </span> 
Let $R$ be a commutative ring. Then $c.dim(R)=gl.dim(R)$. 

The construction of $Ext$-groups uses injective resolutions, which for us works much better than projective ones. This is because being an adapted homology theory assumed from the start that we had enough injectives, which means in particular that we can construct injective resolutions and thus also $Ext$-groups. Hence, for any abelian category $\mathcal{A}$ admitting an adapted homology theory $H\colon \mathcal{C}\longrightarrow \mathcal{A}$, we can talk about the cohomological dimension of $\mathcal{A}$. This might be either finite or $\infty$. We repeat the definition of cohomological dimension again in the general case, just to be precice. Note that for adapted homology theories we have an internal grading $[1]\colon \mathcal{A}\to \mathcal{A}$, hence our $Ext$-groups are in fact bigraded. 

<span style="color:orange" id=def-15> **Definition 15:** </span> 
Let $\mathcal{A}$ be a locally graded abelian category with enough injectives. The cohomological dimension of $\mathcal{A}$, denoted $c.dim(\mathcal{A})$, is defined to be the minimal integer $d$ such that $Ext_\mathcal{A}^{s,t}(A,B)=0$ for all $s>d$ and $A, B\in \mathcal{A}.$

So, what are some examples of this? Let us return to the first example we saw, namely $\pi_*KU \cong \Z[u^\pm]$, where $u$ is the degree $2$ Bott-class. The global dimension of $\Z$ is $1$, and adding a generator increases the dimension by $1$. By inverting that generator, the dimension is again reduced by $1$, hence $c.dim(\Z[u^\pm])=1$. In summary for the category of modules we have the following. 

<span style="color:orange" id=lm-16> **Lemma 16:** </span> 
The cohomological dimension of the category $Mod_{\pi_*KU}$ is $1$. 

We also say the Johnson—Wilson spectrum $E(n)$, especially at height $1$. The ring $\Z_{(p)}$ is a regular Noetherian local ring, with global dimension $1$. By adding $n$ generators, and then inverting one of them to get $\pi_*E(n)=\Z_{(p)}[v_1, \ldots, v_{n-1}, v_n^\pm]$ we get the following. 

<span style="color:orange" id=lm-17> **Lemma 17:** </span>
The cohomological dimension of the category $Mod_{\pi_*E(n)}$ is $n$. 

## Franke algebraicity for certain spectra

We can summarize the above discussion for our favorite example by the following version of Franke’s algebraicity theorem for localized categories of spectra and for module categories over ring spectra. We start with the latter. 

<span style="color:orange" id=thm-19> **Theorem 19:** </span>
Let $R$ be a ring spectrum such that 

1. $\pi_*R$ is concentrated in degrees divisible by $q$, and 
2. $Mod_{\pi_*R}$ has finite cohomological dimension $d<q$.

Then the conservative adapted homology theory $\pi_*\colon Mod_R\longrightarrow Mod_{\pi_*R}$ induces an equivalence $h_{q-d}Mod_R\simeq h_{q-d}D(\pi_*R)$. 

Notice that we have used a slightly different statement than the direct implication from Franke’s algebraicity theorem. Instead of phrasing the result via $D^{per}(Mod_{R_*})$ on can instead note that whenever Franke’s algebraicity theorem applies for $R$ is also applies for $HR_*$. Hence we can splice together three equivalences, and get 
$$h_{q-d}D^{per}(\pi_*R)\simeq h_{q-d}Mod_{H\pi_*R}\simeq h_{q-d}D(\pi_*R).$$

Let us see some examples of this theorem. We can now prove our first claim: the algebraicity for $KU$-modules. 

<span style="color:orange" id=cor-20> **Corollary 20:** </span> 
Let $KU$ be the complex topological $K$-theory spectrum. Then $hMod_{KU}\simeq hD(\Z[u^\pm])$.

*Proof.* By [Lemma 10](#lm-10) the category $Mod_{\pi_*KU}$ has a splitting of order $2$, as $\pi_*KU\cong \Z[u^\pm]$, which is a graded ring concentrated in degrees divisible by $2$, due to the Bott-class $u$ having degree $2$. By [Lemma 16](#lm-16) the cohomological dimension of $Mod_{\pi_*KU}$ is $1$. Since $1<2$ we have by [Theorem 19](#thm-19) an equivalence $h_1Mod_{KU}\simeq h_1D(\pi_*KU)$. Taking $h_1$ is the same as taking the homotopy category $h$, hence we are done. 

<span style="color:orange" id=cor-21> **Corollary 21:** </span> 
Let $E(n)$ be the height $n$ Johnson—Wilson spectrum at a prime $p$. If $2p-2>n$ then there is an equivalence $h_{2p-2-n}Mod_{E(n)}\simeq h_{2p-2-n}D(\pi_*E(n))$. 

*Proof.* By [Lemma 17](#lm-17) the cohomological dimension is $n$, and by [Lemma 10]($lm-10) there is a splitting of order $2p-2$. By [Theorem 19](#thm-19) we obtain the wanted equivalence. 

This again exemplifies the overarching claim that chromatic homotopy theory is algebraic at large primes. But, so far we have only seen that this claim holds for modules, not for the bigger more complicated category $Sp_n$ of all $E(n)$-local spectra. We now turn to this example. To do that we present a version of [Theorem 19](#thm-19) in the more specific case of $R$-homology functors. 

<span style="color:orange" id=thm-22> **Theorem 22:** </span> 
Let $R$ be a nice flat ring spectrum such that

1. $Comod_{R_*R}$ has finite cohomological dimension $d$, and
2. $\pi_*R$ is concentrated in degrees divisible by $q>d$. 

Then the conservative adapted homology theory $R_*\colon Sp_R\longrightarrow Comod_{R_*R}$ induces an equivalence 
$$h_{q-d}Sp_R\simeq h_{q-d}D^{per}(Comod_{R_*R}).$$

There are, unfortunately, not that many ring spectra $R$ where we know precisely the cohomological dimension $d$ of $Comod_{R_*R}$. These categories are rather complicated, and in the examples we know, many have infinite cohomological dimension, hence the results don’t apply. This is the case for example for $R=MU$ or $R=\mathbb{F}_p$. 

But, one ring spectrum that we have fairly good control over is $E(n)$. And it turns out that this has a nice finite cohomological dimension that is purely dependent on the height $n$! This was proven by Pstrągowski. 

<span style="color:orange" id=lm-23> **Lemma 23:**</span>  
Let $E=E(n)$ be height $n$ [Johnson-Wilson theory]({{<ref "posts/2022/johnson-wilson-theory">}}) at a prime $p$ such that $p+1>n$. Then the category $Comod_{E_*E}$ has finite cohomological dimension $n^2+n$. 

Notice that the dimension for the category of modules was simply $n$, which means that the category of comodules is substantially more cohomologically complex than the module category. But, it is still just a finite number, hence quite manageable!

We learned earlier that $E(1)$  was a nice ring spectrum concentrated in degrees divisible by $2p-2$. So, choosing a large prime makes sure that the degree of the splitting is larger than the cohomological dimension. In the particular case $n=1,$ we now know that the cohomological dimension is $2$. Choosing $p>2$, in other words any odd prime, then means that $q>d$. In particular, all the criteria for applying [Theorem 22](#thm-22) are satisfied! This was originally proved without this general machinery by Bousfield, so this approach unifies his result with a more general phenomenon. 

<span style="color:orange" id=thm-24> **Theorem 24:** </span> 
Let $p$ be an odd prime. Then there is an equivalence of categories $hSp_{1,p} \simeq hFr_{1,p}.$

Here $Fr_{n,p}$ denotes the “Franke category” which is an alternative name for the periodic derived category, $D^{per}(Comod_{E(n)_*E(n)}).$ 

The ring spectrum $E(n)$ is concentrated in degrees divisible by $2p-2$ not only in the case $n=1$, but for all $n$. Hence we can make a similar more general algebraicity statement by again choosing big enough primes. 

<span style="color:orange" id=thm-25> **Theorem 25:** </span> 
Let $p$ be a prime and $n$ a natural number. If $2p-2>n^2+n$, then there is an equivalence of categories
$$
h_{2p-2-n^2-n}Sp_{n,p}\simeq h_{2p-2-n^2-n}Fr_{n,p}.
$$

*Proof.* The graded ring $E(n)_ *$ is concentrated in degrees divisible by $2p-2$, hence the category $Comod_{E(n)_*E(n)}$ has a splitting of the same order by [Lemma 10](#lm-10). By [Lemma 23](#lm-23) the category $Comod_{E(n)_*E(n)}$ has cohomological dimension $n^2+n$. This means that we get our wanted equivalence from [Theorem 22](#thm-22). 

This is one of the reasons that chromatic homotopy theory simplifies drastically at large primes compared to the height. Our overarching claim, that chromatic homotopy theory (the study of $Sp_{n,p}$) is asymptotically algebraic, or algebraic at large primes, is now sufficiently justified! 

## Outro

This story is a nice contained version of the claim that chromatic homotopy theory is algebraic at large primes, but there is also another category that shows up all over the place in chromatic homotopy theory, namely the category of $K(n)$-local spectra $Sp_{K(n)}$. To properly justify the claim that things et more algebraic at large primes, one should also have a similar proof for this category. Unfortunately, there are some issues by doing this directly. My research over the last couple years has focused exactly on proving this fact, that $K(n)$-local stable homotopy theory is algebraic at large primes. The paper, called “Algebraicity in monochromatic homotopy theory” was put on the ArXiv yesterday, and I will try to make a blog-post about it soon. For now the interested reader can find it [on ArXiv](https://arxiv.org/abs/2403.07725). 

[^1]: Nice here means Adams type. A technical condition that forces some nice properties on the functor, like the associated Hopf algebroid being a Grothendieck abelian category.


<style>body {text-align: justify}</style>