
## 🏛 Class 5 (07-03-2023): Quantifiers (1/3)

### Topics:
- Final part of propositional attitudes
- Quantifier raising and the de-re reading

----

### Preparation (do this before class; around 30 minutes)
Up to you!

----


## Discuss homework 
📝 Discuss homework exercises 2-6 (set theory, relations, functions, interpretation).


## The fragment so far

### Lexical entries (translation) ###

- sleeps ⇝ λwₛ λxₛₑ . SLEEP(w)(x(w))
- student ⇝ λwₛ λxₛₑ . STUDENT(w)(x(w))
- a ⇝ λwₛ λP<sub><s, <<s, e>, t></sub> λQ<sub><s, <<s, e>, t></sub> ∃x [P(w)(λu.x) ∧ Q(w)(λu.x)]
- John ⇝ λwₛ. john(w)
- believe ⇝ λwₛ λℙₛₜ λxₛₑ ( BELIEVE(w)(x(w), ℙ) )

### Interpretation of BELIEVE ###

> Let Bel(d, w) be the set of worlds that individual d considers possible in w.

📖 Discuss homework exercise 7 (belief worlds etc.).

---

In class we arrived at the following _monstrosity_:

> (1) ⟦BELIEVE⟧ = {<w, {<<d, p>, Bel(d, w) ⊆ p> | for every individual d}> | for every world w}

(So a function from worlds, to functions from individual+proposition pairs (<d, p>) to truth values (Bel(d, w) ⊆ p), namely True if d's belief worlds in w are included in p and False otherwise.)

But here is a clearer (formally equivalent) formulation:

(2) ⟦BELIEVE(w)(a, ℙ)⟧ = True if Bel(⟦a⟧, ⟦w⟧) ⊆ ⟦ℙ⟧, False otherwise 

Paraphrase: the logical expression on the left (informally: in world w, a believes ℙ) whenever in the given world, all of the individual's belief worlds are ones that make the proposition True.

> TODOs:
> - Derive the de-re/de-dicto stuff with quantifier raising.
> - Discuss the Fodor and Sag stuff on why this may not be sufficient.

---

📖 Discuss homework exercise 8 (Mary believes a student sleeps).

a student ⇝ λw ❴a❵(w)(❴student❵)
- λw (λwλPλQ.∃x [P(w)(λu.x) ∧ Q(w)(λu.x)])(w)(λvλx.STUDENT(v)(x(v)))
- λw (λPλQ.∃x [P(w)(λu.x) ∧ Q(w)(λu.x)])(λvλx.STUDENT(v)(x(v)))
- λw (λQ.∃x [ (λv λx.STUDENT(v)(x(v))(w)(λu.x) ∧ Q(w)(λu.x)]))
- λw (λQ.∃x [ (λx.STUDENT(w)(x(w))(λu.x) ∧ Q(w)(λu.x)]))
- λw (λQ.∃x [ (STUDENT(w)((λu.x)(w)) ∧ Q(w)(λu.x)]))
- λw (λQ.∃x [ (STUDENT(w)(x) ∧ Q(w)(λu.x)]))

a student sleeps ⇝ λw ❴a student❵(w)(❴sleeps❵) 
- λw. (λw (λQ.∃x [ STUDENT(w)(x) ∧ Q(w)(λu.x)]))(w) (λvλx.SLEEP(v)(x(v)))
- λw. (λQ.∃x [ STUDENT(w)(x) ∧ Q(w)(λu.x)]) (λvλx.SLEEP(v)(x(v)))
- λw. ∃x [ STUDENT(w)(x) ∧ (λvλx.SLEEP(v)(x(v)))(w)(λu.x)]
- λw. ∃x [ STUDENT(w)(x) ∧ (λx.SLEEP(w)(x(w)))(λu.x)]
- λw. ∃x [ STUDENT(w)(x) ∧ SLEEP(w)((λu.x)(w))]
- λw. ∃x [ STUDENT(w)(x) ∧ SLEEP(w)(x)]

believes a student sleeps ⇝ λw ❴believes❵(w) (❴a student sleeps❵)
- λw (λw λℙ λx ( BELIEVE(w)(x(w), ℙ) ))(w) (λw.∃y[STUDENT(w)(y) ∧ SLEEP(w)(y)])
- λw (λℙ λx ( BELIEVE(w)(x(w), ℙ) )) (λw.∃y[STUDENT(w)(y) ∧ SLEEP(w)(y)])
- λw (λx (BELIEVE(w)(x(w), (λw.∃y[STUDENT(w)(y) ∧ SLEEP(w)(y)]))))
- λw λx (BELIEVE(w)(x(w), (λw.∃y[STUDENT(w)(y) ∧ SLEEP(w)(y)])))

Mary believes a student sleeps ⇝ λw ❴believes a student sleeps❵(w) (❴mary❵)
- λw (λw λx (BELIEVE(w)(x(w), (λu.∃y[STUDENT(u)(y) ∧ SLEEP(u)(y)]))))(w) (λv.mary(v))
- λw (λx BELIEVE(w)(x(w), (λu.∃y[STUDENT(u)(y) ∧ SLEEP(u)(y)]))) (λv.mary(v))
- λw (BELIEVE(w)((λv.mary(v))(w), (λu.∃y[STUDENT(u)(y) ∧ SLEEP(u)(y)])))
- λw (BELIEVE(w)(mary(w), (λu.∃y[STUDENT(u)(y) ∧ SLEEP(u)(y)])))

Now recall:
> (2) ⟦BELIEVE(w)(a, ℙ)⟧ = True if Bel(⟦a⟧, ⟦w⟧) ⊆ ⟦ℙ⟧, False otherwise

So:
- ⟦(BELIEVE(w)(mary(w), (λu.∃y[STUDENT(u)(y) ∧ SLEEP(u)(y)])))⟧ = is True if Bel(⟦mary(w)⟧, ⟦w⟧) ⊆ ⟦λu.∃y[STUDENT(u)(y) ∧ SLEEP(u)(y)]⟧, False otherwise 

Further paraphrasing in the meta-language:
- It is True if Bel(⟦mary(w)⟧, ⟦w⟧) ⊆ {u | u is a world in there exists something that is both student and sleeping}, False otherwise
- It is True if, given whoever is Mary in the world denoted by w, all worlds they consider possible in that world, are ones in which something is both a student and sleeping. 

_**Q:** Is this a de re or de dicto reading?_

---

📖 Discuss homework exercise ~~9~~ 10 (factivity of know).

- ⟦KNOW(w)(a, ℙ)⟧ = True if Bel(⟦a⟧, ⟦w⟧) ⊆ ⟦ℙ⟧ and ...; False otherwise.


🏁 We didn't quite make it till the end again: next week quantifier raising (also in the textbook homework below).


-----

### Postparation (do this after class; around 3 hours)

Exercises will be completed later today; nothing to submit this week _but if you didn't submit last week's assignment, please give it another try._

1. **Models and propositional attitudes.** 
   1. Draw a model with three possible worlds, such that in one world Alf and Beth both correctly believe Gemma walks, in another Alf and Beth both incorrectly believe Gemma walks, and in the third Alf and Beth disagree about whether Gemma walks.
   2. Define the exact same model in set theory, without pictures. For instance, for each world, specify the extensions of the constants alf, beth, and gemma, the predicate WALK, and the predicate BELIEF. Note that the latter can be indirectly specified by listing the belief worlds of each individual in each world (e.g., in w1, Alf considers worlds w1 and w3 possible -- but try it in set theoretical terms).
2. **Chapter 14. Quantifiers** Study Chapter 14 in the textbook.
3. **First vs. second-order logic?** The textbook proposes that quantifiers express _relations_ between the sets denoted by predicates. Later on (p.254) this is phrased in terms of 'second-order' properties, and the author gives a suggestion: 
   > For example, we could define the denotation set of a NP like _most men_ to be the set of all properties which are true of most men. The sentence _Most men snore_ would be true just in case the property of snoring is a member of ⟦most men⟧. However, the mathematical formalism of this approach is more complex than we can handle in the present book. [...]

   We, of course, have already been doing higher-order logic! Would you say our treatment so far of quantifiers like _a student_ and _every student_ (at least their _extensions_) matches the suggestion made here regarding _most men_? (In class we will explore how we can generalize our approach to other quantifiers, which ''.)
4. **Restricted quantifier notation.** The notation introduced in 14.3 is informal. Nevertheless, it looks like the formulae we are used to, with quantifiers and square brackets. Are looks deceiving?
5. **Scope ambiguities.** For examples (24), (25) and (26) in the textbook, which illustrate non-entailments, define a model (picture, or set theory, or both) that demonstrates this lack of an entailment relation. (Recall from Semantics 1: to show that A does _not_ entail B, you need to define a model where A is true but B is false.)
6. **Scope ambiguities and entailment (2).** From the textbook do **Homework** exercise A (p.265). _In addition_, if a sentence allows two interpretations, determine whether one entails the other and vice versa, and support your answer with an example (e.g., one or more models).

...Additional practice exercises (lambdas, intensions, composition) will come online soon...