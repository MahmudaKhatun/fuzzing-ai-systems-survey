---
layout: default
title: Extended Technique-Family Analysis
---

# Extended Technique-Family Analysis

[← Back to Home]({{ site.baseurl }}/)

This page provides the extended analysis of fuzzing techniques reported in the
survey *Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The analysis distinguishes three related but different aspects of a fuzzing
approach:

1. **Technique family** — the main fuzzing mechanism or guidance principle;
2. **Input-generation strategy** — how initial test cases are generated or
   selected; and
3. **Mutation strategy** — how existing seeds or generated inputs are
   transformed.

This separation preserves implementation-level differences that may be hidden
by high-level technique labels.

## Technique-Family Distribution

Technique-family labels are not mutually exclusive because many studies combine
multiple central mechanisms.

| Normalized technique family | Number of studies |
|---|---:|
| Mutation-based | 63 |
| Coverage-guided | 52 |
| Learning-based | 30 |
| Constraint-guided | 17 |
| Search/Heuristic-guided | 16 |
| Differential testing | 15 |
| LLM/Prompt-guided | 14 |
| Generation-based | 7 |
| Metamorphic testing | 3 |
| Debugging/Fault-localization | 1 |

![Distribution of normalized fuzzing technique families]({{ site.baseurl }}/assets/images/technique-family-distribution.png)

*Figure 1. Distribution of normalized fuzzing technique families. Categories
are multi-label because some studies combine multiple central mechanisms.*

Mutation-based and coverage-guided fuzzing are the most common technique
families. This reflects the continued importance of traditional fuzzing
principles: modifying seeds, programs, models, scenarios, or inputs and using
feedback to guide further exploration.

The complete study-level mapping is available on the
[Technique-to-Study Mapping page]({{ site.baseurl }}/results/technique-study-mapping.html).

## Common AI-System Fuzzing Workflow

Although individual methods differ, many AI-system fuzzers follow a common
workflow:

1. seed or input generation;
2. technique-specific generation or mutation;
3. execution on the AI-system target;
4. oracle checking;
5. feedback collection; and
6. iterative refinement.

![Common workflow of AI-system fuzzing techniques]({{ site.baseurl }}/assets/images/technique-workflow.png)

*Figure 2. Common fuzzing workflow across AI-system targets. Different
technique families emphasize different parts of the loop, including mutation,
coverage feedback, constraints, learned guidance, differential comparison, or
LLM-based generation.*

---

## Mutation-Based Fuzzing

Mutation-based fuzzing creates new test cases by modifying existing:

- seeds;
- model inputs;
- programs;
- model structures;
- API calls;
- tensor programs;
- prompts;
- system scenarios; or
- interaction traces.

Mutation is useful because many AI-system targets require inputs that remain
sufficiently valid to execute while differing enough from existing examples to
expose unexpected behavior.

Mutation strategies may be:

- random;
- semantic;
- structure-aware;
- parameter-based;
- gradient-based; or
- target-specific.

For model-level testing, seeds may include images, audio, text, code, or other
data instances.

For framework and library testing, seeds may include:

- API calls;
- tensor programs;
- operator invocations; or
- model graphs.

For system-level testing, seeds may include:

- driving scenarios;
- environmental configurations;
- trajectories; or
- multi-step interactions.

Representative examples include:

- **DeepMutation** and **DeepMutation++**, which apply mutation-testing ideas
  to deep learning models;
- **DLJSFuzzer**, which uses mutation-based testing for TensorFlow.js;
- **DriveFuzz**, which mutates autonomous-driving scenarios; and
- **DeepHunter**, **DLRegion**, and **DEEPWALK**, which combine mutation with
  additional coverage or behavioral guidance.

Mutation-based fuzzing remains a foundational family because it can be adapted
across AI-system targets.

However, mutation quality is strongly target-dependent. Random mutations may
produce invalid or uninformative tests, while semantic or structure-aware
mutations require additional domain knowledge.

---

## Coverage-Guided Fuzzing

Coverage-guided fuzzing uses feedback from the target system to determine which
generated or mutated tests should be retained and explored further.

In conventional software fuzzing, feedback often refers to code coverage.

In AI-system fuzzing, coverage may include:

- code coverage;
- neuron coverage;
- layer coverage;
- activation coverage;
- state coverage;
- trajectory coverage;
- operator coverage;
- compiler-path coverage; or
- behavioral diversity.

A common workflow is:

1. generate or mutate a test;
2. execute the target;
3. measure new coverage or behavioral novelty;
4. retain coverage-increasing tests; and
5. return promising tests to the seed pool.

Representative examples include:

- **DeepHunter**, which combines input mutation with coverage feedback;
- **DLFuzz**, **DeepStellar**, **GradFuzz**, and **DeepCNP**, which use
  model-oriented coverage signals;
- **MDPFuzz**, which applies behavioral coverage to reinforcement-learning
  systems;
- **DriveFuzz**, which uses feedback in autonomous-driving scenario
  exploration; and
- **ReinSeed**, which combines trajectory-related feedback with learned action
  selection.

Coverage guidance provides an explicit exploration signal, but increased
coverage does not necessarily imply stronger failure detection.

For example, higher neuron or state coverage may not correspond to meaningful
semantic failures. Future work therefore requires target-aware adequacy metrics
that better reflect failure-revealing behavior.

---

## Constraint-Guided Fuzzing

Constraint-guided fuzzing generates or mutates tests under explicit validity
constraints.

Constraints may describe:

- API usage rules;
- tensor shapes;
- tensor ranks;
- data types;
- operator dependencies;
- model-graph structures;
- compiler intermediate representations;
- syntax rules;
- parameter conditions; or
- domain-specific validity requirements.

This family is especially important for frameworks, libraries, and compiler
backends because purely random inputs may be rejected before reaching deeper
target behavior.

A typical workflow:

1. defines or infers constraints;
2. generates constraint-satisfying tests;
3. executes the tests;
4. checks crashes, exceptions, inconsistencies, or backend mismatches; and
5. refines later generation.

Representative examples include:

- **NNSmith**, which generates valid neural-network models under constraints;
- **NeuRI** and **OATest**, which use constraint-aware generation for compiler
  behavior;
- **TensorJSFuzz**;
- **DeepConstr**;
- **DocTer**;
- **ConFL**; and
- **ACETest**.

Constraint-guided methods improve input validity and allow deeper target
execution.

Their effectiveness depends on constraint quality. Incomplete, overly strict,
or incorrectly inferred constraints may either generate invalid tests or
exclude important failure-revealing behaviors.

---

## Differential Fuzzing

Differential fuzzing detects potential failures by comparing multiple:

- implementations;
- versions;
- models;
- frameworks;
- devices;
- backends;
- execution modes; or
- reference systems.

Instead of requiring a complete expected output, the method treats
disagreement among comparable executions as a potential failure signal.

A typical differential workflow:

1. generate a test;
2. execute it on two or more comparable targets;
3. compare outputs, errors, numerical values, or runtime behavior; and
4. report significant disagreement.

Representative examples include:

- **NNSmith**, which combines constraint-guided generation with differential
  comparison across DL backends;
- **TensorJSFuzz**;
- **Muffin**;
- **FreeFuzz**;
- **∇Fuzz**;
- **DeepDiffer**;
- **D3**; and
- **TitanFuzz**, which combines LLM-generated programs with differential
  checking.

Differential testing reduces dependence on complete specifications.

However, not every difference indicates a defect. AI systems may exhibit:

- floating-point variation;
- approximation;
- nondeterminism;
- device-specific behavior; or
- acceptable implementation differences.

Differential oracles therefore require carefully selected tolerances and
comparison criteria.

---

## Generation-Based, Grammar-Based, and Structure-Aware Fuzzing

Generation-based fuzzing synthesizes new tests rather than only modifying
existing seeds.

Generated artifacts may include:

- model inputs;
- tensor programs;
- API sequences;
- computation graphs;
- compiler intermediate representations;
- prompts;
- programs; or
- system scenarios.

Grammar-based and structure-aware methods use:

- formal grammars;
- structural templates;
- syntax rules;
- graph constraints; or
- learned generators.

Representative examples include:

- **SYNTHFUZZ**, which uses grammar-based construction for compiler testing;
- **MLIR-Smith**, which generates MLIR programs;
- **HIRGEN**, which combines generation with coverage guidance; and
- **DeepMCC**, which uses learned generation together with diversity and
  validity constraints.

Generation-based fuzzing supports exploration of large, structured input
spaces.

The central challenge is balancing validity and diversity:

- overly unconstrained generators may create invalid tests;
- overly constrained generators may miss unusual but bug-revealing behavior.

---

## Learning-Based Fuzzing

Learning-based fuzzing uses machine learning, deep learning, reinforcement
learning, historical learning, or learned policies to improve:

- test generation;
- seed selection;
- mutation selection;
- prioritization;
- action selection;
- feedback interpretation; or
- search guidance.

The learned component helps make exploration adaptive when the input or state
space is too large or structured for unguided mutation.

Representative examples include:

- **ReinSeed**, which uses reinforcement learning for fuzzing-action
  selection;
- **SeqDivFuzz**, which uses learned diversity information;
- **RGChaser**, which applies reinforcement-learning-guided fuzzing;
- **GMFuzz**, which combines learning-based assessment with coverage, search,
  and mutation; and
- **AutoFuzz**, which uses learned guidance for scenario exploration.

Learning-based fuzzing is not a single input-generation mechanism. Learned
models may support:

- policy learning;
- mutation selection;
- prioritization;
- seed ranking;
- behavioral prediction; or
- adaptive feedback.

However, learned guidance may be:

- costly;
- unstable;
- biased toward training data;
- difficult to reproduce; or
- ineffective outside the training distribution.

Validation, feedback, and repair remain necessary.

---

## LLM/Prompt-Guided Fuzzing

LLM/Prompt-guided fuzzing is a specialized subgroup in which large language
models or prompts are central to:

- generation;
- mutation;
- repair;
- transfer;
- summarization;
- constraint inference;
- driver construction; or
- test prioritization.

A typical workflow:

1. prompt an LLM to generate a test program, API call, prompt, scenario, or
   fuzz driver;
2. validate the generated output;
3. execute the test;
4. evaluate the result using a crash, differential, specification-based, or
   heuristic oracle; and
5. repair or refine invalid outputs.

Representative examples include:

- **TitanFuzz**;
- **FuzzGPT**;
- **DFUZZ**;
- **YANHUI**;
- **MirrorFuzz**;
- **TransFuzz**;
- **FD-FACTORY**;
- **ALF**;
- **NÜWA**; and
- **ScenarioFuzz-LLM**.

LLM-guided fuzzing can generate complex and structured tests that are
difficult to construct manually.

However, LLM outputs may be:

- invalid;
- non-executable;
- nondeterministic;
- prompt-sensitive;
- expensive; or
- dependent on model reasoning quality.

LLM-based fuzzing should therefore be treated as a
**generate–validate–repair** process rather than a one-step generation
mechanism.

---

## Search/Heuristic-Guided and Feedback-Driven Fuzzing

Search/heuristic-guided fuzzing uses explicit objectives or heuristic signals
that are not necessarily structural coverage metrics.

Signals may include:

- distance to a target behavior;
- robustness scores;
- vulnerability likelihood;
- prediction difference;
- historical bug patterns;
- MCTS-based objectives;
- curiosity;
- regression-oriented feedback; or
- XAI-guided attention.

A common workflow:

1. define an objective;
2. generate or mutate tests;
3. execute the target;
4. evaluate the test using the objective; and
5. prioritize candidates that move closer to the desired behavior or expose
   larger differences.

Representative examples include:

- **DRFuzz**, which uses prediction-difference feedback;
- **GMFuzz**, which combines learned assessment, search, mutation, and coverage
  reward;
- **DeFinder**, which uses vulnerability-guided search;
- **Orion**, which uses historical behavior;
- **CureFuzz**, which uses curiosity-driven feedback; and
- **AV-Fuzzer**, which applies search to autonomous-driving scenarios.

The effectiveness of this family depends strongly on heuristic quality.

A weak objective may prioritize tests that appear interesting without exposing
meaningful failures.

---

## Metamorphic Fuzzing

Metamorphic fuzzing evaluates expected relations between related inputs and
outputs.

Instead of requiring an exact output, a metamorphic relation specifies how
behavior should remain unchanged or vary predictably after a transformation.

A typical workflow:

1. start from a seed input;
2. apply a transformation;
3. execute the original and transformed tests;
4. compare their outputs; and
5. identify violations of the expected relation.

Examples include:

- **DeepRoad**, which applies scene transformations to autonomous-driving
  systems;
- **QATest**, which combines metamorphic ideas with coverage guidance for
  question-answering systems; and
- **π-fuzz**, which applies metamorphic testing to reinforcement-learning
  systems.

Metamorphic testing is valuable because it addresses the oracle problem.

However, defining reliable relations is difficult:

- weak relations may miss failures;
- overly strict relations may classify acceptable variation as a defect.

---

## Debugging and Fault-Localization-Oriented Fuzzing

Debugging/fault-localization-oriented fuzzing focuses not only on exposing
failures but also on explaining where and why they occur.

A typical workflow:

1. generate or mutate tests;
2. expose abnormal behavior;
3. analyze the failing input or execution;
4. identify suspicious components or regions; and
5. support diagnosis or repair.

**MODE** represents this category in the normalized taxonomy because its
emphasis extends beyond failure detection toward debugging and fault
localization.

Although this family appears only once, it points to an important future
direction: AI-system fuzzing should support explanation, localization, and
repair rather than only failure reporting.

---

## Hybrid Nature of AI-System Fuzzing

Many AI-system fuzzers combine several central mechanisms.

Examples include:

- **DeepHunter** — mutation-based + coverage-guided;
- **NNSmith** — constraint-guided + differential testing;
- **TitanFuzz** — LLM/prompt-guided + differential testing;
- **ReinSeed** — learning-based guidance + coverage reward + scenario
  mutation; and
- **GMFuzz** — coverage guidance + learned assessment + mutation + search.

This hybrid pattern reflects the difficulty of testing AI systems.

Different mechanisms are often required to address:

- input validity;
- large input spaces;
- complex model behavior;
- structured test artifacts;
- weak or incomplete oracles; and
- target-dependent failure conditions.

Technique-family labels should therefore not be interpreted as mutually
exclusive categories.

They represent the central mechanisms combined by a fuzzer to generate, guide,
execute, and evaluate tests.

## Main Observations

The extended analysis supports five observations:

1. Mutation-based and coverage-guided approaches remain dominant.
2. Input-generation and mutation strategies reveal differences hidden by
   high-level family labels.
3. Learning-based and LLM/prompt-guided techniques are increasingly important
   for complex and structured input spaces.
4. Constraint-guided and differential methods are strongly associated with
   framework/library and compiler/backend targets.
5. AI-system fuzzers are increasingly hybrid rather than single-family.
