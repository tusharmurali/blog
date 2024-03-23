---
layout: post
title: "The Paradoxes of Implication: Paper Tigers"
tags: philosophy
author:
  - Tushar Muralidharan
---
The goal of logic is to formalize arguments. Arguments take the form of natural language, which subjects them to varying interpretations. On occasion, we encounter provable logical statements that are incongruous with our intuitive reasoning. The paradoxes of implication are just that — a set of provable logical statements whose conclusions do not depend on their premises [[2](#paradoxes)]. These paradoxes are made possible because, in classical logic, a true statement is implied by any statement, and a false statement implies any statement. Consider the following statement. *If this paper is wet and this paper is not wet, then the Moon is made out of cheese.* Many observers find these statements unsettling; what does the condition of this paper tell you about the Moon? Surprisingly, this statement has a proof in classical logic. If $p$ is the statement that this paper is wet, and $q$ is the statement that the Moon is made out of cheese, then we proceed as follows:

\\[p, \neg p \vdash q\\]
\begin{array} {rl}\alpha_1 & (1) & p & \text{A} \\\\ \alpha_2 & (2) & \neg p & \text{A} \\\\ \alpha_1, \alpha_2 & (3) & \neg \neg q & \text{1, 2[ ] RAA} \\\\ \alpha_1, \alpha_2 & (4) & q & 3 \neg \neg \text{E}  \end{array}

## References

[<a name="anderson-belnap">1</a>] Anderson, A.R. and Belnap, N.D., 1975. *Entailment: The Logic of Relevance and Neccessity*. Volume 1. Princeton: Princeton University Press.

[<a name="paradoxes">2</a>] Slaney, J., 2021. *Paradoxes of Implication*. [online] The Logic Notes. Available at: <http://users.cecs.anu.edu.au/~jks/LogicNotes/paradoxes.html> [Accessed 29 May 2022].

[<a name="substructural">3</a>] Slaney, J., 2021. *Substructural Logics*. [online] The Logic Notes. Available at: <http://users.cecs.anu.edu.au/~jks/LogicNotes/rules-nonclassical.html> [Accessed 29 May 2022].

[<a name="tarski">4</a>] Tarski, A., 1941. *Introduction to Logic and to the Methodology of Deductive Sciences*. New York: Dover Publications.
