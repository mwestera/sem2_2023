
## 🏛 Class 2 (14-02-2023): De-re and de-dicto ambiguity (1/2)

### Topics:
- De-re, de-dicto ambiguity.
- Extensional semantics (recap from Semantics 1).
- Developing an _intensional_ semantics.

----

## Class notes:

### 1. De-re, de-dicto

[Homework discussion, & building an intuitive account]


### 2. Extensional semantics

The following is a recap from semantics 1, slightly more formal:

#### Indirect interpretation

For a natural language structure α, its logical translation τ and its interpretation A on a model:

- translation: α ⇝ τ, 
  - and for convenience we can also agree to write: ⧙α⧘ = τ
- interpretation: ⟦τ⟧ = A (e.g., true, false, (set of) entities, etc.)

***Note:*** The book doesn't always keep these two steps consistently separated, e.g., it will mix the intermediate, logical language with the (final) meta-language of English + set theory, and also mix the logical language with the object language (e.g., apply ⟦...⟧ to both).

#### Example fragment in extensional semantics

Translation rules:
- sleep ⇝ λx SLEEP(x)   (equivalent to simply SLEEP)
- kiss ⇝ λx λy KISS(y, x)
- John ⇝ john
- every ⇝ λP λQ ∀x [P(x) → Q(x)]
- **Composition:** For a composite natural language expression 'α β', possible translations are ⧙α⧘(⧙β⧘) or ⧙β⧘(⧙α⧘)

(Typically only one of these will result in a well-formed formula. Why?)

Interpretation rules:
- ⟦john⟧ = the entity john
- ⟦SLEEP⟧ = the set of sleeping entities
- ⟦KISS⟧ = the set _pairs_ of entities where the first kisses the second.
- ...plus the interpretation rules for logical symbols, composition etc.

What else do we need?
- Syntactic assumptions, possible (covert) movement... We return to this later.

**_Note:_** First-order predicate logic, strictly speaking, allows no quantification over predicates yet (hence 'first-order'), but we did this anyway (e.g., λP). We silently shifted to a higher-order predicate logic.

#### Types

What types of things do we need in our models (in _extensional_ semantics):
- e: entities
- t: truth values
- <e,t>: mapping from entities to truth values (e.g. intransitive verbs)
- <e,<e,t>>: mapping from entities to unary predicates (e.g., transitive verbs)

It can help to explicate the _types_ of our various logical expressions, especially variables, e.g.:

- sleep ⇝ λxₑ SLEEP(x)
- kiss ⇝ λxₑ λyₑ KISS(y, x)
- John ⇝ john
- every ⇝ λP<sub><e,t></sub> λQ<sub><e,t></sub> ∀xₑ [P(x) → Q(x)]

**_Note:_** Sets and their characteristic functions: 
- The _characteristic function of a set_ is that function which maps each element in the set to TRUE, and each element that is not in the set to FALSE.
- Hence, we can conceive of sets as functions to truth values, and vice versa.


### 3. Intensional semantics

Thus far we modeled only denotation, not sense:

> [Frege] used the German term Sinn (English sense) for those aspects of meaning which do not depend on the context of use, the kind of meaning we might look up in a dictionary

> One crucial difference between sense and reference is that reference depends on the current situation under discussion, or universe of discourse, whereas senses are stable across situations.

Why should we care about senses? Why might we define our compositional semantics at the level of senses?


#### How to formalize senses (= intensions)

> For each situation, the sense determines a denotation set, and knowing the sense of the word allows speakers to identify the members of this set.

**_Idea:_** let's add _situations_ to our logic/models, and replace all denotations by _a function from situations to denotations_.

Common term for situations: _possible worlds_ 🤯

We add the situation/world type _s_ to our ontology (se we have _e_, _s_ and _t_). Example: 
- _sleep_ ⇝ λwₛ λxₑ SLEEP(w)(x)
- ⟦λwₛ λxₑ SLEEP(w)(x)⟧ = Function that takes a world (w) and returns a function from entities to truth values (i.e., a unary predicate). The latter takes an entity (x), and returns True if the entity is in the denotation of SLEEP in that world.

**Some types:**
- e: entities
- s: worlds ('situations')
- t: truth values
- <e, t>: mapping from entities to truth values (i.e., set of entities), a 'predicate'.
- <s, <e, t>>: mapping each world to a mapping from entities to truth values (i.e., a set of entities per world), a 'property'.
- <e, <e, t>>: mapping each entity to a mapping from entities to truth values
- <s, t>: mapping from worlds to truth values (i.e., a set of worlds), a 'proposition'.
- ... 

**Terminology:** _extension_ is denotation, _intension_ is a function from worlds to denotations, \approx sense.

Could such a 'possible worlds' approach to senses-as-intensions account for this:

> [...] two expressions which have different senses may have the same denotation in certain situations. However, two expressions  that have the same sense (i.e., synonymous expressions) must always have the same denotation in any possible situation. 

And this?

> Frege’s distinction allows us to see that non-referring expressions like those in (11) may not have a referent, but they do have a sense, and that sense is derived in a predictable way by the normal rules of the language.
> 
> (11) a. the present King of France [...]


#### A fragment in intensional semantics

[on whiteboard; will be in class notes for next week]


----

### Preparation (do this before class; around 30 minutes)

1. **De-re/de-dicto.** Explain in your own words, with the help of an example, what the de-re/de-dicto ambiguity is. If necessary, review section 12.5 in the textbook from last week's 'postparation'.

-----

### Postparation (do this after class; around 3 hours)

1. **Class summary.** Try to summarize, from memory and with the help of your class notes, what we discussed in class. What is the idea behind adding possible worlds to our toolbox? Why did we need to replace function application by an intensional variant (illustrate with an example derivation!)? What is the possible relation between de-re/de-dicto ambiguity and quantifier scope?
2. **Propositions.** The intension of a sentence, according to intensional semantics, would be a _proposition_, i.e., a set of worlds (type: <s, t>). Do you think that this corresponds to the Fregean idea that the denotation of a sentence is its truth value, and the sense of a sentence is the _thought_ it expresses? If not, which aspects of a 'thought' do you believe are not adequately captured by a set of worlds, or vice versa? Reflect critically, also on the nature/role of possible worlds in this approach.
3. **Evidence.** Suppose the mechanism responsible for quantifier scope ambiguity is quantifier raising -- a form of (covert) movement. Given what you know about movement on the syntax side, what would constitute evidence for a quantifier scope analysis of the de-re/de-dicto ambiguity? And what would constitute evidence against? Can you come up with concrete, linguistic examples?
4. **Referential and quantificational indefinites.** Study the classic paper [Fodor and Sag 1982](https://www.jstor.org/stable/25001100) sections 1-3. In case you cannot access the link, I have uploaded the PDF to Brightspace.
5. **Linguistic examples.** For each of the linguistic examples in the paper (sections 1-3), write down what the authors intend it to demonstrate. In each case, do you believe the example is convincing in this regard?
6. **Summary of the paper _([📩 submit by 17-02-2023](https://brightspace.universiteitleiden.nl/d2l/le/lessons/210127/units/2292941))_.** Write a precise, academically written summary of the paper (sections 1-3), of 10 medium-sized sentences. A good summary should make clear what the author's aim is for the paper (what the authors aim to demonstrate) and what their core observations and arguments are.
7. **Semantics/pragmatics.** What role does the semantics/pragmatics distinction play in the paper? Consider both its role in the paper's overall aims, and its role in the authors' assessment of the various pieces of evidence in section 2.