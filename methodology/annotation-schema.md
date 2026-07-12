---
layout: default
title: Annotation Schema
---

# Annotation Schema

[← Back to Home]({{ site.baseurl }}/)

[← Data Preprocessing]({{ site.baseurl }}/methodology/preprocessing.html)

This page describes the metadata and annotation schema used to classify the
primary studies in the survey *Fuzzing AI Systems: Foundations, Techniques,
and Open Challenges*.

After the final study-selection process, each included study was represented
using both bibliographic metadata and technical annotation fields. The schema
was designed to support the research questions and enable consistent
comparison across different AI-system targets, fuzzing techniques, oracle
mechanisms, and failure types.

## Bibliographic Metadata

The following bibliographic fields were retained for each selected study.

| Field | Description |
|---|---|
| Paper ID | Unique identifier assigned to the study |
| Title | Full title of the publication |
| Authors | Authors listed in the publication |
| Publication year | Year associated with the selected publication version |
| Venue | Conference, journal, workshop, or preprint venue |
| Publisher | Publisher or publication platform |
| DOI | Digital Object Identifier, when available |
| URL | Publisher, repository, or publication link |
| Abstract | Abstract text used during screening and verification |

## Technical Annotation Fields

The technical schema contained 17 fields.

| No. | Annotation field | Purpose |
|---:|---|---|
| 1 | Testing Target | Identifies the direct artifact exercised by the fuzzing approach |
| 2 | System Level | Identifies the AI-system layer at which behavior or failure is observed |
| 3 | AI Paradigm | Records the AI paradigm addressed by the study |
| 4 | Target Framework/Platform | Records the framework, library, compiler, backend, simulator, or platform under test |
| 5 | Technique Name | Records the name of the proposed technique, tool, or fuzzing approach |
| 6 | Technique Family | Classifies the high-level fuzzing or testing mechanism |
| 7 | Input Generation Strategy | Describes how initial test inputs are generated or selected |
| 8 | Mutation Strategy | Describes how existing inputs, programs, models, prompts, or scenarios are transformed |
| 9 | Oracle Type | Identifies the high-level mechanism used to determine whether a failure occurred |
| 10 | Oracle Construction | Describes how the oracle is implemented or derived |
| 11 | Failure Type | Records the type of failure exposed by the approach |
| 12 | Reported Limitations | Captures limitations explicitly reported by the study |
| 13 | Threats to Validity | Records threats to validity discussed by the authors |
| 14 | Future Work | Captures future research directions proposed by the study |
| 15 | Observed Gap | Records gaps identified through evidence-based review |
| 16 | Main Contribution | Summarizes the primary contribution of the study |
| 17 | Notes | Stores supporting evidence, clarification, or annotation comments |

## Main Classification Dimensions

### Testing Target

The testing target identifies the concrete artifact directly exercised by the
fuzzer.

The main categories include:

- **Model**
- **Framework/Library**
- **Compiler/Backend**
- **System-level AI application**

Some studies may span more than one target layer.

### System Level

The system-level field captures the layer at which behavior or failure is
observed.

This distinction is useful because the direct testing target and the level at
which the failure becomes visible are not always identical.

### AI Paradigm

This field records the primary AI paradigm addressed by the study, such as:

- machine learning;
- deep learning;
- reinforcement learning;
- large language models;
- generative AI; or
- agent-based AI systems.

### Target Framework or Platform

This field records the concrete software ecosystem or execution platform
examined by the study.

Examples may include:

- TensorFlow;
- PyTorch;
- Keras;
- TensorFlow.js;
- TVM;
- MLIR;
- ONNX Runtime;
- autonomous-driving simulators;
- reinforcement-learning environments; or
- LLM-based application platforms.

## Technique-Related Dimensions

### Technique Family

The technique-family field captures the high-level testing or fuzzing
mechanism used by a study.

The main technique families include:

- Mutation-based
- Coverage-guided
- Learning-based
- Constraint-guided
- Search/heuristic-guided
- Differential testing
- LLM/prompt-guided
- Generation-based
- Metamorphic testing
- Debugging/fault-localization-oriented

Technique families are not necessarily mutually exclusive. A study may
combine several mechanisms within a hybrid workflow.

### Input Generation Strategy

This field records how the initial test inputs are produced or selected.

Examples include:

- seed-based generation;
- random generation;
- grammar-based generation;
- constraint-based generation;
- model-guided generation;
- generative-model-based synthesis;
- prompt-based generation; and
- scenario generation.

### Mutation Strategy

This field records how existing inputs or test artifacts are modified.

Examples include:

- random mutation;
- gradient-based mutation;
- semantic mutation;
- structure-aware mutation;
- parameter mutation;
- graph or program mutation;
- prompt mutation; and
- scenario mutation.

Input generation and mutation were recorded separately because studies may
use the same high-level technique family while differing substantially in how
tests are created and transformed.

## Oracle-Related Dimensions

### Oracle Type

The oracle-type field captures the high-level mechanism used to determine
whether the observed behavior indicates a failure.

The main oracle types include:

- Specification-based
- Differential
- Crash/Exception
- Inconsistency-based

### Oracle Construction

Oracle construction describes how the failure-detection mechanism is
implemented.

Common construction mechanisms include:

- rules or constraints;
- heuristics;
- multiple models;
- reference implementations;
- multiple backends;
- multiple frameworks or libraries; and
- target-specific behavioral conditions.

Oracle type and oracle construction were recorded separately because the same
oracle type may be implemented in different ways.

## Failure Type

The failure-type field records the form of abnormal behavior exposed by the
fuzzing approach.

The main categories include:

- misclassification;
- crash/runtime error;
- numerical inconsistency;
- security vulnerability;
- safety violation;
- performance bug;
- behavioral inconsistency; and
- task- or domain-specific failures.

Failure categories were treated as multi-label when a study reported more
than one type of failure.

## Multi-Label Annotation

Several annotation dimensions were treated as non-mutually exclusive.

A study could receive multiple labels when it:

- combined several technique families;
- used more than one input-generation or mutation strategy;
- employed multiple oracle mechanisms;
- exposed several failure types; or
- evaluated more than one target or platform.

This design preserved the hybrid and target-dependent nature of AI-system
fuzzing approaches rather than forcing each study into a single category.

## Schema Development

The annotation schema was developed from the research questions and refined
iteratively during pilot annotation.

Controlled labels were used for the primary classification fields to improve
consistency, while evidence notes were retained for ambiguous or complex
cases.

The schema supported the subsequent LLM-assisted annotation, human
verification, consistency checking, and final synthesis reported in the
survey.

Further details are available on the
[LLM-Assisted Annotation page]({{ site.baseurl }}/methodology/llm-annotation.html)
and the
[Annotation Quality Control page]({{ site.baseurl }}/methodology/quality-control.html).
