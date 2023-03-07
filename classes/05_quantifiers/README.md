
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


## Quantifier raising recap

**Basic recipe:**
- A quantificational DP node can rise up in the tree, leaving a trace behind.
- Traces get translated as free variables (not bound by any lambda/quantifier).
- Just before composing with the raised DP, the variable is bound by a lambda (for subsequent composition). 

_**Q:** What type should the trace be?_

t sleeps ⇝ λw ❴sleeps❵(w)(❴t❵) 
- λw (λvλx.SLEEP(v)(x(v)))(w)(z)
- λw (λx.SLEEP(w)(x(w)))(z)
- λw (SLEEP(w)(z(w)))

believes t sleeps ⇝ λw ❴believes❵(w) (❴t sleeps❵)
- λw (λw λℙ λx ( BELIEVE(w)(x(w), ℙ) ))(w) (λv (SLEEP(v)(z(v))))
- λw (λℙ λx ( BELIEVE(w)(x(w), ℙ) )) (λv (SLEEP(v)(z(v))))
- λw (λx BELIEVE(w)(x(w), λv(SLEEP(v)(z(v)))))

Mary believes t sleeps ⇝ λw ❴believes t sleeps❵(w) (❴mary❵)
- λw (λw λx BELIEVE(w)(x(w), λv (SLEEP(v)(z(v)))))(w) (λv.mary(v))
- λw (λx BELIEVE(w)(x(w), λv (SLEEP(v)(z(v))))) (λv.mary(v))
- λw (BELIEVE(w)((λv.mary(v))(w), λv (SLEEP(v)(z(v)))))
- λw (BELIEVE(w)(mary(w), λv (SLEEP(v)(z(v)))))

Lambda abstraction over the trace variable z:

Mary believes t sleeps ⇝ λw λz (BELIEVE(w)(mary(w), λv (SLEEP(v)(z(v)))))

Composing with the raised quantifier:

A student Mary believes t sleeps ⇝ λw ❴a student❵(w)(❴Mary believes t sleeps❵)
- λw (λw λQ.∃x [ (STUDENT(w)(x) ∧ Q(w)(λu.x)])) (w) (λu λz (BELIEVE(u)(mary(u), λv (SLEEP(v)(z(v))))))
- λw (λQ.∃x [ (STUDENT(w)(x) ∧ Q(w)(λu.x)])) (λu λz (BELIEVE(u)(mary(u), λv (SLEEP(v)(z(v))))))
- λw (∃x [ (STUDENT(w)(x) ∧  (λu λz (BELIEVE(u)(mary(u), λv (SLEEP(v)(z(v))))))  (w)(λu.x)]))
- λw (∃x [ STUDENT(w)(x) ∧  (λz (BELIEVE(w)(mary(w), λv (SLEEP(v)(z(v))))))(λu.x)])
- λw (∃x [ STUDENT(w)(x) ∧  BELIEVE(w)(mary(w), λv (SLEEP(v)((λu.x)(v))))])
- λw (∃x [ STUDENT(w)(x) ∧  BELIEVE(w)(mary(w), λv SLEEP(v)(x))])

De re :)


### 4. The Fodor and Sag paper

Fodor and Sag distinguish two candidate theories: 
- indefinites are a quantifier, albeit with the special property that it can escape scope islands.
- indefinites have a purely referential reading, i.e., it can refer to one specific individual regardless of scope.

How exactly does the following example help us test which of these is correct?

(69) Each teacher overheard the rumor that a student of mine had been called before the dean.

🏁

-----

### Postparation (do this after class; around 3 hours)

Exercises will be completed later today; nothing to submit this week.

1. **tbd.** tbd.