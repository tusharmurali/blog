---
layout: post
title: "An Introduction to Category Theory"
tags: mathematics
ordered_toc: true
author:
  - Tushar Muralidharan
---

> "Category theory is the mathematics of mathematics... Whatever mathematics does for the world, category theory does for mathematics." - Eugenia Cheng

Category theory aims to unify mathematics by studying mathematical structures and their relationships. Its objects of study are mathematical structures themselves, and many traditional mathematical concepts can be reformulated in category-theoretic language, offering deeper insights.

## Categories

### What is a Category?

**Definition.** (Category) A **category** $\mathcal{C}$ consists of
- a collection[^collection] $\|\mathcal{C}\|$ of **objects**
- for every pair of objects $X,Y \in \|\mathcal{C}\|$, a collection $\mathcal{C}(X,Y)$ of **morphisms**[^morphisms] from[^domain] $X$ to $Y$
- for every object $X \in \|\mathcal{C}\|$, an **identity morphism** $1_X \in \mathcal{C}(X,X)$ on $X$, written $\begin{CD}
X @\>{1_X}\>\> X
\end{CD}$
- for every $\begin{CD}
X @\>{f}\>\> Y @\>{g}\>\> Z
\end{CD}$, a **composite morphism**[^composition] $\begin{CD}
X @\>{g \circ f}\>\> Z
\end{CD}$

that satisfy 
- $1_Y \circ f = f = f \circ 1_X$ for every $\begin{CD}
X @\>{f}\>\> Y
\end{CD}$ (**identity laws**)
- $h \circ (g \circ f) = (h \circ g) \circ f$ for every $\begin{CD}
X @\>{f}\>\> Y @\>{g}\>\> Z @\>{h}\>\> W
\end{CD}$ (**associative law**)

**Definition.** (Small) A category $\mathcal{C}$ is called **locally small** if for every $X,Y \in \|\mathcal{C}\|$, $\mathcal{C}(X,Y)$ is a set. If $\|\mathcal{C}\|$ is also set, then $\mathcal{C}$ is called **small**.

**Examples**
- $\mathsf{Set}$: the category of sets (and functions)
  - $\|\mathsf{Set}\| :=$ the collection[^russell] of all sets
  - $\mathsf{Set}(X,Y) :=$ the *set* of all functions from $X$ to $Y$
  - $1_X :=$ the identity function $X \to X$ defined by $x \mapsto x$
  - Given $\begin{CD}
X @\>{f}\>\> Y @\>{g}\>\> Z
\end{CD}$, define $\begin{CD}
X @\>{g \circ f}\>\> Z
\end{CD}$ by $x \mapsto g(f(x))$.
  - $\mathsf{Set}$ is locally small but not small.
- $\mathsf{Top}$: the category of topological spaces (and continuous maps)
  - $\|\mathsf{Top}\| :=$ the collection of all topological spaces
  - $\mathsf{Top}(S,T) :=$ the set of all continuous functions from $S$ to $T$
  - $\mathsf{Top}$ is locally small but not small.
- $\mathsf{Grp}$: the category of groups (and homomorphisms)
  - $\mathsf{Grp}$ is locally small but not small.
- $\mathsf{Vect}_K$: the category of vector spaces over a field $K$ (and linear transformations)
  - $\mathsf{Vect}_K$ is locally small but not small.
- $\mathsf{Rel}$: the category of (sets and) relations
  - $\|\mathsf{Rel}\| :=$ the collection of all sets
  - $\mathsf{Rel}(X,Y) :=$ the set of all relations between $X$ and $Y$, described by functions $X \times Y \to \\{\text{True},\text{False}\\}.$
  - $1_X :=$ the graph of the identity function on $X$, i.e. $\\{(x,x) : x \in X\\}$
  - Given $\begin{CD}
X @\>{R}\>\> Y @\>{S}\>\> Z
\end{CD}$, define $\begin{CD}
X @\>{R;S}\>\> Z
\end{CD}$ by $x(R;S)z \iff xRy \land ySz$ for some $y$.
  - $\mathsf{Rel}$ is locally small but not small.
- $\mathsf{G}$: the group $(G, \cdot, e)$ as a category
  - $\|\mathsf{G}\| := \\{\ast\\}$
  - $\mathsf{G}(\ast, \ast) := G$
  - $1_\ast := e$
  - Given $\begin{CD}
\ast @\>{g}\>\> \ast @\>{h}\>\> \ast
\end{CD}$, define $\begin{CD}
\ast @\>{h \circ g}\>\> \ast
\end{CD}$ by $h \circ g = h \cdot g$.
  - $\mathsf{G}$ is small.
- $\mathsf{M}$: the monoid $(M, \cdot, e)$ as a category[^categorification]
  - $\mathsf{M}$ is small.
- $\mathsf{P}$: the poset $(P, \leq)$ as a category
  - $\|\mathsf{P}\| := P$
  - $\mathsf{P}(x,y) :=$ a unique element labeled ' $x \leq y$ ' if $x \leq y$, otherwise the empty set.
- $\mathsf{P}$: the preorder $(P, \leq)$ as a category[^posetcategorifications]

### Isomorphisms and Monomorphisms

Morphisms from an object to itself are called **endomorphisms**. Additionally, we can define the following types of morphisms directly from the definition of a category. 

**Definition.** Let $\begin{CD}
X @\>{f}\>\> Y
\end{CD}$ be a morphism. 

$f$ is an **isomorphism** if there exists $\begin{CD}
Y @\>{f^{-1}}\>\> X
\end{CD}$ such that $f^{-1} \circ f = 1_X$ and $f \circ f^{-1} = 1_Y$. 

$f$ is a **monomorphism** if for all $\begin{CD}
Z @\>{x}\>{y}\> X
\end{CD}$, if $f \circ x = f \circ y$, then $x = y$.


**Theorem**. If $f$ is an isomorphism, then $f^{-1}$ is unique.

*Proof.* Suppose that $\begin{CD}
X @\>{f}\>\> Y
\end{CD}$ has two inverses $\begin{CD}
Y @\>{f_1^{-1}}\>{f_2^{-1}}\> X
\end{CD}$. Then 
\\[f_1^{-1} = f_1^{-1} \circ 1_Y = f_1^{-1} \circ (f \circ f_2^{-1}) = (f_1^{-1} \circ f) \circ f_2^{-1} = 1_X \circ f_2^{-1} = f_2^{-1}.\\]
<div style="text-align: right; margin-top: -20px">&#x25A1;</div>

**Theorem**. Every isomorphism is a monomorphism.

*Proof.* Suppose that $\begin{CD}
X @\>{f}\>\> Y
\end{CD}$ is an isomorphism, and take $\begin{CD}
Z @\>{x}\>{y}\> X
\end{CD}$ such that $f \circ x = f \circ y$. Then 
\\[x = 1_X \circ x = (f^{-1} \circ f) \circ x = f^{-1} \circ (f \circ x) = f^{-1} \circ (f \circ y) = (f^{-1} \circ f) \circ y = 1_X \circ y = y.\\]
<div style="text-align: right; margin-top: -20px">&#x25A1;</div>

**Examples**
\\[\begin{array}{c|c|c}\text{Category} & \text{Isomorphisms} & \text{Monomorphisms} \\\\ \hline\mathsf{Set} & \text{Bijections} & \text{Injections} \\\\ \mathsf{Top} & \text{Homeomorphisms} & \text{Injective continuous functions} \\\\ \mathsf{Grp} & \text{Group isomorphisms} & \text{Injective homomorphisms} \\\\ \mathsf{Vect}_K & \text{Linear isomorphisms} & \text{Injective linear transformations} \\\\ \mathsf{G} \text{ (a group)} & \text{All maps} & \text{All maps} \\\\ \mathsf{P} \text{ (a poset)} & \text{Identities} & \text{All maps}
\end{array}\\]

## Functors

### What is a Functor?

**Definition.** (Functor) Let $\mathcal{C}$ and $\mathcal{D}$ be categories. A **functor** $F \colon \mathcal{C} \to \mathcal{D}$ is given by
- a function $F_{0} \colon \|\mathcal{C}\| \to \|\mathcal{D}\|$
- for every pair of objects $X, Y \in \|\mathcal{C}\|$, a function $F_{1,\color{gray}{X,Y}} \colon \mathcal{C}(X,Y) \to \mathcal{D}(F_0X,F_0Y)$

that satisfies
- $F_1(1\_X) = 1_{F_0 X}$ for every object $X \in \|\mathcal{C}\|$
- $F_{1,\color{gray}{X,Z}}(g \circ f) = F_{1,\color{gray}{Y,Z}}(g) \circ F_{1,\color{gray}{X,Y}}(f)$ for every $\begin{CD}
X @\>{f}\>\> Y @\>{g}\>\> Z @\>{h}\>\> W
\end{CD}$

**Examples**
- $U \colon \mathsf{Grp} \to \mathsf{Set}$: the forgetful functor
  - $U(G,m,e) = G$
  - $U\left(\begin{CD}
(G,m,e) @\>{f}\>\> (G',m',e')
\end{CD}\right) = \begin{CD}
G @\>{f}\>\> G'
\end{CD}$
- $U \colon \mathsf{Top} \to \mathsf{Set}$: the forgetful functor
- $U \colon \mathsf{Vect}_K \to \mathsf{Set}$: the forgetful functor
- Functors $\mathsf{G} \to \mathsf{H}$ are just homomorphisms
- Functors $\mathsf{P} \to \mathsf{Q}$ are just monotone (order-preserving) maps

For any category $\mathcal{C}$, there exists an identity functor $\mathcal{C} \to \mathcal{C}$. Moreover, given functors $\begin{CD}
\mathcal{C} @\>{F}\>\> \mathcal{D} @\>{G}\>\> \mathcal{E}
\end{CD}$, there is an obvious composite functor $\begin{CD}
\mathcal{C} @\>{G \circ F}\>\> \mathcal{E}
\end{CD}$. This composition obeys the identity laws and associative laws. Therefore, we may define $\mathsf{Cat}$: the category of *small*[^problems] categories (and functors). $\mathsf{Cat}$ is locally small but not small.

### The Opposite Category

**Definition.** (Opposite Category) For any category $\mathcal{C}$, define its **opposite** (or **dual**) **category** $\mathcal{C}^{\mathrm{op}}$ by 
- $\|\mathcal{C}^{\mathrm{op}}\| := \|\mathcal{C}\|$
- $\mathcal{C}^{\mathrm{op}}(X,Y) := \mathcal{C}(Y,X)$
- $\left(\begin{CD}
X @\>{1\_X}\>\>\_{\mathcal{C}^{\mathrm{op}}}\; X\end{CD}\right) := \left(\begin{CD}
X @\>{1\_X}\>\>\_{\mathcal{C}}\; X\end{CD}\right)$
- given $\begin{CD}
X @\>{f}\>\> Y @\>{g}\>\> Z
\end{CD}$, define $g \circ_{\color{gray}{\mathcal{C}^{\mathrm{op}}}} f := f \circ_{\color{gray}{\mathcal{C}}} g$.

For example, $\mathsf{G}^{\mathrm{op}}$ is called the *opposite group*, and $\mathsf{P}^{\mathrm{op}}$ is called the *dual order*. Note that $(\mathcal{C}^{\mathrm{op}})^{\mathrm{op}} = \mathcal{C}$. Moreover, functors $\mathcal{C} \to \mathcal{D}$ are in one-to-one correspondence with functors $\mathcal{C}^{\mathrm{op}} \to \mathcal{D}^{\mathrm{op}}$.

**Definition.** (Contravariant and Covariant Functors) A functor $\mathcal{C}^{\mathrm{op}} \to \mathcal{D}$ is called a **contravariant functor** from $\mathcal{C}$ to $\mathcal{D}$. In contrast, an ordinary functor $\mathcal{C} \to \mathcal{D}$ is called a **covariant functor** from $\mathcal{C}$ to $\mathcal{D}$.

**Example.** (Dual Vector Space) The dual of a vector space $V$ over a field $K$ is defined by $V^* = \\{f \colon V \to K : f \text{ linear}\\}$. We claim that this is contravariant functorial, i.e., $V \mapsto V^*$ is the object action of a functor $\mathsf{Vec}^{\mathrm{op}} \to \mathsf{Vec}$. We define the morphism action by 

<div>
$$\begin{CD}
V \\
@V{l}VV \\
W
\end{CD} \quad\longmapsto\quad \begin{CD}
V^* \\
@VV{(f \mapsto f \circ l)}V \\
W^*
\end{CD}$$
</div>
One verifies that this is functorial, i.e., respects identities and composition.

**<a name="image-inverseimage"></a>Example.** There is a covariant functor from $\mathsf{Set}$ to $\mathsf{Set}$ whose action on objects is $X \mapsto \mathcal{P}X$ and whose action on morphisms $\begin{CD}
X @\>{f}\>\> Y\end{CD}$ is the *image* $\begin{CD}
\mathcal{P}X @\>{f}\>\> \mathcal{P}Y\end{CD}$. Indeed, we have $F(1_X)(A) = 1_X(A) = A$ and \\[F(g \circ f)(A) = (g \circ f)(A) = g(f(A)) = g(F(f)(A)) = F(g)(F(f)(A)).\\]

Similarly, there is a contravariant functor from $\mathsf{Set}$ to $\mathsf{Set}$ whose action on objects is also $X \mapsto \mathcal{P}X$ and whose action on morphisms $\begin{CD}
X @\>{f}\>\> Y\end{CD}$ is the *inverse image* $\begin{CD}
\mathcal{P}Y @\>{f^{-1}}\>\> \mathcal{P}X\end{CD}$.

### The Product Category

**Definition.** (Product Category) The **product category** $\mathcal{C} \times \mathcal{D}$ of categories $\mathcal{C}$ and $\mathcal{D}$ is given by
- $\|\mathcal{C} \times \mathcal{D}\| := \|\mathcal{C}\| \times \|\mathcal{D}\|$
- $(\mathcal{C} \times \mathcal{D})((X,Y),(X',Y')) := \mathcal{C}(X,X') \times \mathcal{D}(Y,Y')$
- $1_{(X,Y)} = (1_X, 1_Y)$
- $((f,g) \circ (f',g')) := (f \circ f', g \circ g')$

There are projection functors $\pi_1 \colon \mathcal{C} \times \mathcal{D} \to \mathcal{C}$ and $\pi_2 \colon \mathcal{C} \times \mathcal{D} \to \mathcal{D}$. The above definition generalizes to finite products $\mathcal{C}_1 \times \cdots \times \mathcal{C}_n$ of categories, and arbitrary products $\prod\_{i \in I} \mathcal{C}_i$. A multi-argument functor is a functor $\mathcal{C}_1 \times \cdots \times \mathcal{C}_n \to \mathcal{D}$.

**Definition.** (Hom Functor) The **hom functor** $\mathcal{C}(-,-)$ for a *locally small* category $\mathcal{C}$ is the functor $\mathcal{C}^{\mathrm{op}} \times \mathcal{C} \to \mathsf{Set}$ defined by $(X,Y) \mapsto \mathcal{C}(X,Y)$ and 

<div>
$$\begin{CD}
X \\
@A{g}AA \\
X'
\end{CD} \; \begin{CD}
Y \\
@VV{h}V \\
Y'
\end{CD} \quad\longmapsto\quad \begin{CD}
\mathcal{C}(X,Y) \\
@VV{(f \mapsto h \circ f \circ g)}V \\
\mathcal{C}(X',Y')
\end{CD}$$
</div>
This is verified to be functorial, and it is contravariant in its first argument and covariant in its second argument.

### Duality and Epimorphisms

**Definition.** A morphism $\begin{CD}
X @\>{f}\>\> Y\end{CD}$ in $\mathcal{C}$ is an **epimorphism** (epi.) if it is a monomorphism in $\mathcal{C}^{\mathrm{op}}$.

Unraveling the definition, a morphism $\begin{CD}
X @\>{f}\>\> Y\end{CD}$ in $\mathcal{C}$ is an epimorphism if for all $\begin{CD}
Y @\>{g}\>{h}\> Z
\end{CD}$, if $g \circ f = h \circ f$, then $g = h$. For example, in $\mathsf{Set}$, the epimorphisms are surjections.

## Natural Transformations
Recall that for any finite-dimensional vector space $V$, there is an isomorphism $V \cong V^*$ whose definition involves arbitrarily choosing a basis for $V$. However, we have an isomorphism $V \cong V^{**}$ without making an arbitrary choice.

**Definition.** Given functors $F,G \colon \mathcal{C} \to \mathcal{D}$, a **natural transformation** $\alpha \colon F \Rightarrow G$ is given by a family $(\begin{CD}
FX @\>{\alpha_X}\>\> GX\end{CD})_{X \in \|\mathcal{C}\|}$ of **components** (maps in $\mathcal{D}$) indexed by objects in $\mathcal{C}$, that satisfies the **naturality condition**: 
- for all 
  $\begin{CD}
  X @\>{f}\>\> Y\end{CD}$, the diagram
  <div>
  $$\begin{CD}
  FX @>{\alpha_X}>> GX \\
  @V{Ff} VV @VV{Gf} V \\
  FY @>{\alpha_Y}>> GY
  \end{CD}$$
  </div>
  commutes, i.e, $Gf \circ \alpha_X = \alpha_Y \circ Ff$.

**Example.** For any vector space $V$, the map $\epsilon_V \colon V \to V^{\*\*}$ defined by $v \mapsto (f \in V^\* \mapsto f(v))$ is linear.[^linearisomorphism] The family $(\epsilon_V)_{V \in \mathsf{Vect}}$ defines a natural transformation $\epsilon \colon 1\_{\mathsf{Vect}} \Rightarrow (\cdot)^{\*\*}$, where $1\_{\mathsf{Vect}}$ is the identity functor and $(\cdot)^{\*\*}$ is the double-dual functor defined by the composition 
$\$\begin{CD}
\mathsf{Vect} @\>{(\cdot)^\*}\>\> \mathsf{Vect}^{\mathrm{op}} @\>{(\cdot)^\*}\>\> \mathsf{Vect}
\end{CD}\$$
One verifies that the naturality condition is satisfied: for all $\begin{CD}
V @\>{l}\>\> W\end{CD}$, the square 
\$$\minCDarrowwidth55pt\begin{CD}
V @\>{v \mapsto (f \in V^\* \mapsto f(v))}\>\> V^{\*\*} \\\\\
@V{l} VV @VV{F \in V^{\*\*} \mapsto (g \in W^\* \mapsto F(g \circ l))} V \\\\\
W @\>{w \mapsto (f \in W^\* \mapsto f(w))}\>\> W^{\*\*}
\end{CD}$\$
commutes.

**Example.** For any set $X$, we have functions 
- $\\{\cdot\\}_X \colon X \to \mathcal{P}X$ defined by $x \mapsto \\{x\\}$

- $\bigcup_X \colon \mathcal{P}\mathcal{P}X \to \mathcal{P}X$ defined by $\mathsf{Y} \mapsto \bigcup \mathsf{Y}$, where $\bigcup \mathsf{Y} := \\{x \in X \mid \exists X' \in \mathsf{Y},\; x \in X'\\}$.

These define natural transformations $\\{\cdot\\} \colon 1\_{\mathsf{Set}} \Rightarrow \mathcal{P}$ and $\bigcup \colon \mathcal{P}^2 \Rightarrow \mathcal{P}$, respectively, where $\mathcal{P}^2 := \mathcal{P}\mathcal{P}$ and $\mathcal{P}$ is the *covariant powerset functor* whose action on morphisms is the *image* (see [Example](#image-inverseimage)).
The naturality conditions are:
<div>
  $$\begin{CD}
  X @>{\{\cdot\}_X}>> \mathcal{P}X \\
  @V{f} VV @VV{\mathcal{P}f} V \\
  Y @>{\{\cdot\}_Y}>> \mathcal{P}Y
  \end{CD}\quad\quad\quad\quad \begin{CD}
  \mathcal{P}^2 X @>{\bigcup_X}>> \mathcal{P}X \\
  @V{\mathcal{P}^2 f} VV @VV{\mathcal{P}f} V \\
  \mathcal{P}^2Y @>{\bigcup_Y}>> \mathcal{P}Y
  \end{CD}$$
  </div>

## Footnotes

[^collection]: We use the informal word "collection" because we do not require that the objects in a category form a set.
[^morphisms]: The collection $\mathcal{C}(X,Y)$ is also called a hom-class.
[^domain]: Given $\begin{CD} X @\>{f}\>\> Y \end{CD}$, $X$ is called the **domain** of $f$ and $Y$ is called the **codomain** of $f$.
[^composition]: We can view composition as a family of functions $\mathcal{C}(Y,Z) \times \mathcal{C}(X,Y) \to \mathcal{C}(X,Z)$ for each triple of objects $X,Y,Z \in \|\mathcal{C}\|$, defined by $(g,f) \mapsto g \circ f$.
[^russell]: By [Russell's paradox](https://en.wikipedia.org/wiki/Russell%27s_paradox), the collection of all sets is not a set; instead, it is a proper class.
[^categorification]: Encoding mathematical structures in categories (and vice versa) is often called "categorification." In this vain, a monoid can be seen as a category with one object, and a group as a category in which every morphism is an isomorphism.
[^posetcategorifications]: A preorder is a category with at most one morphism in every hom-class, and a poset is a category with at most one morphism in every hom-class and in which the only isomorphisms are the identities.
[^problems]: We restrict the objects to small categories in order to avoid size problems and foundational problems.
[^linearisomorphism]: If $V$ is finite-dimensional, this map is a linear isomorphism.