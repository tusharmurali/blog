---
layout: post
title: "An Introduction to Category Theory"
tags: mathematics
ordered_toc: true
author:
  - Tushar Muralidharan
---

Category theory aims to unify mathematics by studying mathematical structures and their relationships. Its objects of study are mathematical structures themselves, and many traditional mathematical concepts can be reformulated in category-theoretic language, offering deeper insights.

## Categories

**Definition.** A **category** $\mathcal{C}$ consists of
- a collection[^collection] $\|\mathcal{C}\|$ of **objects**
- for every pair of objects $X,Y \in \|\mathcal{C}\|$, a collection $\mathcal{C}(X,Y)$ of **morphisms**[^endomorphisms] from[^domain] $X$ to $Y$
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

**Definition.** A category $\mathcal{C}$ is called **locally small** if for every $X,Y \in \|\mathcal{C}\|$, $\mathcal{C}(X,Y)$ is a set. If $\|\mathcal{C}\|$ is also set, then $\mathcal{C}$ is called **small**.

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
  - $\mathsf{Rel}(X,Y) :=$ the set of all relations between $X$ and $Y$, described by functions $R : X \times Y \to \\{\text{True},\text{False}\\}.$
  - $1_X :=$ the graph of the identity function on $X$, i.e. $(x,y) \mapsto \mathrm{Bool}(x == y)$
  - Given $\begin{CD}
X @\>{f}\>\> Y @\>{g}\>\> Z
\end{CD}$, define $\begin{CD}
X @\>{g \circ f}\>\> Z
\end{CD}$ by 

## Footnotes

[^collection]: We use the informal word "collection" because we do not require that the objects in a category form a set.
[^endomorphisms]: Morphisms from an object to itself are called **endomorphisms**.
[^domain]: Given $\begin{CD} X @\>{f}\>\> Y \end{CD}$, $X$ is called the **domain** of $f$ and $Y$ is called the **codomain** of $f$.
[^composition]: We can view composition as a family of functions $\mathcal{C}(Y,Z) \times \mathcal{C}(X,Y) \to \mathcal{C}(X,Z)$ for each triple of objects $X,Y,Z \in \|\mathcal{C}\|$, defined by $(g,f) \mapsto g \circ f$.
[^russell]: By [Russell's paradox](https://en.wikipedia.org/wiki/Russell%27s_paradox), the collection of all sets is not a set; instead, it is a proper class.