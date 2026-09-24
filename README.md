# What I'm Doing and How to Get Involved

This repository is a public window into the research I am currently working on.

I use it to explain the direction of the work, document selected results, and post important milestones from time to time as the research develops. It is not intended to be a complete copy of my working environment or a public release of the private research laboratory.

If something here interests you and you would like more information, want to discuss the work, or want to ask about getting involved, send me a message or open an issue in this repository.

## Current status — September 24, 2026

The work is active and still developing.

So far, I have built and tested a series of deterministic and analytical experiments around explicit character structure, context, attention, residual-state changes, and feed-forward transformation.

Some of the things established so far include:

- a complete printable-ASCII character representation in which all 95 characters remain distinguishable;
- an executable attention → residual → feed-forward path that can reproduce a fully specified small-context control without ordinary gradient training;
- several independent contextual analyses that can be compared without replacing one another;
- a direct relationship between measured contextual co-occurrence and positive attention-scale allocation;
- measurable improvement when contextual analysis is used to compile corrective state transformations;
- localization of remaining errors to a small set of structurally close competitors rather than arbitrary characters;
- evidence that broad contextual support, structural similarity, exact competitor discrimination, and context-specific attribution are related but distinct signals;
- named context analysis capable of identifying which surrounding character relationships are associated with particular target-versus-competitor distinctions;
- negative results that ruled out several simpler mechanisms and helped identify where additional structure was required.

Where a result has failed, plateaued, or remained incomplete, that has been retained as part of the research record rather than presented as a success.

### What I am working on now

The current work is focused on understanding **when contextual evidence should be allowed to change a model state and when it should not**.

Recent experiments have shown that more specific contextual information can correct some previously unresolved cases, while in other cases it can leave the same ambiguity in place or introduce a new error.

The present objective is therefore to distinguish:

- contextual relationships associated with successful correction;
- relationships associated with persistent ambiguity;
- relationships associated with harmful overcorrection.

The goal is to determine whether those differences can be measured clearly enough to compile a more selective state-transition mechanism.

This remains an active research question.

### If you want to understand how a result was obtained

The public repository intentionally does not expose every implementation detail, private artifact, or working experiment.

If a particular result or milestone interests you and you want to understand **how it was produced**, I am open to considering requests for additional explanation, discussion, or closer research involvement.

Send me a message or open a `Research Interest` issue and identify the specific result or part of the work you want to understand.

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

This repository is primarily here so people can see what I am working on and follow major milestones as they are reached.

I will update it from time to time with further results, clarifications, and important changes in direction.

If the work interests you and you want more information, want to discuss a result, or want to ask about participating, **send me a message or open an issue in this repository**.

You can title the issue:

`Research Interest`

and simply tell me what caught your attention and what you would like to know.

There is no automatic membership or access to the private working laboratory. If closer involvement makes sense, we can discuss it directly.

## Research-use boundary

The material in this repository is published for research and discussion only.

See **[LICENSE.md](LICENSE.md)**.

## Author

Nathan / Nate Soundz  
GitHub: **@natesoundz**
