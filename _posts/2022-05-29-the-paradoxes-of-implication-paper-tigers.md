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

This jarring result is created because of the difference in the way implication is treated in classical logic as opposed to natural language. This discussion gives rise to the question of whether we should amend formal logic to facilitate ease of understanding.

I contend that the paradoxes of implication do not constitute a significant threat to classical logic; at worst, they are unsightly. Although logical constructions are motivated by intuitions about natural language, we must be wary when trying to reshape logic based on natural language interests. The purpose of logic is to filter out that which is muddled. By altering logic to cater for intuitive understanding, we run the risk of overfitting to the vagueries that govern colloquial discourse, thereby undermining the utility of formal logic. Furthermore, such a principle has no end in sight. Trying to rid any system of formalization of all unintuitive truths is a fool's errand.

As logician Alfred Tarski notes, it cannot be expected that any two people will converge on the meaning of any phrase [[4](#tarski)]. Logical constructs, like words, are bound to their definitions. Thus, the paradoxes of implication are paradoxes insofar as the observer is unaware of the formal definition of implication. This is a non-issue especially when the definition is made for a good reason, which will be examined later. Some logicians such as Anderson and Belnap go as far as to say that definitions of logical constructs should be viewed as disconnected from those of their cognate terms [[1](#anderson-belnap)].

We must, then, accept these paradoxes as true. The resistance to doing so is unfounded. Consider the paradox that arises from the following statement. *This statement is false.* This statement sends logicians into crisis because it contains an internal contradiction. The paradoxes of implication contain no such internal contradiction. In fact, they are hyper-consistent with the rules that govern their existence. Yet, they send even the most informed logicians into crisis merely because they conflict with the intuitions of an unprimed observer. Also, unlike most paradoxes, the paradoxes of implication have perfectly intuitive explanations — a false statement implies any statement because the false statement is never forthcoming.

It should be stated that statements that seem absurd are not automatically wrong, nor do they signal that something needs fixing. Indeed, the probability that a continuous random variable takes on any one value is 0. The result of multiplying together no numbers, the so-called vacuous product, is equal to 1. The entities $0.999...$ and $1$ represent the *exact* same number. Switching your choice of doors on a famous game show doubles your chance of winning a car. These are all mathematically valid claims that we have taken no liberties to modify. Additionally, some of the principles listed above have tremendous utility in ensuring that mathematics is as consistent as possible. Similarly, allowing an implication to be true when the premise is not forthcoming greatly simplifies logic. In classical logic, this allows implication to function as a semantic analog for set inclusion.

The principles behind the paradoxes of implication cannot be disturbed without causing a greater catastrophe than the paradoxes themselves. For instance, consider a simple proof of the paradox of entailment as follows

1. $p \land \neg p$
2. $p$                  from 1
3. $p \lor q$           from 2
4. $\neg p$             from 3
5. $q$,                 from 3,4

where the last step uses the disjunctive syllogism [[2](#paradoxes)]. Then, anyone who sets out to resolve these paradoxes must propose a system that makes at least one of these rules impossible, requiring lengthy development and justification. He must also acknowledge the fact that the paradoxes of implication are easily understood with a minute shift in the way one thinks about implication. Therefore, I propose, a large-scale modification of classical logic would be unproductive.

Remedies proposed to the paradoxes of implication are largely ineffectual and detract from the simplicity and elegance of classical logic. One may naively suggest that the only problem with material implication is the fact that $F \rightarrow F$ is valid. Following this suggestion through, if we define the truth value of the implication $F \rightarrow F$ to be false, the notion of implication becomes meaningless, since it makes the truth value of the implication equivalent to that of the consequent.

One may attempt to remove rules of negation such as the law of excluded middle and double-negation-elimination to create a more restricted logic. This encroaches on the territory of intuitionistic logic. This will not do, however, as the principle of vacuous discharge still emerges. This principle allows us to prove the paradox $p \vdash q \rightarrow p$ in one fell swoop.

If we are to accept the paradoxes, we lack a notion of causation or material connection between antecedents and consequents. *Relevant logic* attempts to partially fix this problem. For example, in a system of relevant logic, we want to ensure that an implication is only provable if its antecedent and consequent share at least one variable. This would resolve paradoxes such as the paradox of entailment. One system of relevance logic is proposed by John Slaney, which uses bunches instead of sets to differentiate between assumptions conjoined by and-introduction and modus ponens [[3](#substructural)]. However, even this system does not ensure that there is a *causal* relationship between antecedent and consequent, only that there is some semblance of correlation. This comes at the cost of greater intuitions in other areas. Since the left-hand sides of sequents are no longer sets, we may no longer contract assumptions. This also has drastic implications for the fundamental nature of sequents as quantity of identical assumptions now confer different meaning. Similar problems are visited upon modal logic, which introduces a dimension of possibility into logical formulae. Not only are suggested improvements lacking in both elegance and efficacy, but they also require quantum leaps in intuition.

In summary, logic should be concerned with truth and nothing but the truth. That is to say, one's visceral reactions to logical statements should be of no concern to logic. This is not stated in pure ignorance, however. The rules behind these paradoxes are well-founded and crucial to set-theoretic interpretations of logic. Labeling these formulae paradoxes is but for a lack of trying to understand them. When one evaluates these paradoxes jointly with their antecedents and consequents in sight, they become crystal clear. For that, they are paper tigers. To those who say that this does not address the issue, I posit that classical logic is the simplest, most unrestrained system that we have available to us, which explains why the field of logic has evolved to accept its primacy; the best response has already been identified by intellectual evolution. The paradoxes of implication are then left in an awkward place. Any cure one is to propose will metastasize and almost certainly become worse than the ostensible disease.

## References

[<a name="anderson-belnap">1</a>] Anderson, A.R. and Belnap, N.D., 1975. *Entailment: The Logic of Relevance and Neccessity*. Volume 1. Princeton: Princeton University Press.

[<a name="paradoxes">2</a>] Slaney, J., 2021. *Paradoxes of Implication*. [online] The Logic Notes. Available at: <http://users.cecs.anu.edu.au/~jks/LogicNotes/paradoxes.html> [Accessed 29 May 2022].

[<a name="substructural">3</a>] Slaney, J., 2021. *Substructural Logics*. [online] The Logic Notes. Available at: <http://users.cecs.anu.edu.au/~jks/LogicNotes/rules-nonclassical.html> [Accessed 29 May 2022].

[<a name="tarski">4</a>] Tarski, A., 1941. *Introduction to Logic and to the Methodology of Deductive Sciences*. New York: Dover Publications.