---
layout: default
title: Extended Background
---

# Extended Background

[← Back to Home]({{ site.baseurl }}/)

[View Boundary with Related Testing Techniques →]({{ site.baseurl }}/background/boundary-related-techniques.html)

[View Extended Taxonomy Definitions →]({{ site.baseurl }}/background/taxonomy-definitions.html)

This page provides extended background for the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The main paper presents the background in compact form. This companion page
expands the common fuzzing workflow, explains how conventional fuzzing
principles are adapted to AI systems, and summarizes the four target layers
used throughout the survey.

> **Reference note:** Foundational and boundary-setting studies discussed in
> the main paper are cited there in the formal bibliography. Included primary
> studies are linked here through their stable paper identifiers (PIDs).

---

## Overview of Fuzz Testing

Fuzz testing is an automated testing technique that repeatedly:

1. generates or selects test inputs;
2. mutates or transforms those inputs;
3. executes the system under test;
4. observes the resulting behavior;
5. checks for failures or anomalous behavior; and
6. uses feedback to guide subsequent exploration.

A simplified fuzzing loop can be represented as:

```text
Seed inputs or input generator
            ↓
Generation or mutation
            ↓
Execution on the target
            ↓
Monitoring and oracle checking
            ↓
Feedback, selection, or prioritization
            ↺
```

The process is iterative rather than purely random. Information obtained from
previous executions can influence which tests are retained, mutated, repaired,
or prioritized next.

Typical feedback signals in conventional software fuzzing include:

- code coverage;
- branch coverage;
- execution paths;
- exception types;
- crashes;
- assertion failures; and
- newly reached program states.

In AI-system fuzzing, the same general loop is retained, but the inputs,
feedback signals, oracle mechanisms, and failure definitions become more
target-dependent.

---

## Fuzzing in AI Systems

Fuzzing in AI systems refers to the automated generation or mutation of:

- data inputs;
- configurations;
- tensor programs;
- API calls;
- model graphs;
- compiler inputs;
- scenarios;
- prompts; or
- interaction traces

to expose failures in AI-enabled systems.

Unlike conventional fuzzing over byte-level inputs, AI-system fuzzing must
account for:

- learned and probabilistic behavior;
- semantic validity of inputs;
- numerical computation;
- large and structured test spaces;
- weak or incomplete test oracles;
- nondeterminism;
- multiple software layers; and
- interactions between learned and conventional components.

The target may be a model, framework/library, compiler/backend, or integrated
AI application.

---

## How the Test Space Changes Across AI-System Targets

The form of a valid test depends strongly on the target.

<div style="overflow-x:auto;">

<table style="width:100%; min-width:1050px; table-layout:fixed;">
<colgroup>
<col style="width:19%;">
<col style="width:31%;">
<col style="width:25%;">
<col style="width:25%;">
</colgroup>
<thead>
<tr>
<th>Target</th>
<th>Example test artifacts</th>
<th>Typical feedback</th>
<th>Representative failures</th>
</tr>
</thead>
<tbody>

<tr>
<td><strong>Model</strong></td>
<td>Images, text, audio, tensors, feature vectors, prompts, or task-specific inputs</td>
<td>Prediction changes, confidence, activation patterns, neuron coverage, gradients, robustness signals</td>
<td>Misclassification, prediction instability, robustness degradation, unsafe or degraded output</td>
</tr>

<tr>
<td><strong>Framework/Library</strong></td>
<td>API calls, operator invocations, tensor programs, model graphs, parameter combinations</td>
<td>API coverage, operator coverage, code paths, exceptions, output differences</td>
<td>Crash, runtime error, invalid tensor handling, numerical inconsistency, security vulnerability</td>
</tr>

<tr>
<td><strong>Compiler/Backend</strong></td>
<td>Models, computation graphs, intermediate representations, pass sequences, backend configurations</td>
<td>Compiler paths, pass coverage, optimization behavior, cross-backend comparison</td>
<td>Compiler crash, miscompilation, wrong-code behavior, numerical divergence, performance bug</td>
</tr>

<tr>
<td><strong>System-level application</strong></td>
<td>Driving scenarios, environment states, trajectories, policies, prompts, tool calls, multi-step interactions</td>
<td>State novelty, trajectory coverage, scenario diversity, safety signals, policy behavior</td>
<td>Safety violation, policy failure, perception failure, interaction failure, domain-specific behavioral error</td>
</tr>

</tbody>
</table>

</div>

---

## Testing Targets in AI Systems

The survey organizes AI-system fuzzing into four target layers:

1. Model
2. Framework/Library
3. Compiler/Backend
4. System-level AI application

These layers expose different failure surfaces and therefore require different
input representations, feedback mechanisms, oracle designs, and evaluation
criteria.

### Model-Level AI Fuzzing

Model-level fuzzing treats the trained model as the primary artifact under
test.

The fuzzer generates or mutates inputs and observes:

- predictions;
- confidence scores;
- internal activations;
- coverage signals;
- gradients;
- robustness measures; or
- behavioral changes.

Typical failures include:

- misclassification;
- prediction instability;
- robustness degradation;
- adversarial behavior; and
- unsafe or degraded outputs.

Representative primary studies include:

- [DeepHunter]({{ site.baseurl }}/results/primary-studies.html#p032)
- [DLFuzz]({{ site.baseurl }}/results/primary-studies.html#p042)
- [GradFuzz]({{ site.baseurl }}/results/primary-studies.html#p040)
- [DeepCNP]({{ site.baseurl }}/results/primary-studies.html#p004)
- [DLRegion]({{ site.baseurl }}/results/primary-studies.html#p007)

Foundational model-testing studies such as DeepXplore and TensorFuzz are also
discussed in the main paper because they helped establish coverage- and
behavior-oriented testing for deep neural networks.

### Framework- and Library-Level AI Fuzzing

Framework/library fuzzing targets the software infrastructure that implements
AI computation.

Deep learning libraries expose large API surfaces with constraints over:

- tensor shapes;
- ranks;
- data types;
- devices;
- parameter values;
- operator dependencies; and
- execution semantics.

Fuzzers generate valid but diverse API calls, tensor programs, operator
invocations, or model graphs to expose:

- crashes;
- uncaught exceptions;
- invalid tensor handling;
- implementation inconsistencies;
- numerical discrepancies; and
- security vulnerabilities.

Representative primary studies include:

- [FreeFuzz]({{ site.baseurl }}/results/primary-studies.html#p010)
- [DocTer]({{ site.baseurl }}/results/primary-studies.html#p017)
- [TensorJSFuzz]({{ site.baseurl }}/results/primary-studies.html#p003)
- [Predoo]({{ site.baseurl }}/results/primary-studies.html#p021)
- [ACETest]({{ site.baseurl }}/results/primary-studies.html#p113)
- [DeepConstr]({{ site.baseurl }}/results/primary-studies.html#p005)

Framework-level testing often depends on strong validity constraints because
randomly generated API calls may fail before reaching deep implementation
logic.

### Compiler- and Backend-Level AI Fuzzing

Compiler/backend fuzzing targets the transformation pipeline that converts
high-level AI computations into optimized executable code.

Relevant stages include:

- graph optimization;
- lowering;
- intermediate-representation transformation;
- pass scheduling;
- code generation;
- backend execution; and
- hardware-specific optimization.

Defects may cause:

- compiler crashes;
- wrong-code behavior;
- miscompilation;
- numerical inconsistency;
- semantic divergence;
- backend-specific mismatch; and
- performance degradation.

Representative primary studies include:

- [TzER]({{ site.baseurl }}/results/primary-studies.html#p046)
- [NNsmith]({{ site.baseurl }}/results/primary-studies.html#p001)
- [HIRGEN]({{ site.baseurl }}/results/primary-studies.html#p028)
- [MLIR-Smith]({{ site.baseurl }}/results/primary-studies.html#p036)
- [NeuRI]({{ site.baseurl }}/results/primary-studies.html#p006)
- [TorchProbe]({{ site.baseurl }}/results/primary-studies.html#p089)

Compiler/backend fuzzers often combine:

- structured generation;
- constraint inference;
- IR mutation;
- coverage guidance;
- reference execution; and
- differential comparison.

### System-Level AI Fuzzing

System-level AI fuzzing evaluates an integrated application rather than an
isolated model, API, or compiler component.

The target may combine:

- learned models;
- software components;
- simulators;
- control logic;
- policies;
- tools;
- environments; and
- external inputs.

Typical test artifacts include:

- driving scenes;
- traffic configurations;
- trajectories;
- environment states;
- policy-relevant conditions;
- prompts;
- tool calls; and
- interaction histories.

Typical failures include:

- collision;
- traffic-rule violation;
- unsafe policy behavior;
- perception failure;
- steering inconsistency;
- degraded task performance;
- malware-classifier evasion;
- hallucination; and
- security-policy violation.

Representative primary studies include:

- [DriveFuzz]({{ site.baseurl }}/results/primary-studies.html#p066)
- [AV-FUZZER]({{ site.baseurl }}/results/primary-studies.html#p069)
- [MDPFuzz]({{ site.baseurl }}/results/primary-studies.html#p019)
- [ReinSeed]({{ site.baseurl }}/results/primary-studies.html#p130)
- [ScenarioFuzz-LLM]({{ site.baseurl }}/results/primary-studies.html#p127)
- [MalFuzz]({{ site.baseurl }}/results/primary-studies.html#p140)
- [SimsV]({{ site.baseurl }}/results/primary-studies.html#p197)
- [FuzzScene]({{ site.baseurl }}/results/primary-studies.html#p198)

System-level fuzzing is especially challenging because failures may depend on
long interaction sequences, simulator fidelity, environmental assumptions, and
interactions among multiple components.

---

## Why AI-System Fuzzing Is Difficult

Across the four target layers, five recurring difficulties appear.

### 1. Input Validity

Generated tests must remain syntactically, semantically, structurally, or
physically meaningful.

### 2. Oracle Construction

Exact expected outputs are often unavailable, requiring partial
specifications, differential comparison, heuristics, metamorphic relations, or
domain-specific rules.

### 3. Adequacy and Feedback

Coverage or novelty signals may guide exploration without necessarily
correlating with meaningful failure detection.

### 4. Scalability

Gradient computation, model execution, constraint solving, compilation,
cross-backend comparison, simulation, and LLM inference can all be expensive.

### 5. Generalization

A technique evaluated on a small set of models, APIs, compilers, datasets,
simulators, or scenarios may not transfer to other systems or deployment
conditions.

These challenges are synthesized in detail on the
[Challenge Synthesis page]({{ site.baseurl }}/discussion/challenge-synthesis.html).

---

## Relationship to the Survey Taxonomy

The extended background motivates the main taxonomy dimensions:

- Testing Target
- System Level
- AI Paradigm
- Target Framework/Platform
- Technique Family
- Input-Generation Strategy
- Mutation Strategy
- Oracle Type
- Oracle Construction
- Failure Type

Together, these dimensions connect:

> **where fuzzing is applied, how tests are generated, how failures are
> detected, and what failures are exposed across the AI software stack.**

## Related Companion Pages

- [Boundary with Related Testing Techniques]({{ site.baseurl }}/background/boundary-related-techniques.html)
- [Extended Taxonomy Definitions]({{ site.baseurl }}/background/taxonomy-definitions.html)
- [Annotation Schema]({{ site.baseurl }}/methodology/annotation-schema.html)
- [Extended Technique-Family Analysis]({{ site.baseurl }}/results/technique-families.html)
- [Oracle Analysis and Study Mapping]({{ site.baseurl }}/results/oracle-study-mapping.html)
- [Failure Analysis and Study Mapping]({{ site.baseurl }}/results/failure-study-mapping.html)
