
## 🏛 Class 6 (14-03-2023): Quantifiers (2/3)

### Topics:
- Quantifier raising, finally! 
- The 'singleton quantifier domains' idea
- Prep for the reading material on quantifiers in American Sign Language.

(Office hours this week incidentally in Reuvens 1.46a.) 

----

### Preparation (do this before class; around 30 minutes)

1. **Quantifier scope recap.** It might be useful to brush up your predicate logic before class. For each of the following pairs of formulae, does one entail the other? And the other the one?
   1. ∀x ∃y [KISS(x, y)] &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ∃y ∀x [KISS(x, y)]
   2. ∀x ∀y [KISS(x, y)] &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ∃y ∀x [KISS(x, y)]
   3. ∃x ∃y [KISS(x, y)] &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ∃y ∃x [KISS(x, y)]
   4. ∃x ∃y [KISS(x, y)] &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ∃x ∃z [KISS(x, z)]
   5. ∀x [STUDENT(x) → SLEEP(x)] &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ∀x [STUDENT(x) ∧ SLEEP(x)] 
   6. ∀x [STUDENT(x) ∨ SLEEP(x)] &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ∀x [STUDENT(x)] ∨ ∀x [SLEEP(x)]

-----

## Class notes


### 1. Quantifier raising

**Basic recipe:**
- A quantificational DP node can rise up in the tree, leaving a trace behind.
- Traces get translated as free variables (not bound by any lambda/quantifier).
- Just before composing with the raised DP, the variable is bound by a lambda (for subsequent composition).

_**Question:** What type should the trace be?_

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

Lambda abstraction (and then creating an intension again) over the trace variable z (sometimes assumed to be an operation by a 'silent node' in the tree, here omitted):

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



"Since we have QR and it accounts for the de-re/de-dicto ambiguity, we might as well use it."

_Enter Fodor and Sag..._

### 2. The Fodor and Sag paper

Fodor and Sag distinguish two candidate theories: 
- indefinites are a quantifier, albeit with the special property that it can escape scope islands.
- indefinites have a purely referential reading, i.e., it can refer to one specific individual regardless of scope.

How exactly does the following example help us test which of these is correct?

(69) Each teacher overheard the rumor that a student of mine had been called before the dean.


### 3. Quantifier domains


-----

### Postparation (do this after class; around 3 hours)

1. **Paper on quantifier domains in American Sign Language.** Study the paper [Vertical representation of quantifier domains](https://ojs.ub.uni-konstanz.de/sub/index.php/sub/article/view/307/241) by Kathryn Davidson and Deanna Gagne. (There is a more recent, extended version [here](https://semprag.org/index.php/sp/article/view/sp.15.1/pdf), but we will read the shorter article, which is a bit more accessible at this stage.) Try to be as thorough as time permits at least until (including) section 3.1; do the later sections if you have time remaining.
2. **Quantifier type vs. quantifier domain.** If in ASL, the size of the domain can be indicated by the height at which a quantifier/plural pronoun is signed, then how come one can sometimes find a universal quantifier signed low and an existential quantifier signed high?
3. **Quantifier scope vs. quantifier domain.** How does domain relate to the notion of scope we are already familiar with? In particular, do you expect quantifier sign height in ASL to be able to disambiguate scope ambiguities? If so, in which kinds of sentences? If not, why not?
4. **Linguistic examples _([📩 submit by 17-03-2023](https://brightspace.universiteitleiden.nl/d2l/le/lessons/210127/units/2292941))_.** For each of the linguistic examples in the paper, at least up until (including) section 3.1, explain its purpose in relation to the overall goals of the paper. What does each example show and/or what part of their proposal does it illustrate? If anything remains unclear, indicate so. Some examples can be tricky, so take your time.
5. **Type shift?** On page  121 (12 in the PDF) the authors write:
   > If there  is  an  intervening  type  shift, then the  usual  semantics for  generalized  quantifiers  can  be  used, but  of  course the domain is still provided  through  the locus  in  the  DP  complement.
  
   Where would a 'type shift' be necessary in the trees in figure 9? First think about what type each constituent (quantifier, pronoun, predicate) ought to have given how they would combine in other sentences. Then identify a place in the tree where the type one constituent _needs_ from its argument is not what it _gets_.
6. **Is it just emphasis?** If you have time to read section 3.4, can you explain why the authors believe quantifier sign height in ASL is not just a form of emphasis? 