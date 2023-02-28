
## 🏛 Class 3 (21-02-2023): Intensional semantics (2/3) 

### Topics:
1. Formal fragment of intensional semantics.
2. Challenges & open questions


----

### Preparation (do this before class; around 20 minutes)

1. **Homework review.** Review your own homework from last time.


----


## Class notes:

Note: for readability we changed ⧙α⧘ into ❴α❵ (signifying: the translation of the syntactic node α). 

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
- For a syntactic node with expressions α and β as children, a candidate translation is: ❴α❵(❴β❵)

**Intensional function application:**
- For a syntactic node with expressions α and β as children, a candidate translation is: λw ❴α❵(w)(❴β❵)

> Q: why not apply β to world w too?


#### Derivation with intransitive verb 'sleep'

John sleeps.

- sleeps ⇝ λwₛ λxₛₑ . SLEEP(w)(x(w))
- John ⇝ λwₛ. john(w)
- John sleeps ⇝ λv . ❴sleeps❵(v)(❴John❵)
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
- sees John ⇝ λuₛ . ❴sees❵(u)(❴John❵)
  - λu (λwₛ λyₛₑ λxₛₑ . SEE(w)(x(w), y(w)))(u) (λv. john(v))
  - λu (λyₛₑ λxₛₑ . SEE(u)(x(u), y(u))) (λv. john(v))
  - λu (λxₛₑ . SEE(u)(x(u), (λv. john(v))(u)))
  - λu λxₛₑ . SEE(u)(x(u), john(u))
- Susie sees John ⇝ λwₛ . ❴sees John❵(w)(❴susie❵) 
  - λw . (λuₛ λxₛₑ . SEE(u)(x(u), john(u)))(w) (λv. susie(v))
  - λw . (λxₛₑ . SEE(w)(x(w), john(w))) (λv. susie(v))
  - λw . (SEE(w)((λv. susie(v))(w), john(w)))
  - λw . SEE(w)(susie(w), john(w)) 

So: the set of worlds in which whoever is Susie in that world, sees whoever is John in that world.



#### Derivation with subject quantifier

Every student sleeps
- sleeps ⇝ λwₛ λxₛₑ . SLEEP(w)(x(w))
- student ⇝ λwₛ λxₛₑ . STUDENT(w)(x(w))
- Every ⇝ λwₛ λP<sub><s, <<s, e>, t></sub> λQ<sub><s, <<s, e>, t></sub> ∀x [P(v)(λu.x) → Q(v)(λu.x)]
- Every student ⇝ λvₛ . ❴every❵(v) (❴student❵)
  - λv (λw λP λQ ∀x [P(v)(λu.x) → Q(v)(λu.x)])(v) (λu λy. STUDENT(u)(y(u)))
  - λv (λP λQ ∀x [P(v)(λu.x) → Q(v)(λu.x)]) (λu λy. STUDENT(u)(y(u)))
  - λv (λQ ∀x [((λu λy.STUDENT(u)(y(u))))(v)(λu.x) → Q(v)(λu.x)])
  - λv (λQ ∀x [(λy.STUDENT(v)(y(v)))(λu.x) → Q(v)(λu.x)])
  - λv (λQ ∀x [STUDENT(v)(λu.x (v)) → Q(v)(λu.x)])
  - λv (λQ ∀x [STUDENT(v)(x) → Q(v)(λu.x)])
- Every student sleeps ⇝ λuₛ . ❴every student❵(u) (❴sleeps❵)
  - λu (λv λQ ∀x [STUDENT(v)(x) → Q(v)(λv.x)]) (u) (λw λy . SLEEP(w)(y(w)))
  - λu (λQ ∀x [STUDENT(u)(x) → Q(u)(λv.x)]) (λw λy . SLEEP(w)(y(w)))
  - λu (∀x [STUDENT(u)(x) → (λw λy . SLEEP(w)(y(w)))(u)(λv.x)])
  - λu (∀x [STUDENT(u)(x) → (λy . SLEEP(u)(y(u)))(λv.x)])
  - λu (∀x [STUDENT(u)(x) → SLEEP(u)(λv.x(u))])
  - λu (∀x [STUDENT(u)(x) → SLEEP(u)(x)])

The set of worlds where everything that is a student (in that world) sleeps.


#### Preview of the treatment of beliefs

Basic idea: belief can be modeled as a relation between an individual's 'belief worlds' (the worlds they consider possible) and a proposition (= also a set of worlds).


-----

### Postparation (do this after class; around 3 hours)

(Nothing to submit this week.)

1. **Types.** For each of the following types, initially without looking at the notes above, (i) try to unambiguously describe the type in English (a function from...), and (ii) can you think of a class of natural language expressions whose _intension_ or _extension_ (indicate which!) would conceivably be of that type?  
   1. <s, t>
   2. <s, <<s, e>, t>
   3. t
   4. <<<s, e>, t>, <<s, e>, t>> 
   5. <t, <t, t>>
   6. e
   7. <e, e>
   8. <s, <<s, e>, <s, e>>>
   9. <s, <<s, <<s, e>, t>>, t>>
   10. <<s, e>, t>
   11. <<s, e>, <<s, e>, t>>
   12. <t, t>
   13. <<s, <<s, e>, t>>, <<s, <<s, e>, t>>, t>>
2. **Function/set duality.** Which of the above types can be equivalently described as a _function_ and as a _set_? For those, give the latter type of paraphrase.
3. **Function application.** Which of the following pairs of types can be combined with _extensional_ function application (see last week)? Which can be combined with _intensional_ function application? In each case where combination is possible (whether extensional or intensional), indicate the type of the resulting expression. 
   1. <s, <<s, e>, t>> with <e, t>
   2. <e, t> with <s, e>
   3. e with <<e, t>, t>
   4. <s, e> with <e, t> 
   5. <e, <e, <e, t>>> with e
   6. <e, <e, <e, t>>> with <e, e>
   7. <s, e> with <<s, e>, t>
   8. <s, <<s, <<s, e>, t>>, t>> with <s, <<s, e>, t>>
4. **Chapter 13 and section 15.6.** Read chapter 13 about modeling compositionality, and the short section 15.6 in chapter 15, about lambdas.
5. **Sloppiness in chapter 13.** Can you identify points in the chapter where the author is not entirely consistent in their use of logic? Can you find places where the intermediate logical language (as used in 'indirect interpretation') is mixed with the metalanguage of set theory + English? (How would you reformulate these points/examples/definitions to maintain a clearer separation?) 
6. **Practice derivations.** Compositionally derive logical translations for the following sentences, ideally without looking at the class notes (unless you remain stuck for a while). Specify adequate lexical entries as required.
   1. Alan sleeps.
   2. Susie kisses Alan.
   3. A student sleeps.
7. **Extending the fragment with adverbs.** ⭐⭐ Let's assume adjectives combine with a noun to form a noun phrase, and then with a determiner to form a determiner phrase. Note that adjectives are optional; moreover, note that we can in principle insert any number of adjectives without affecting the way the (modified) noun composes higher up. Given this, and taking note of the type we have been assigning to nouns so far (e.g. 'student'), what might be a possible type for an adjective? Try to illustrate your potential solution with a compositional translation of a phrase like 'tall student'.