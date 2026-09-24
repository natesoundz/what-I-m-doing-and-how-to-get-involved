# What I'm Doing and How to Get Involved

I am exploring whether useful machine intelligence can be **compiled from explicit structure, measured relationships, and deterministic transformations**, rather than relying exclusively on ordinary gradient-trained prediction.

The working research repository is private. This public repository exists to explain the work, publish formal writeups and verified results, and give interested researchers a way to contact me.

## Current research direction

The current work uses a deliberately small, inspectable domain: the 95 printable ASCII characters.

Each character is represented through an explicit attribute system. The present active line uses 254 recovered character attributes covering structural, orthographic, phonetic, shape, numeric, punctuation, operator, and contextual properties.

The central question is not simply:

> Can a model predict the next character?

It is:

> Can contextual behavior be constructed from measured relationships between known symbols and their attributes, then compiled directly into attention, residual-state transformations, and feed-forward behavior?

The current pipeline studies:

```
known text
    ↓
per-position attribute analysis
    ↓
co-occurrence and conditional relationships
    ↓
context-specific attribute evidence
    ↓
attention-scale allocation
    ↓
residual-state transformation
    ↓
feed-forward correction / consequence
    ↓
full competitor audit
```

Ordinary gradient descent is not the default compiler. When gradients are used, they are treated as diagnostics unless an experiment explicitly declares otherwise.

## Why this is different

The project deliberately separates:

- **known ground truth** from prediction;
- **analysis** from compilation;
- **static token structure** from occurrence-specific context;
- **attention** from feed-forward transformation;
- **successful results** from failed hypotheses;
- **historical controls** from active mechanisms.

Negative results are preserved instead of being discarded when a later mechanism works better.

## What has been demonstrated so far

The current research has established several concrete results:

- A 95-character attribute geometry can uniquely distinguish every printable ASCII token.
- A repaired causal attention → residual → compiled ReLU FFN path can exactly realize all 9,025 ordered two-character contexts in the historical order-2 control without gradient training.
- A simple covariance-based contextual bridge was tested and found infeasible; that failure was retained and used to localize the missing mechanism.
- Co-occurrence statistics were mapped directly onto the same 0..1 scale used for positive attention allocation.
- On the current 31-example / 2,729-position analysis corpus, the positional 254-attribute analysis placed active attributes above inactive attributes in approximately **96.25%** of pairwise comparisons.
- The first deterministic co-occurrence/FFN compiler moved the full-path reconstruction from **94.28%** to **97.43%**, then stopped at a stable residual rather than forcing a perfect result.
- Every baseline error in the current analysis fell inside the target character's structurally nearest-10 competitor set.
- Cross-analysis work showed that broad contextual support and fine target/competitor discrimination are related but not identical.
- Named context attribution can identify which exact context character, relative position, and distinguishing attribute pushes a target toward or away from a specific competitor.

These are research results, not claims that the project has solved general intelligence or replaced conventional machine learning.

## Formal paper

The current formal public writeup is here:

**[Compiling Contextual Behavior from Explicit Character Attributes and Measured Relationships](PAPER.md)**

It describes the research question, architecture, experimental lineage, positive results, negative results, current limitations, and next experimental direction.

## Private working laboratory

The active development repository remains private.

This public repository is intentionally not a mirror of the working lab. Internal datasets, intermediate artifacts, experimental branches, and implementation files are not automatically published here.

The purpose of this repository is to make the research understandable without exposing the entire private workspace.

## Interested in the work?

If you are genuinely interested in the research, want to reproduce an idea independently, have a technical criticism, or want to ask about participating:

**Open an issue in this repository titled `Research Interest`.**

Tell me:

- what part of the work interests you;
- what your background or relevant experience is, if applicable;
- whether you want to discuss, reproduce, critique, or contribute;
- what specifically you would like access to or involvement with.

There is no automatic membership or access to the private laboratory. I will decide case by case whether further access or collaboration makes sense.

You do not need credentials or an academic affiliation to ask.

## Research-use boundary

The material in this repository is published for research and discussion only.

See **[LICENSE.md](LICENSE.md)**.

## Author

Nathan / Nate Soundz  
GitHub: **@natesoundz**
