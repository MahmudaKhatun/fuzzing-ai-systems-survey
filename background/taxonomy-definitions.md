---
layout: default
title: Extended Taxonomy Definitions
---

# Extended Taxonomy Definitions

[← Back to Home]({{ site.baseurl }}/)

[← Extended Background]({{ site.baseurl }}/background/extended-background.html)

This page provides expanded definitions for the concepts used throughout the
survey *Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The main paper presents these concepts in compact form. This companion page
adds interpretation, boundary cases, and examples to clarify how the taxonomy
was applied during study annotation and analysis.

## Taxonomy at a Glance

<div style="overflow-x:auto;">

<table style="width:100%; min-width:950px; table-layout:fixed;">
<colgroup>
<col style="width:24%;">
<col style="width:76%;">
</colgroup>
<thead>
<tr>
<th>Concept</th>
<th>Question answered by the concept</th>
</tr>
</thead>
<tbody>

<tr>
<td><strong>Testing Target</strong></td>
<td>What concrete artifact does the fuzzer directly exercise?</td>
</tr>

<tr>
<td><strong>System Level</strong></td>
<td>At what layer is the behavior or failure observed?</td>
</tr>

<tr>
<td><strong>AI Paradigm</strong></td>
<td>What kind of AI system or learning setting is under test?</td>
</tr>

<tr>
<td><strong>Target Framework/Platform</strong></td>
<td>Which software ecosystem, runtime, compiler, simulator, or execution platform is tested?</td>
</tr>

<tr>
<td><strong>Technique Family</strong></td>
<td>What high-level mechanism guides test generation or exploration?</td>
</tr>

<tr>
<td><strong>Input-Generation Strategy</strong></td>
<td>How are initial tests or seeds created or selected?</td>
</tr>

<tr>
<td><strong>Mutation Strategy</strong></td>
<td>How are existing tests transformed into new candidates?</td>
</tr>

<tr>
<td><strong>Oracle Type and Construction</strong></td>
<td>How is a failure recognized, and how is that oracle implemented?</td>
</tr>

<tr>
<td><strong>Failure Type</strong></td>
<td>What kind of abnormal behavior is ultimately exposed?</td>
</tr>

</tbody>
</table>

</div>

---

## Testing Target

The **Testing Target** identifies the concrete artifact directly exercised by
the fuzzer.

The four target categories used in the survey are:

1. **Model**
2. **Framework/Library**
3. **Compiler/Backend**
4. **System-level AI application**

This dimension is central because the target strongly influences:

- the form of the test input;
- the validity constraints that generated tests must satisfy;
- the feedback signal used during exploration;
- the available oracle mechanisms; and
- the failure types that can be observed.

### Model

The trained or deployed model is the primary artifact under test.

Typical test inputs include:

- images;
- text;
- audio;
- feature vectors;
- prompts; or
- task-specific data instances.

Typical observations include:

- predictions;
- confidence scores;
- internal activations;
- coverage signals;
- robustness changes; and
- behavioral differences.

Representative examples include [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032),
[DLFuzz]({{ site.baseurl }}/results/primary-studies.html#p042), [GradFuzz]({{ site.baseurl }}/results/primary-studies.html#p040), and
[DeepCNP]({{ site.baseurl }}/results/primary-studies.html#p004).

### Framework/Library

The target is software infrastructure that implements AI computation, such as:

- an API;
- tensor operator;
- library function;
- runtime component; or
- framework implementation.

Generated tests may need to satisfy constraints over:

- tensor shapes;
- ranks;
- data types;
- devices;
- parameter values;
- API dependencies; and
- operator semantics.

Representative examples include [FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010),
[DocTer]({{ site.baseurl }}/results/primary-studies.html#p017), [TensorJSFuzz]({{ site.baseurl }}/results/primary-studies.html#p003), and
[ACETest]({{ site.baseurl }}/results/primary-studies.html#p113).

### Compiler/Backend

The target is the transformation or execution pipeline that converts AI
computations into optimized executable code.

Relevant components may include:

- compiler frontends;
- intermediate representations;
- optimization passes;
- schedulers;
- code generators;
- hardware backends; and
- inference runtimes.

Representative examples include [TzER]({{ site.baseurl }}/results/primary-studies.html#p046),
[NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001), [HIRGEN]({{ site.baseurl }}/results/primary-studies.html#p028),
[MLIR-Smith]({{ site.baseurl }}/results/primary-studies.html#p036), and [NeuRI]({{ site.baseurl }}/results/primary-studies.html#p006).

### System-Level AI Application

The target is an integrated AI-enabled application rather than an isolated
model, API, or compiler component.

The fuzzer evaluates interactions among:

- learned models;
- simulators;
- control logic;
- software components;
- tools;
- environments; and
- external inputs.

Representative examples include [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066),
[AV-FUZZER]({{ site.baseurl }}/results/primary-studies.html#p069), [MDPFuzz]({{ site.baseurl }}/results/primary-studies.html#p019), and
[MalFuzz]({{ site.baseurl }}/results/primary-studies.html#p140).

---

## System Level

The **System Level** records the layer at which behavior or failure is
observed.

The survey distinguishes:

- **Model-level**
- **Component-level**
- **System-level**

### Model-Level Observation

The observed behavior is centered on the trained model.

Examples include:

- changed predictions;
- reduced confidence;
- incorrect classifications;
- unstable activations;
- robustness degradation; and
- model-behavior inconsistency.

### Component-Level Observation

The observed behavior occurs in an AI software component, such as:

- a framework API;
- operator implementation;
- compiler pass;
- backend runtime; or
- library execution path.

Typical failures include:

- crashes;
- exceptions;
- assertion failures;
- numerical divergence;
- miscompilation; and
- performance anomalies.

### System-Level Observation

The observed behavior emerges from an integrated AI-enabled system.

Examples include:

- unsafe driving behavior;
- policy failures;
- trajectory violations;
- interaction failures;
- tool-use errors;
- security-policy violations; and
- application-level task failure.

> **Testing Target and System Level are related but not interchangeable.**
> The Testing Target records the artifact directly exercised by the fuzzer,
> whereas System Level records where the behavior or failure is observed.
> A test can exercise one layer while exposing a defect whose consequences
> become visible at another layer.

---

## AI Paradigm

The **AI Paradigm** records the type of AI system or learning setting addressed
by the study.

Common paradigms include:

- machine learning;
- deep learning;
- reinforcement learning;
- natural-language processing;
- large language models;
- generative AI; and
- agent-based AI systems.

The paradigm affects both the test representation and the meaning of failure.

### Deep Learning and Computer Vision

Many early studies focus on deep neural networks, especially image
classification.

Typical test artifacts include:

- images;
- tensors;
- feature vectors; and
- model graphs.

Typical failures include:

- misclassification;
- robustness degradation;
- unstable predictions; and
- adversarial behavior.

### Autonomous and Cyber-Physical Systems

The input may be a complete scenario rather than a single data instance.

Examples include:

- road layouts;
- weather conditions;
- traffic participants;
- vehicle trajectories;
- sensor conditions; and
- environment configurations.

Representative studies include [DeepRoad]({{ site.baseurl }}/results/primary-studies.html#p049),
[AV-FUZZER]({{ site.baseurl }}/results/primary-studies.html#p069), and [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066).

### Reinforcement Learning

Fuzzing explores sequential decision-making behavior by modifying:

- environment states;
- trajectories;
- policies;
- action sequences;
- Markov decision process configurations; or
- reward-relevant conditions.

Representative examples include [MDPFuzz]({{ site.baseurl }}/results/primary-studies.html#p019),
[ReinSeed]({{ site.baseurl }}/results/primary-studies.html#p130), and [the RL testing and repair framework]({{ site.baseurl }}/results/primary-studies.html#p164).

### LLM and Agent-Based Systems

The test input may include:

- prompts;
- multi-turn conversations;
- tool requests;
- package names;
- generated programs;
- interaction traces; or
- information flows.

These settings introduce failure modes such as:

- hallucination;
- unsafe generation;
- incorrect tool use;
- security-policy violation;
- prompt sensitivity; and
- agent-level interaction failure.

---

## Target Framework or Platform

The **Target Framework/Platform** records the concrete software ecosystem in
which fuzzing is performed.

Examples include:

### Frameworks and Libraries

- TensorFlow
- PyTorch
- Keras
- TensorFlow.js

### Compilers, Backends, and Runtimes

- TVM
- XLA
- MLIR
- TensorRT
- ONNX Runtime

### Simulators and System Platforms

- CARLA
- OpenAI Gym
- Stable-Baselines3
- autonomous-driving stacks
- reinforcement-learning environments

Representative studies include:

- [FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010) for DL-library testing;
- [TzER]({{ site.baseurl }}/results/primary-studies.html#p046) for tensor-compiler testing;
- [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001) for DL-compiler and backend testing;
- [MLIR-Smith]({{ site.baseurl }}/results/primary-studies.html#p036) for MLIR infrastructure; and
- [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066) for autonomous-driving system testing.

> **Datasets and model architectures are not classified as frameworks or
> platforms.** For example, MNIST, ImageNet, ResNet, and BERT may describe
> experimental subjects, but they do not identify the software platform being
> fuzzed.

---

## Technique Family

The **Technique Family** captures the high-level mechanism or guidance
principle used to explore the test space.

The normalized technique families used in the survey are:

1. Mutation-based
2. Coverage-guided
3. Learning-based
4. Constraint-guided
5. Search/Heuristic-guided
6. Differential testing
7. LLM/Prompt-guided
8. Generation-based
9. Metamorphic testing
10. Debugging/Fault-localization

### Mutation-Based

New tests are created by modifying existing:

- inputs;
- API calls;
- programs;
- model graphs;
- prompts;
- scenarios; or
- interaction traces.

Representative examples include [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032),
[FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010), and [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066).

### Coverage-Guided

The fuzzer retains or prioritizes tests using feedback such as:

- code coverage;
- neuron coverage;
- activation coverage;
- operator coverage;
- compiler-path coverage;
- state coverage; or
- trajectory coverage.

Representative examples include [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032) and
[TzER]({{ site.baseurl }}/results/primary-studies.html#p046).

### Constraint-Guided

Generation or mutation is restricted by explicit or inferred validity
constraints.

Representative examples include [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001),
[DocTer]({{ site.baseurl }}/results/primary-studies.html#p017), [TensorJSFuzz]({{ site.baseurl }}/results/primary-studies.html#p003), and
[ACETest]({{ site.baseurl }}/results/primary-studies.html#p113).

### Differential Testing

The same or equivalent test is executed across multiple:

- models;
- implementations;
- frameworks;
- libraries;
- devices;
- versions;
- backends; or
- reference systems.

Disagreement is treated as a potential failure signal.

Representative examples include [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001),
[Muffin]({{ site.baseurl }}/results/primary-studies.html#p009), and [DeepDiffer]({{ site.baseurl }}/results/primary-studies.html#p091).

### Learning-Based and LLM/Prompt-Guided

Learning-based methods use learned policies or models to support:

- generation;
- seed selection;
- mutation selection;
- prioritization; or
- search guidance.

LLM/prompt-guided methods specifically use LLMs or prompts for:

- program generation;
- API generation;
- repair;
- constraint inference;
- fuzz-driver construction; or
- test transfer.

Representative examples include [TitanFuzz]({{ site.baseurl }}/results/primary-studies.html#p015),
[DFUZZ]({{ site.baseurl }}/results/primary-studies.html#p002), [MirrorFuzz]({{ site.baseurl }}/results/primary-studies.html#p078), and
[NÜWA]({{ site.baseurl }}/results/primary-studies.html#p081).

### Generation-Based

Tests are synthesized from a grammar, template, generative model, structural
model, or other generator rather than only being mutated from existing seeds.

Representative examples include [SYNTHFUZZ]({{ site.baseurl }}/results/primary-studies.html#p034),
[MLIR-Smith]({{ site.baseurl }}/results/primary-studies.html#p036), and [HIRGEN]({{ site.baseurl }}/results/primary-studies.html#p028).

### Metamorphic Testing

The fuzzer generates related inputs and checks whether an expected relation
between their outputs holds.

Representative examples include [DeepRoad]({{ site.baseurl }}/results/primary-studies.html#p049),
[QATest]({{ site.baseurl }}/results/primary-studies.html#p039), and [π-fuzz]({{ site.baseurl }}/results/primary-studies.html#p041).

Technique-family labels are multi-label. A study may combine several central
mechanisms, such as:

- mutation + coverage guidance;
- constraints + differential testing;
- LLM generation + differential checking; or
- learning-based guidance + search.

The complete distribution and study mapping are available on the
[Technique-Family Analysis]({{ site.baseurl }}/results/technique-families.html)
and
[Technique-to-Study Mapping]({{ site.baseurl }}/results/technique-study-mapping.html)
pages.

---

## Input-Generation Strategy

The **Input-Generation Strategy** describes how initial tests or seeds are
created or selected before execution or mutation.

Common strategies include:

- seed-based generation;
- random generation;
- constraint-based generation;
- grammar-based generation;
- model-guided generation;
- generative-model-based synthesis;
- prompt-based generation; and
- scenario generation.

### Seed-Based Generation

The fuzzer starts from existing:

- images;
- datasets;
- API calls;
- model programs;
- driving scenes;
- prompts; or
- execution traces.

Representative examples include [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032) and
[FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010).

### Constraint-Based Generation

Generated tests must satisfy conditions such as:

- shape constraints;
- data-type constraints;
- API dependencies;
- operator preconditions;
- graph validity; or
- compiler grammar requirements.

Representative examples include [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001),
[ACETest]({{ site.baseurl }}/results/primary-studies.html#p113), and [DocTer]({{ site.baseurl }}/results/primary-studies.html#p017).

### Generative or Model-Guided Generation

Tests are synthesized using:

- learned generators;
- diffusion models;
- GANs;
- domain models;
- search procedures; or
- target-aware generation logic.

Representative examples include [DeepRoad]({{ site.baseurl }}/results/primary-studies.html#p049),
[CtrlFuzz]({{ site.baseurl }}/results/primary-studies.html#p012), and [MDPFuzz]({{ site.baseurl }}/results/primary-studies.html#p019).

### LLM-Based Generation

LLMs may create:

- API programs;
- unusual code;
- fuzz drivers;
- prompts;
- scenarios;
- constraints; or
- test analogues.

Representative examples include [TitanFuzz]({{ site.baseurl }}/results/primary-studies.html#p015),
[DFUZZ]({{ site.baseurl }}/results/primary-studies.html#p002), and [FD-FACTORY]({{ site.baseurl }}/results/primary-studies.html#p101).

Input generation is therefore strongly shaped by the validity requirements and
representation of the target layer.

---

## Mutation Strategy

The **Mutation Strategy** describes how an existing test is transformed into a
new candidate.

Common mutation categories include:

- random mutation;
- semantic mutation;
- structure-aware mutation;
- gradient-based mutation;
- parameter mutation;
- graph or program mutation;
- prompt mutation; and
- scenario mutation.

### Semantic or Robustness-Oriented Mutation

The transformation attempts to preserve relevant high-level meaning while
changing low-level characteristics.

Examples include:

- image transformations;
- weather changes;
- perceptual perturbations;
- semantics-preserving text changes; and
- scenario modifications.

Representative studies include [DeepRoad]({{ site.baseurl }}/results/primary-studies.html#p049),
[DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032), and [DEEPWALK]({{ site.baseurl }}/results/primary-studies.html#p061).

### Gradient-Based Mutation

Model gradients or gradient-related signals guide the search toward
error-inducing inputs.

Representative examples include [DLFuzz]({{ site.baseurl }}/results/primary-studies.html#p042) and
[GradFuzz]({{ site.baseurl }}/results/primary-studies.html#p040).

### Structure-Aware Mutation

The fuzzer modifies structured artifacts while preserving syntactic or
semantic validity.

Examples include:

- API calls;
- tensor shapes;
- data types;
- parameters;
- call sequences;
- computation graphs;
- intermediate representations; and
- optimization passes.

Representative examples include [FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010),
[DocTer]({{ site.baseurl }}/results/primary-studies.html#p017), [TzER]({{ site.baseurl }}/results/primary-studies.html#p046),
[HIRGEN]({{ site.baseurl }}/results/primary-studies.html#p028), and [MLIR-Smith]({{ site.baseurl }}/results/primary-studies.html#p036).

### Scenario and Interaction Mutation

System-level fuzzers may mutate:

- road layouts;
- weather;
- traffic participants;
- environment states;
- trajectories;
- policy-relevant conditions;
- prompts; or
- interaction histories.

Representative examples include [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066),
[MDPFuzz]({{ site.baseurl }}/results/primary-studies.html#p019), and [ScenarioFuzz-LLM]({{ site.baseurl }}/results/primary-studies.html#p127).

Input generation and mutation are recorded separately because the mechanism
used to create initial tests may differ from the mechanism used to transform
them during iterative exploration.

---

## Test Oracle and Oracle Construction

The **Test Oracle** determines how the fuzzer recognizes a failure.

The survey distinguishes four oracle types:

1. Specification-based
2. Differential
3. Crash/Exception
4. Inconsistency-based

### Specification-Based Oracle

The system is checked against:

- rules;
- constraints;
- metamorphic relations;
- safety requirements;
- validity conditions; or
- domain-specific expectations.

Representative examples include [MDPFuzz]({{ site.baseurl }}/results/primary-studies.html#p019) and
[DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066).

### Differential Oracle

Behavior is compared across:

- models;
- implementations;
- frameworks;
- backends;
- versions;
- devices; or
- reference executions.

Representative examples include [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001),
[TensorJSFuzz]({{ site.baseurl }}/results/primary-studies.html#p003), and [DeepDiffer]({{ site.baseurl }}/results/primary-studies.html#p091).

### Crash/Exception Oracle

Failures are identified through:

- crashes;
- exceptions;
- assertion failures;
- abnormal termination;
- invalid execution states; or
- internal compiler errors.

Representative examples include [DocTer]({{ site.baseurl }}/results/primary-studies.html#p017),
[TzER]({{ site.baseurl }}/results/primary-studies.html#p046), and [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001).

### Inconsistency-Based Oracle

The oracle detects:

- changed predictions;
- unstable behavior;
- numerical divergence;
- semantic inconsistency; or
- unexpected differences when exact ground truth is unavailable.

Representative examples include [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032) and
[DLRegion]({{ site.baseurl }}/results/primary-studies.html#p007).

### Oracle Construction

**Oracle Construction** records how the oracle is implemented or approximated
in practice.

Construction mechanisms include:

- rules/constraints;
- heuristics;
- multiple models;
- reference implementations;
- multiple backends; and
- multiple frameworks/libraries.

Oracle type and construction are separate because the same high-level oracle
can be realized in different ways.

For example, a differential oracle may compare:

- two models;
- a target and reference implementation;
- CPU and GPU executions;
- multiple compiler backends; or
- different AI frameworks.

The complete oracle analysis is available on the
[Oracle Analysis and Study Mapping page]({{ site.baseurl }}/results/oracle-study-mapping.html).

---

## Failure Type

The **Failure Type** records the abnormal behavior ultimately exposed by the
fuzzer.

The main categories include:

- misclassification;
- crash/runtime error;
- numerical inconsistency;
- security vulnerability;
- safety violation;
- performance bug;
- behavioral inconsistency; and
- task- or domain-specific failures.

### Model-Level Failures

Common examples include:

- incorrect prediction;
- changed label;
- robustness degradation;
- unstable behavior;
- unsafe output; and
- task-performance degradation.

Representative studies include [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032),
[DLFuzz]({{ site.baseurl }}/results/primary-studies.html#p042), and [DeepCNP]({{ site.baseurl }}/results/primary-studies.html#p004).

### Framework/Library Failures

Common examples include:

- crash;
- runtime exception;
- invalid tensor handling;
- API inconsistency;
- numerical discrepancy; and
- security vulnerability.

Representative studies include [FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010),
[DocTer]({{ site.baseurl }}/results/primary-studies.html#p017), and [ACETest]({{ site.baseurl }}/results/primary-studies.html#p113).

### Compiler/Backend Failures

Common examples include:

- compiler crash;
- wrong-code behavior;
- miscompilation;
- numerical inconsistency;
- optimization-induced divergence;
- backend mismatch; and
- performance degradation.

Representative examples include [TzER]({{ site.baseurl }}/results/primary-studies.html#p046),
[NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001), and [HIRGEN]({{ site.baseurl }}/results/primary-studies.html#p028).

### System-Level Failures

Common examples include:

- safety violation;
- policy failure;
- degraded task performance;
- autonomous-driving collision or traffic violation;
- perception failure;
- steering inconsistency;
- malware-classifier evasion;
- hallucination; and
- security-policy violation.

Representative examples include [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066),
[AV-FUZZER]({{ site.baseurl }}/results/primary-studies.html#p069), [MalFuzz]({{ site.baseurl }}/results/primary-studies.html#p140),
[SimsV]({{ site.baseurl }}/results/primary-studies.html#p197), and [FuzzScene]({{ site.baseurl }}/results/primary-studies.html#p198).

AI fuzzing therefore does not rely on one universal failure signal. The
appropriate failure definition depends on the target, system layer, domain,
and available oracle.

The complete failure analysis is available on the
[Failure Analysis and Study Mapping page]({{ site.baseurl }}/results/failure-study-mapping.html).

---

## Multi-Label Interpretation

Several taxonomy dimensions are intentionally non-mutually exclusive.

A study may:

- exercise more than one target;
- span multiple system levels;
- combine several technique families;
- use multiple input-generation or mutation strategies;
- employ hybrid oracle mechanisms; or
- expose several failure types.

Multi-label annotation preserves the hybrid and cross-layer nature of
AI-system fuzzing rather than forcing each study into one category.

## Related Companion Pages

- [Extended Background]({{ site.baseurl }}/background/extended-background.html)
- [Boundary with Related Testing Techniques]({{ site.baseurl }}/background/boundary-related-techniques.html)
- [Annotation Schema]({{ site.baseurl }}/methodology/annotation-schema.html)
- [Extended Technique-Family Analysis]({{ site.baseurl }}/results/technique-families.html)
- [Oracle Analysis and Study Mapping]({{ site.baseurl }}/results/oracle-study-mapping.html)
- [Failure Analysis and Study Mapping]({{ site.baseurl }}/results/failure-study-mapping.html)
