# Compiling Contextual Behavior from Explicit Character Attributes and Measured Relationships

**Nathan / Nate Soundz**  
**Compiled Intelligence Research**  
**September 2026**

## Abstract

This work investigates whether useful contextual behavior can be constructed directly from explicit symbol structure and measured relationships rather than learned exclusively through conventional gradient-based next-token training.

The current experimental domain is the 95 printable ASCII characters. Each character is associated with an explicit binary attribute description, and the active research line uses a 254-dimensional recovered attribute inventory. The source character at each analyzed position is already known. The task is therefore not ordinary next-character prediction. Instead, the research asks whether contextual evidence can determine how attributes should be weighted, strengthened, weakened, and transformed so that a numerical model state reflects the known occurrence correctly relative to all competing characters.

The experimental program proceeds by preserving independent analyses rather than collapsing them into one score. These include static structural distance, ranked per-position attribute evidence, co-occurrence-derived contextual support, target-specific mismatch analysis, bidirectional conditional relationships, character-specific context radius, context-character hierarchy, cross-analysis correspondence, and named context attribution.

Several results have been established. The 95-character attribute substrate is structurally distinguishable. A repaired causal attention → residual → compiled ReLU feed-forward control exactly realizes all 9,025 ordered two-character contexts of a historical order-2 model without gradient descent. A first covariance-based contextual bridge was falsified by infeasibility. A later co-occurrence-derived compiler mapped measured 0..1 contextual relationships directly onto positive attention allocation and reached 97.43% correct target reconstruction on the current 2,729-position analysis corpus before reaching a stable residual. All baseline errors fell within the structurally nearest-10 competitor set. Cross-analysis results show that broad contextual support and exact target-versus-competitor discrimination are distinct. Named context attribution further localizes which context character, relative lag, and distinguishing attribute pushes a target toward or away from a specific competitor.

The present work does not claim general language intelligence, broad generalization, or a complete replacement for conventional learning. Its current result is narrower: explicit symbolic attributes, empirical contextual relationships, attention-scale allocation, residual-state transformation, and deterministic feed-forward correction can be connected into an executable research program whose successes and failures remain inspectable at each stage.

---

## 1. Research question

The governing question is:

> Can contextual model behavior be compiled from explicit, measurable relationships between known symbols and their attributes?

The project deliberately distinguishes this question from ordinary prediction.

For an analyzed text position, the source text already supplies the correct character. The compiler is therefore not asked to guess which character occurred. It is asked to analyze why that occurrence is numerically compatible with its context and how that information should be represented in model state.

The high-level process is:

```
known occurrence
    ↓
explicit character attributes
    ↓
contextual measurements
    ↓
ranked attribute evidence
    ↓
attention allocation
    ↓
residual transformation
    ↓
feed-forward consequence
    ↓
comparison against all alternative characters
```

The intended result is a model whose internal numerical organization is constructed from known relationships rather than obtained only by minimizing a prediction loss.

---

## 2. Experimental substrate

### 2.1 Vocabulary

The present domain is the complete set of 95 printable ASCII characters:

```
ASCII 32 ... ASCII 126
```

Each character has a stable token identity.

### 2.2 Attribute representation

The current active line uses 254 binary character attributes.

These dimensions encode multiple kinds of structure, including:

- broad character class;
- orthographic properties;
- vowel and consonant eligibility;
- glyph and shape properties;
- numeric structure;
- punctuation and operator behavior;
- contextual and inference-related properties.

The binary matrix has shape:

[
A in {0,1}^{95 	imes 254}.
]

All 95 rows are distinct.

The minimum non-self Hamming distance is 1, which is sufficient to establish that no two printable characters share an identical 254-dimensional row.

A signed representation is:

[
X = 2A - 1.
]

Under this signed form, each token ranks itself above every other token under the static identity score.

This establishes a structural substrate. It does not establish contextual behavior.

---

## 3. Why known ground truth is intentional

Conventional supervised next-token training typically presents a context and asks the model to increase the score of a target token.

This project uses a different construction.

At each analyzed source position:

1. the character occurrence is already known;
2. its complete attribute membership is known;
3. the competing 94 characters are known;
4. the context surrounding the occurrence is known;
5. the compiler measures how the context supports or suppresses the attributes that distinguish the correct character from competitors.

Thus the fundamental object is not:

[
P(y mid x)
]

as an unknown target to be learned.

Instead, the compiler works from a known occurrence (y) and asks:

[
	ext{What measured contextual structure explains and numerically supports } y
	ext{ relative to its competitors?}
]

This distinction is central to the project.

---

## 4. Historical executable control

An earlier count-derived model compiled ordered two-character contexts into continuation statistics.

The initial executable implementation was later audited and found to use a direct continuation lookup even though attention was discussed conceptually.

A repaired implementation replaced that shortcut with an explicit computational path:

[
	ext{embedding}
ightarrow
	ext{causal attention}
ightarrow
	ext{residual}
ightarrow
	ext{compiled ReLU FFN}
ightarrow
	ext{output head}.
]

The repaired construction used two fixed positional attention heads whose linear combination reconstructed the previous token embedding exactly.

A ReLU detector was then constructed for every ordered pair.

For signed token embeddings (e_a,e_b), the pair detector has the form:

[
g_{ij}(e_a,e_b)
=
operatorname{ReLU}
left(
rac{
e_a^	op e_i + e_b^	op e_j - C + delta
}{delta}
ight),
]

where (C) is the matching self-score constant and (delta) is the verified identity margin.

Across all:

[
95^2 = 9{,}025
]

ordered pairs:

- the correct detector activates exactly;
- nonmatching detectors remain inactive;
- the continuation path depends on attention;
- ablation of attention destroys the detector input.

This was an important control because it established that the desired causal path could be made physically executable rather than described only symbolically.

It did **not** establish general language intelligence. The construction still represented an exact order-2 mapping.

---

## 5. Context-width collision audit

The order-2 control also exposed a hard limitation.

If identical causal histories demand different continuations, a deterministic order-2 state cannot satisfy all occurrences simultaneously.

On the 31-example active corpus:

| context width | best deterministic upper bound |
|---:|---:|
| 1 | 33.3580% |
| 2 | 57.0304% |
| 3 | 78.8316% |
| 4 | 89.7121% |
| 5 | 93.2842% |
| 6 | 95.2119% |
| 7 | 96.8663% |

This table is not a performance claim for a trained model. It is a collision audit showing how much ambiguity remains when the state is restricted to a literal context width.

The result motivated richer context analysis rather than simply increasing numerical magnitude.

---

## 6. First contextual bridge: a negative result

A first confirmatory attempt used raw relative-position attribute covariance.

The declared path was:

[
	ext{raw co-occurrence counts}
ightarrow
	ext{attribute covariance}
ightarrow
	ext{additive contextual support}
ightarrow
	ext{fixed signed token geometry}.
]

No smoothing was used.

The constraint universe contained more than half a million target-versus-competitor inequalities.

A first subset of constraints could be made feasible.

When additional violated constraints were introduced, the system became infeasible even after the numerical magnitude bound was removed.

Therefore the failure was not:

> the weights need to be larger.

It was:

> this contextual equation cannot satisfy the requested occurrence relationships simultaneously.

That result was retained.

It localized the missing mechanism to occurrence-specific state transformation rather than static token identity.

---

## 7. Co-occurrence as attention-scale evidence

A later experiment used a more direct observation.

For a context character (c), target character (y), and relative lag (d), measured conditional support is already a value on a 0..1 scale:

[
P(y mid c,d).
]

Projecting target characters through the binary attribute matrix gives:

[
P(A_k=1 mid c,d).
]

These probabilities can therefore be interpreted as positive contextual support for target attributes.

For the visible positions of a particular occurrence, a relevance value (r_j) is computed.

The attention allocation is:

[
alpha_j
=
rac{r_j}{sum_ell r_ell}.
]

For positive (r_j), this is equivalent to:

[
alpha_j
=
operatorname{softmax}(log r_j).
]

No arbitrary attention-strength scale is required between the measured co-occurrence relationship and positive attention allocation.

This is one of the central mechanical connections in the current research.

---

## 8. Positional ranked-attribute analysis

The active corpus currently contains:

- 31 source examples;
- 2,729 character positions;
- all 95 printable ASCII targets.

For each known source position, the compiler constructs exactly one ranked 254-attribute profile.

The known target's active dimensions are compared with inactive dimensions.

Across:

[
22{,}814{,}599
]

explicit active-versus-inactive comparisons, the measured ranking agreement was:

[
96.2455925699%.
]

The top-(|A_y|) overlap with the target's active attribute set was:

[
79.4083563731%.
]

These measurements are not treated as proof of semantic understanding.

They establish that the contextual statistics strongly recover the known target's active attribute structure while retaining identifiable failure modes.

---

## 9. Attention movement and residual transformation

The compiled token geometry is character-specific:

[
E[c,k].
]

The attention-stage state for a known target is written as:

[
h_A
=
E_y odot 	ext{attention_profile}.
]

This permits context to weaken or preserve dimensions that belong structurally to the target.

The mean L1 attention displacement in the first complete run was approximately:

[
6.9515.
]

Decoder taps showed:

- before attention, the known target reconstructs trivially at 100%;
- after raw attention alone, target argmax falls to 24.51%;
- mean target rank after attention is approximately 4.63.

This is important because attention is not acting as a decorative component. It produces a large measurable state movement.

The raw attention state alone is not sufficient.

---

## 10. Deterministic feed-forward consequence compilation

The next stage compiles correction pressure from observed mismatch.

When a transformed occurrence decodes to the wrong competitor, only dimensions that distinguish the known target from that competitor contribute corrective evidence.

No gradient descent is used in this compiler.

The correction sequence was:

| iteration | correct target | failures |
|---:|---:|---:|
| 0 | 94.2836% | 156 |
| 1 | 96.5555% | 94 |
| 2 | 96.8120% | 87 |
| 3 | 96.9219% | 84 |
| 4 | 97.1418% | 78 |
| 5 | 97.2884% | 74 |
| 6 | 97.3617% | 72 |
| 7 | **97.43496%** | **70** |
| 8 | 97.43496% | 70 |

The process stopped when an additional pass produced no improvement.

The stable residual failures were concentrated in a small number of relationships:

- (p ightarrow P)
- (f ightarrow F)
- (W ightarrow Y)
- (H ightarrow F)
- (N ightarrow M)

The failure concentration became the next object of analysis.

---

## 11. Static neighborhoods and failure localization

The static 254-dimensional substrate was independently analyzed through Hamming neighborhoods.

For every target, the ten structurally closest competitors were retained as the **near-10** set.

In the baseline mismatch analysis:

- near-10 failures: 156;
- middle-74 failures: 0;
- far-10 failures: 0.

Therefore:

[
P(	ext{near10} mid 	ext{failure}) = 1.
]

However, exact Hamming magnitude within the close-neighbor region correlated only weakly with failure rate.

This means:

- structural closeness is highly informative about where ambiguity lives;
- structural distance alone is not enough to resolve which close competitor will win.

That distinction motivated more contextual analyses.

---

## 12. Multiple analyses are preserved independently

A central methodological rule of the project is that a new analysis does not overwrite an earlier one.

The current research keeps separate evidence streams including:

- static structural similarity;
- positional attribute ranking;
- co-occurrence support;
- target-specific mismatch;
- bidirectional conditionals;
- target-specific useful context radius;
- context-character hierarchy;
- cross-analysis correspondence;
- named context attribution.

This makes disagreement measurable.

The intended direction is not to collapse everything immediately into one scalar.

Instead, the system asks how one analysis corresponds to another.

---

## 13. Cross-analysis correspondence

A later analysis compared several independent evidence streams over the same 31-example corpus.

Selected results include:

### Contextual support vs attribute ranking

Spearman correlation:

[
ho approx +0.8915.
]

Broad co-occurrence support strongly corresponds to better active-versus-inactive attribute ordering.

### Forward conditional vs context hierarchy

Across 1,244 target/context relationships:

[
ho approx +0.6646.
]

Thus context characters that strongly support a target under the forward conditional tend also to rank highly in the independently constructed context hierarchy.

### Raw support count vs contextual authority

Spearman correlation:

[
ho approx +0.0728.
]

This is near zero.

Raw frequency is therefore not equivalent to contextual importance.

### Static distance vs failure

Correlations were weak.

Structural closeness identifies the relevant competitor region, but fine contextual discrimination requires additional information.

---

## 14. Character-specific context radius

The project also tested how analysis quality changes as context radius grows independently for each target character.

The useful-radius distribution was:

| radius | target characters |
|---:|---:|
| 1 | 40 |
| 2 | 38 |
| 3 | 12 |
| 4 | 4 |
| 5 | 0 |
| 6 | 0 |
| 7 | 1 |

The aggregate score peaks around radius 2, but individual characters differ.

This argues against imposing one universal context radius on every character.

---

## 15. Named context attribution

The most specific current analysis operates on:

[
(y,c,d)
]

where:

- (y) is the known target character;
- (c) is a context character;
- (d) is relative position.

For each relation, the analysis measures:

[
P(y mid c,d),
]

[
P(c mid y,d),
]

and an attribute shift:

[
Delta_{y,c,d,k}
=
P(A_k=1 mid c,d)
-
	ext{baseline}_{y,k}.
]

The shift is then intersected with dimensions that distinguish (y) from one of its near structural competitors.

This allows the analysis to state not merely:

> context helps.

It can state:

> this specific context character at this specific relative lag raises or lowers these specific dimensions that distinguish this target from this competitor.

Examples in the current corpus include the recurring distinctions:

- lowercase (p) versus uppercase (P);
- lowercase (u) versus uppercase (U);
- (W) versus (Y);
- (H) versus (F);
- (N) versus (M).

This moves the project from generic contextual support toward named causal candidates for state transformation.

---

## 16. First named-context compiler condition

The named-context analysis was applied as a separate compiler condition rather than replacing the earlier compiler.

Baseline:

[
94.2836%
]

with 156 failures.

Named-context condition:

[
95.1631%
]

with 132 failures.

The net change was:

- 37 previously wrong positions repaired;
- 13 previously correct positions damaged;
- 119 positions remained wrong with the **same wrong competitor**;
- zero positions changed from one wrong competitor to another wrong competitor.

This is a particularly informative result.

The added contextual signal was not randomly reshuffling errors.

It repaired some exact relationships, harmed others, and left a stable unresolved competitor identity elsewhere.

That creates three new evidence classes:

1. contextual repairs;
2. persistent ambiguities;
3. context-induced regressions.

The next analysis can compare those three groups directly.

---

## 17. What has not been established

The current work does **not** establish:

- general natural-language intelligence;
- broad out-of-distribution generalization;
- parity with large pretrained language models;
- a complete transformer replacement;
- a universal theory of representation;
- that all useful learning can be replaced by compilation;
- that the current 254 attributes are sufficient for arbitrary language.

The current corpus is deliberately small and diagnostic.

Several experiments are intentionally in-sample because their purpose is to test whether the requested numerical mechanism can be constructed from known evidence.

Generalization must be tested separately.

---

## 18. Why preserve negative results

This project treats failed hypotheses as part of the model-development record.

For example:

- a phonetic attribute bridge did not establish robust withheld-context generalization;
- a covariance-based contextual bridge became infeasible;
- two-character context was provably insufficient for the full current curriculum;
- raw co-occurrence attention strongly moved state but degraded target decoding before later correction;
- named-context application repaired some occurrences while introducing others.

Removing these results would destroy information about the mechanism.

The project therefore uses an append-only experimental philosophy:

[
	ext{analysis}_1,
	ext{analysis}_2,
dots,
	ext{analysis}_n
]

remain available for comparison rather than being silently rewritten into one historical narrative.

---

## 19. Current research direction

The immediate research problem is no longer simply:

> Which attributes are important?

It is more specific:

> Under which exact target/context/lag/competitor conditions should a measured attribute shift be allowed to alter model state?

The next layer of analysis is therefore expected to compare:

- contexts associated with successful repair;
- contexts associated with persistent ambiguity;
- contexts associated with harmful overcorrection.

The goal is a selective state-transition rule derived from observed relationships rather than an unconditional global correction.

---

## 20. Broader hypothesis

The broader hypothesis is that useful computational behavior may be assembled from a hierarchy of explicit relational evidence:

[
	ext{identity}
ightarrow
	ext{attributes}
ightarrow
	ext{co-occurrence}
ightarrow
	ext{conditional structure}
ightarrow
	ext{context attribution}
ightarrow
	ext{state transformation}
ightarrow
	ext{procedure}.
]

If this holds beyond the present domain, it suggests an alternative research path in which part of what is ordinarily acquired through optimization may instead be explicitly measured, compiled, audited, and revised.

That remains a hypothesis.

The present work is intended to make that hypothesis experimentally inspectable.

---

## 21. Reproducibility and access boundary

The active working laboratory is private.

This public paper reports selected measurements and mechanisms that have been executed in the private research environment.

The public repository is not currently intended to contain the complete executable laboratory, internal datasets, or every historical artifact.

Interested researchers may request further information or discuss independent reproduction.

---

## 22. How to get involved

If this work overlaps with your interests in:

- alternative model construction;
- interpretable numerical representations;
- deterministic or analytical weight compilation;
- attention and residual-state analysis;
- character or symbolic representations;
- mechanistic interpretability;
- explicit procedural memory;
- nonstandard learning systems;
- experimental replication or falsification;

open an issue in this repository titled:

```
Research Interest
```

Include what part of the work interests you and whether you want to:

- discuss the research;
- critique a mechanism;
- independently reproduce an experiment;
- contribute an analysis;
- propose a discriminating experiment;
- ask about participating in the private research effort.

Participation and private repository access are not automatic and are considered individually.

---

## 23. Conclusion

The current experimental record supports a narrower but concrete conclusion.

Explicit character attributes and measured contextual relationships can be connected to real numerical model operations:

[
	ext{measured context}
ightarrow
	ext{attention allocation}
ightarrow
	ext{state movement}
ightarrow
	ext{feed-forward correction}
ightarrow
	ext{auditable competitor discrimination}.
]

The process can be executed without ordinary gradient descent, and its failures remain sufficiently localized to become subsequent objects of analysis.

Whether this construction scales into a substantially more capable form of compiled intelligence remains unanswered.

That unanswered question is the purpose of the continuing work.
