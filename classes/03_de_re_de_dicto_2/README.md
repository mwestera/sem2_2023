
## 🏛 Class 3 (21-02-2023): Intensional semantics (2/3) 

### Topics:
1. Formal fragment of intensional semantics.
2. Challenges & open questions


----

### Preparation (do this before class; around 20 minutes)

1. **Homework review.** Review your own homework from last time.


----


## Class notes:

### 1. A formal fragment in intensional semantics

Partial recap from last class:

Types:
- Names: e or <s, e>?
- Nouns/intransitive verbs: <s, et> (= <s, <e, t>>; 'property') 
- Quantifiers: <s, <et, <et, t>>>
  - After 'eating' the first noun (e.g., "every student"): <s, <et, t>>
- Sentence: <s, t> ('proposition')
- Definite description: <s, e> ('individual concept')


**Extensional function application:** 
- For a syntactic node with expressions α and β as children, a candidate translation is: ⧙α⧘(⧙β⧘)

**Intensional function application:**
- For a syntactic node with expressions α and β as children, a candidate translation is: λw ⧙α⧘(w)(⧙β⧘)

> Q: why not apply β to world w too?


#### Derivation with intransitive verb 'sleep'

John sleeps.

- sleeps ⇝ λwₛ λxₛₑ . SLEEP(w)(x(w))
- John ⇝ λwₛ. john(w)
- John sleeps ⇝ λv . ⧙sleeps⧘(v)(⧙john⧘)
  - λv . (λwₛ λxₛₑ . SLEEP(w)(x(w)))(v) (λwₛ. john(w))
  - λv . (λxₛₑ . SLEEP(v)(x(v))) (λwₛ. john(w))
  - λv . (SLEEP(v)((λwₛ. john(w))(v)))
  - λv . (SLEEP(v)(john(v)))

'A function from each world v to true if whoever is John in world v sleeps in world v, and false otherwise.'

Equivalently:

'The set of worlds where whomever is John in that world sleeps in that world'

More sloppily:

'The set of worlds in which John sleeps'


#### Derivation with transitive verb 'see'

Susie sees John.

- sees ⇝ λwₛ λyₛₑ λxₛₑ . SEE(w)(x(w), y(w))
- sees John ⇝ λuₛ . ⧙sees⧘(u)(⧙john⧘)
  - λu (λwₛ λyₛₑ λxₛₑ . SEE(w)(x(w), y(w)))(u) (λv. john(v))
  - λu (λyₛₑ λxₛₑ . SEE(w)(x(u), y(u))) (λv. john(v))
  - λu (λxₛₑ . SEE(u)(x(u), (λv. john(v))(u)))
  - λu λxₛₑ . SEE(u)(x(u), john(u))
  - λu λxₛₑ . SEE(u)(x(u), john(u))
- Susie sees John ⇝ λwₛ . ⧙sees John⧘(w)(⧙susie⧘) 
  - λw . (λuₛ λxₛₑ . SEE(u)(x(u), john(u)))(w) (λv. susie(v))
  - λw . (λxₛₑ . SEE(w)(x(w), john(w))) (λv. susie(v))
  - λw . (SEE(w)((λv. susie(v))(w), john(w)))
  - λw . SEE(w)(susie(w), john(w)) 

So: the set of worlds in which whoever is Susie in that world, sees whoever is John in that world.



#### Derivation with subject quantifier

Every student sleeps
- sleeps ⇝ λwₛ λxₛₑ . SLEEP(w)(x(w))
- student ⇝ λwₛ λxₛₑ . STUDENT(w)(x(w))
- Every ⇝ λwₛ λP<sub><s, et></sub> λQ<sub><s, et></sub> ∀x [P(v)(λu.x) → Q(v)(λu.x)]
- Every student ⇝ λvₛ . ⧙every⧘(v) (⧙student⧘)
  - λv (λw λP λQ ∀x [P(v)(λu.x) → Q(v)(λu.x)])(v) (λu λy. STUDENT(u)(y(u)))
  - λv (λP λQ ∀x [P(v)(λu.x) → Q(v)(λu.x)]) (λu λy. STUDENT(u)(y(u)))
  - λv (λQ ∀x [((λu λy.STUDENT(u)(y(u))))(v)(λu.x) → Q(v)(λu.x)])
  - λv (λQ ∀x [(λy.STUDENT(v)(y(v)))(λu.x) → Q(v)(λu.x)])
  - λv (λQ ∀x [STUDENT(v)(λu.x (v)) → Q(v)(λu.x)])
  - λv (λQ ∀x [STUDENT(v)(x) → Q(v)(λu.x)])
- Every student sleeps ⇝ λuₛ . ⧙every student⧘(u) (⧙sleeps⧘)
  - λu (λv λQ ∀x [STUDENT(v)(x) → Q(v)(λv.x)]) (u) (λw λy . SLEEP(w)(y(w)))
  - λu (λQ ∀x [STUDENT(u)(x) → Q(u)(λv.x)]) (λw λy . SLEEP(w)(y(w)))
  - λu (∀x [STUDENT(u)(x) → (λw λy . SLEEP(w)(y(w)))(u)(λv.x)])
  - λu (∀x [STUDENT(u)(x) → (λy . SLEEP(u)(y(u)))(λv.x)])
  - λu (∀x [STUDENT(u)(x) → SLEEP(u)(λv.x(u))])
  - λu (∀x [STUDENT(u)(x) → SLEEP(u)(x)])

The set of worlds where everything that is a student (in that world) sleeps.


#### Derivation with object quantifier

John sees every student

- sees ~> (λwₛ λyₛₑ λxₛₑ . SEE(w)(x(w), y(w)))
- every student ~> λv (λQ ∀x [STUDENT(v)(x) → Q(v)(λu.x)])(w)
- sees every student ~> λwₛ . ⧙every student⧘(w) (⧙sees⧘)
  - λw (λv (λQ ∀x [STUDENT(v)(x) → Q(v)(λu.x)])(w)) (λvₛ λyₛₑ λxₛₑ . SEE(v)(x(v), y(v)))
  - λw (λQ ∀x [STUDENT(w)(x) → Q(w)(λu.x)]) (λvₛ λyₛₑ λxₛₑ . SEE(v)(x(v), y(v)))
  - TYPE MISMATCH: function wants a Q of type <s, <e, t>>, argument is of type <s, <<e, t>, <<e, t>, t>>>


[remainder to be done in class]



### 2. The derivation of de-re/de-dicto ambiguity

>
> - The Governor still believes in Santa Claus.
> - Ponce de León hoped to find the fountain of youth.
> 
> [...]
> Frege pointed out that when we substitute one co-referential expression for another in the complement clause of a propositional attitude verb, the truth value  of the sentence as a whole can be affected.
> 
> - Mary does not know [that Samuel Clemens is Mark Twain].
> - ? Mary does not know [that Samuel Clemens is Samuel Clemens].

Main take-away: expressions like believe, hope, seek should have access to the _intensions_ of their complements.

> - The Dean believes that I am collaborating with a famous linguist.

De-re/de-dicto: the de-dicto reading seems to involve the _intension_ of 'a famous linguist', de-re is about its _extension_.


#### Derivation with propositional attitude verb 'believe'

Susie believes John sleeps.

[to be done in class]





-----

### Postparation (do this after class; around 3 hours)

(Nothing to submit this week.)

1. **Extra lambda exercises.** tbd.
2. **Practice derivations.** Compositionally derive logical translations for the following sentences, ideally without looking at the class notes (unless you remain stuck for a while). Define adequate lexical entries as required.
  1.  tbd.
3. **Chapter 3.** Read chapter 13 about modeling compositionality.