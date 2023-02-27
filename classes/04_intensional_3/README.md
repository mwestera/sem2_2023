
## 🏛 Class 4 (28-02-2023): Intensional semantics (3/3)

### Topics:
- Finalizing our intensional semantic fragment... 
- ...with special focus on set theory, models, type theory, logic and their relations.
- Discussing the paper from week 2.

----

### Preparation (do this before class; around 20 minutes)

1. **Review your week 2 submission.** Please take a moment to review your own submitted assignment about the de-re/de-dicto paper! Looking back, does it adequately address that week's assignment? Does it help you remember the crucial parts of the paper? Do you see room for improvement?

-----

## Class notes


### 1. Lexical entries (and models) for propositional attitude verbs 


### 2. Finally: a possible derivation of de-re/de-dicto ambiguity


### 3. Reflections on 'indirect interpretation', logic, and models



### 4. The paper you studied


### 5. Open questions


-----

### Postparation (do this after class; around 3 hours)

1. **Indirect interpretation.** In your own words, explain the method of 'indirect interpretation' in semantics. Make sure to use the terms meta-language and object-language, explain the role of models, and identify possible (dis)adantages of using logic as an intermediary in modeling natural language semantics. 
2. **Set theory exercises.** Suppose we have sets A = {1, 3, 5}, B = {2, 4, 6} and C = {1, 2, 4, 5}. For each of the following expressions, indicate whether they are well-formed, and if so, write down what the expression evaluates to (in these cases either a truth value or a set):
   1. A ∪ B
   2. A ∩ B
   3. A ∪ C
   4. B ∩ C
   5. 3 ∈ A
   6. A ∈ C
   7. C ∈ 6
   7. (A ∪ B) = C
   8. (A ∩ B) ∪ C
   9. (A ∪ B) ∩ C
   10. (A ∪ B) ∪ C
   11. A ∪ (B ∪ C)
   12. (A ∪ B) ∩ A = A (is this true in general, for _any_ sets A and B)
   13. (A ∩ B) ∪ A) = A
   14. A ⊆ C
3. **Relations.** We saw that binary relations can be modeled in set theory as a set of pairs (do you understand why?). Assuming the domain contains three individuals Alf (a) and Beth (b) and Chris (c), specify in set theory a possible _interpretation_ for the predicate LOVE that maximizes the amount of drama.
4. **Relations (2).** Which of the following sets could model a possible interpretation for a predicate like IS_PARENT_OF (albeit on a limited domain of individuals)? What about the predicate IS_ANCESTOR_OF? Which situations would be incestuous? Which would require time travel?
   1. {<a, b>, <b, c>, <b, d>, <a, d>}
   2. {<a, b>, <b, a>, <c, d>}
   3. {<a, b>, <a, c>, <a, d>}
   4. {<a, b>, <a, c>, <b, c>, <c, d>, <a, d>, <b, d>}
   5. {<a, b>, <b, c>, <c, a>}
5. **Functions.** Functions are a special type of relation. Do you remember the criteria? Assuming a domain of four individuals, which of the following relations are functions? Why (not)?
   1. {<a, b>, <c, d>}
   2. {<a, b>, <b, c>, <c, d>, <d, a>}
   3. {<a, b>, <b, c>, <c, d>, <d, a>, <a, c>, <b, d>}
   4. {<a, b>, <b, c>, <c, d>, <d, a>}
   5. {<a, b>, <b, c>, <a, c>, <d, c>}
6. **Functions and intensions.** 
   1. Specify in set theory an example (say, on a domain of four individuals) of the type of function that could be the _extension_ of an intransitive verb like _walk_. If you are unsure, consider the _type_ (s, e, t, etc.) of intransitive verbs.  
   2. Similarly, specify an example of the type of function that could be the _intension_ of an intransitive verb.
   3. Do the same for the extension and intension of a _transitive_ verb like _kiss_.
7. **Belief.** Recall that BELIEF can be interpreted as a relation between each individual (the subject) and a set of its 'belief worlds'. Specify such a relation in set theory, assuming, say, three individuals and four worlds, such that individual _a_ believes it is raining, individual _b_ believes that it is not raining, and individual _c_ does not hold either belief (i.e., they are unsure).
8. **Quantifier raising for de-re/de-dicto.** 
   1. Mostly from memory (only peak at your notes if absolutely necessary), write out the formal, compositional derivation of the _two_ translations predicted for the sentence 'Mary believes a student sleeps'.
   2. If you got stuck, at least provide the two translations you would expect to get out at the top node. Is there an entailment relation between the two translations? Should there be? Try to provide reasoning for your answer, illustrated by one or several models.
9. **Why the quantifier-raising account may be insufficient for wide-scope indefinites.** Do you remember from the paper (and class discussion) the _main argument_ why a quantifier raising account may be insufficient? (Remember that section 2 has a rather slow build up, culminating in the most serious evidence in section 2.3). Try to recontruct some of the crucial examples, and indicate exactly what the problem is. Does this mean quantifier raising should _not_ be assumed as a possible mechanism in semantics?
10. **Know (factivity) _([📩 submit by 03-03-2023](https://brightspace.universiteitleiden.nl/d2l/le/lessons/210127/units/2292941))_.**
   1. Provide a lexical entry for the verb _know_ (translation into logic), analogous to that of _belief_, and also specify its interpretation into the set-theoretical meta-language. You can refer to an individual's 'knowledge worlds' in a given world as, say, the set K_w.
   2. It has often been observed that English _know_ presupposes the truth of its complement (i.e., it is weird to say "Anna _knows_ that it's raining" if you (as the speaker) think that it isn't.). This is the _factivity_ presupposition of _know_. By your own judgments (in a language of choice), test which of the following propositional attitude verbs similarly presuppose factivity (provide concrete linguistic examples as evidence): _believe_, _discover_, _see_, _doubt_.
   3. Let's say w₀ in our set-theoretical meta-language always refers to the _actual_ world in which the utterance is being made. Can you capture the factivity presupposition of _know_ by tweaking the interpretation of KNOW, that is, on the set theory side? Perhaps factivity can be modeled as some kind of relation between the actual world w₀ and a person's knowledge-worlds...
   4. Instead of specifying factivity in the _interpretation_ of the predicate KNOW, we could also include it, instead, in the lexical entry for _know_, i.e., in its _translation_ to logic. Find a way to achieve this, by making use of the fact that functions (to truth values) can be seen as sets.