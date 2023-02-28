
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


### 0. Homework discussion


### 1. Lexical entries (and models) for propositional attitude verbs 


### 2. Reflections on 'indirect interpretation', logic, and models


### 3. Finally: a possible derivation of de-re/de-dicto ambiguity

- sleeps ⇝ λwₛ λxₛₑ . SLEEP(w)(x(w))
- student ⇝ λwₛ λxₛₑ . STUDENT(w)(x(w))
- a ⇝ λwₛ λP<sub><s, <<s, e>, t></sub> λQ<sub><s, <<s, e>, t></sub> ∃x [P(v)(λu.x) ∧ Q(v)(λu.x)]
- John ⇝ λwₛ. john(w)
- believe ⇝ λwₛ λℙₛₜ λxₛₑ ( BELIEVE(w)(x(w), ℙ) )

Let Bel(d, w) be the set of worlds that individual d considers possible in w.

In class we arrived at the following:

(1) ⟦BELIEVE⟧ = {<w, {<(d, p), Bel(d, w) ⊆ p> | for every individual d}> | for every world w}

But here is a much clearer (formally equivalent) formulation I should have used (NB. Whereas in (1), w, d and p were variables in the meta-language, in (2) we use w, a and ℙ in the object language, hence the square brackets around them are needed on the right-hand side):

(2) ⟦BELIEVE(w)(a, ℙ)⟧ = True if Bel(⟦a⟧, ⟦w⟧) ⊆ ⟦ℙ⟧, False otherwise 

Altogether, equation (2) states that the logical expression on the left (informal paraphrase: in world w, a believes ℙ) is interpreted as True whenever the individual's belief worlds in that world are a subset of the given proposition, and False otherwise. 

Equivalently: the logical expression on the left (informally: in world w, a believes ℙ) whenever in the given world, all of the individual's belief worlds are ones that make the proposition True.

(Equation (1) merely enables equation (2) to be derived compositionally, but we need not care about that; we care only really about compositionality of the object language, not the logical language...)

TODOs:
- Derive the de-re/de-dicto stuff with quantifier raising.
- Discuss the Fodor and Sag stuff on why this may not be sufficient.

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
   1. Specify in set theory an example (say, on a domain of four individuals) of the type of function that could be the _extension_ of an intransitive verb like _walk_. That is, fill in the dots: ⟦WALK(w)⟧ = .... If you are unsure, consider the _type_ (s, e, t, etc.) of (the extension of) intransitive verbs.
   2. Similarly, specify an example of the type of function that could be the _intension_ of an intransitive verb, i.e., ⟦WALK⟧ = ....
7. **Belief.** Suppose there are two worlds: w₁ in which it rains, and w₂ in which it doesn't. Specify (set-theoretically) John's belief worlds in w₁, such that, in w₁, John believes that it doesn't rain. Next, specify John's belief worlds in w₂ such that, in that world, John is unsure whether it rains. (This can be difficult to wrap your head around at first, so collaborate, and/or ask in the forum if you get stuck!)
8. **Derivation with 'belief' _([📩 submit by 03-03-2023](https://brightspace.universiteitleiden.nl/d2l/le/lessons/210127/units/2292941))_.** 
   1. Provide a formal derivation of the logical translation of the sentence 'A student sleeps'.
   2. Next, compositionally derive a translation (using the result you obtained previously and the lexical entry from the class notes) for the sentence 'Mary believes a student sleeps'.
   3. Define a model (using English, set theory and/or pictures) containing at least one world in which the sentence is true, specifying all the relevant pieces (mainly, Mary's belief worlds).
   4. Does your translation correspond to a de-re or de-dicto reading? (Next week we'll derive the other reading; it's taking a while to get there!)
10. **An account of the factivity of know.**
    1. First, define a lexical entry for the verb _know_ (translation into logic), that is entirely analogous to that of _belief_, except it has predicate KNOW instead of BELIEVE. For starters, let's interpret KNOW exactly like BELIEVE (see class notes): ⟦KNOW(w)(a, ℙ)⟧ = True if Bel(⟦a⟧, ⟦w⟧) ⊆ ⟦ℙ⟧, False otherwise.
    2. It has often been observed that English _know_ presupposes the truth of its complement (i.e., it is weird to say "Anna _knows_ that it's raining" if you (as the speaker) think that it isn't.). This is the _factivity_ presupposition of _know_. By your own judgments (in a language of choice), test which of the following propositional attitude verbs similarly presuppose factivity (provide concrete linguistic examples as evidence): _believe_, _discover_, _see_, _doubt_.
    3. Let's add a shorthand w<sub>u</sub> to our set-theoretical meta-language, which always refers to the _actual_ world in which the utterance is being made. Can you capture the factivity of _know_ by tweaking the interpretation of KNOW, adding some kind of constraint involving w<sub>u</sub> and ⟦ℙ⟧? That is, fill in the dots: ⟦KNOW(w)(a, ℙ)⟧ = True if Bel(⟦a⟧, ⟦w⟧) ⊆ ⟦ℙ⟧ and ..., False otherwise. _(This is tricky to conceive, but not super complicated once you see it. Please collaborate, and ask in the forum if you get stuck, there indicating what you have tried so far and why it doesn't work.)_
