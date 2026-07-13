---
layout: default
title: Boundary with Related Testing Techniques
---

# Boundary with Related Testing Techniques

[← Back to Home]({{ site.baseurl }}/)

[← Extended Background]({{ site.baseurl }}/background/extended-background.html)

[View Extended Taxonomy Definitions →]({{ site.baseurl }}/background/taxonomy-definitions.html)

This page clarifies how the survey distinguishes **fuzzing** from closely
related testing techniques.

The purpose of this boundary is not to suggest that related techniques are
unimportant. Instead, it explains when a study falls within the survey scope
and when it is treated as outside the scope because it lacks an iterative
fuzzing-style exploration workflow.

## Operational Boundary Used in the Survey

A technique is considered **fuzzing** when it follows an iterative process that:

1. generates, selects, or mutates test inputs;
2. executes the system under test;
3. observes the resulting behavior;
4. checks for failures or suspicious outcomes; and
5. uses feedback, novelty, coverage, or failure signals to guide continued
   exploration.

A study is generally excluded when it contributes only one isolated element,
such as:

- an oracle;
- an adequacy criterion;
- a path constraint;
- an adversarial attack;
- a mutation operator;
- a scenario generator; or
- a benchmark

without integrating that element into an iterative fuzzing workflow.

## Inclusion Decision at a Glance

<div style="overflow-x:auto;">

<table style="width:100%; min-width:1000px; table-layout:fixed;">
<colgroup>
<col style="width:22%;">
<col style="width:31%;">
<col style="width:23.5%;">
<col style="width:23.5%;">
</colgroup>
<thead>
<tr>
<th>Related technique</th>
<th>Why it overlaps with fuzzing</th>
<th>Included when</th>
<th>Excluded when</th>
</tr>
</thead>
<tbody>

<tr>
<td><strong>Metamorphic testing</strong></td>
<td>Metamorphic relations can generate related tests and act as oracles when exact expected outputs are unavailable.</td>
<td>The relations are embedded in an automated, iterative generation or mutation workflow with execution and failure checking.</td>
<td>The study only defines, validates, or evaluates metamorphic relations.</td>
</tr>

<tr>
<td><strong>Mutation testing</strong></td>
<td>Both mutation testing and fuzzing use mutation, but they mutate different artifacts.</td>
<td>Mutation supports iterative exploration of test inputs for failure discovery.</td>
<td>The study mutates programs, models, or tests only to evaluate test-suite adequacy.</td>
</tr>

<tr>
<td><strong>Concolic or symbolic testing</strong></td>
<td>Path exploration and constraint solving can support input generation and target deeper execution states.</td>
<td>Symbolic or concolic analysis is integrated with repeated generation or mutation, execution, feedback, and failure reporting.</td>
<td>Symbolic execution or constraint solving is the complete testing method and no fuzzing loop is present.</td>
</tr>

<tr>
<td><strong>Adversarial testing</strong></td>
<td>Adversarial input generation can search for model errors or robustness weaknesses.</td>
<td>The adversarial method is used as a mutation operator or search strategy within a broader fuzzing workflow.</td>
<td>The study is formulated only as an adversarial optimization or attack problem.</td>
</tr>

<tr>
<td><strong>Coverage-based autonomous-vehicle testing</strong></td>
<td>Scenario generation and simulator execution may use coverage or behavioral feedback.</td>
<td>Scenarios are iteratively generated or mutated, executed, evaluated, and guided by coverage or safety feedback.</td>
<td>The study only generates scenarios, measures coverage, or constructs a benchmark.</td>
</tr>

</tbody>
</table>

</div>

---

## Metamorphic Testing

Metamorphic testing is closely related to fuzzing because metamorphic
relations can provide a practical oracle when the expected output is difficult
or impossible to specify directly.

A metamorphic relation defines how the output should behave when the input is
transformed.

For example, a transformation may be expected to preserve:

- a model prediction;
- semantic meaning;
- a safety property;
- a numerical relation; or
- a behavioral invariant.

### Included

A metamorphic-testing study is included when the relation is part of an
automated process that repeatedly:

1. generates or transforms inputs;
2. executes the target;
3. checks whether the relation holds; and
4. continues exploration using the observed outcomes.

### Excluded

A study is excluded when its main contribution is limited to:

- defining metamorphic relations;
- evaluating the quality of those relations;
- proposing a new oracle only; or
- applying a fixed set of transformations without an iterative fuzzing loop.

The distinction is therefore based on the **workflow**, not on the presence of
metamorphic relations alone.

---

## Mutation Testing

Mutation testing and fuzzing both use the term **mutation**, but they usually
modify different artifacts for different purposes.

### Fuzzing

Fuzzing typically mutates:

- inputs;
- seeds;
- API calls;
- tensor programs;
- model graphs;
- scenarios;
- prompts; or
- interaction traces.

The purpose is to expose failures in the original system under test.

### Mutation Testing

Mutation testing typically modifies:

- source code;
- program statements;
- models;
- operators;
- test cases; or
- test artifacts.

The purpose is to evaluate the effectiveness or adequacy of a test suite.

### Included

A study is included when mutation is used to generate or evolve test inputs
within an iterative fuzzing workflow.

### Excluded

A study is excluded when mutation is used only to:

- create artificial faults;
- evaluate test-suite strength;
- compare adequacy criteria; or
- assess whether existing tests can detect mutants.

The key question is:

> **Is mutation being used to explore the input space and discover failures in
> the target, or to evaluate the effectiveness of a test suite?**

---

## Concolic and Symbolic Testing

Concolic and symbolic testing generate inputs by reasoning about program paths,
constraints, and internal execution conditions.

These techniques overlap with fuzzing because they can improve:

- path reachability;
- input validity;
- deep-state exploration;
- constraint satisfaction; and
- targeted test generation.

### Included

A study is included when concolic or symbolic analysis is one component of a
broader workflow that also performs:

- repeated input generation or mutation;
- target execution;
- runtime monitoring;
- feedback-guided exploration; and
- failure reporting.

In such cases, symbolic reasoning supports the fuzzer rather than replacing the
fuzzing loop.

### Excluded

A study is excluded when:

- symbolic execution is the complete testing method;
- path constraints are solved once without iterative fuzzing;
- no mutation or repeated exploration is used; or
- no fuzzing-style feedback loop is present.

The presence of constraint solving alone is therefore not sufficient for
inclusion.

---

## Adversarial Testing

Adversarial testing generates inputs designed to expose model errors,
robustness weaknesses, or security failures.

It overlaps with fuzzing because both may:

- perturb inputs;
- search for error-inducing behavior;
- use gradients or heuristics;
- optimize a failure objective; and
- evaluate model robustness.

### Included

An adversarial-testing study is included when adversarial generation is used
within a broader fuzzing workflow, for example as:

- a mutation operator;
- a search strategy;
- a seed-generation mechanism;
- a feedback-guided exploration method; or
- one component of an iterative failure-discovery loop.

### Excluded

A study is excluded when it is formulated only as:

- an adversarial optimization problem;
- a one-shot attack;
- a robustness benchmark;
- an attack-success evaluation; or
- a perturbation method without iterative fuzzing and failure exploration.

The survey therefore does not equate all adversarial attacks with fuzzing.

---

## Coverage-Based Autonomous-Vehicle Testing

Autonomous-vehicle testing often uses:

- scenario generation;
- simulator execution;
- environmental transformations;
- trajectory exploration;
- coverage metrics;
- behavioral diversity; and
- safety rules.

These features can resemble fuzzing, but scenario generation alone is not
sufficient.

### Included

A study is included when it repeatedly:

1. generates or mutates driving scenarios;
2. executes the autonomous-driving system or simulator;
3. observes coverage, behavior, or safety outcomes;
4. identifies failures or high-risk cases; and
5. uses feedback to guide subsequent scenario exploration.

### Excluded

A study is excluded when it focuses only on:

- scenario generation;
- coverage measurement;
- benchmark construction;
- simulation infrastructure;
- fixed scenario evaluation; or
- dataset creation

without feedback-guided mutation and failure discovery.

The central criterion is whether scenario generation participates in an
iterative fuzzing loop.

---

## Practical Screening Questions

During screening, the following questions help determine whether a study
belongs within the survey scope.

<div style="overflow-x:auto;">

<table style="width:100%; min-width:900px; table-layout:fixed;">
<colgroup>
<col style="width:9%;">
<col style="width:58%;">
<col style="width:33%;">
</colgroup>
<thead>
<tr>
<th>#</th>
<th>Screening question</th>
<th>Interpretation</th>
</tr>
</thead>
<tbody>

<tr>
<td style="text-align:center;"><strong>1</strong></td>
<td>Does the approach automatically generate, select, or mutate test inputs?</td>
<td>Required for a fuzzing-style input-exploration process.</td>
</tr>

<tr>
<td style="text-align:center;"><strong>2</strong></td>
<td>Are generated tests executed on a concrete AI system, component, or application?</td>
<td>Distinguishes testing from purely analytical or generative work.</td>
</tr>

<tr>
<td style="text-align:center;"><strong>3</strong></td>
<td>Does the approach observe runtime, behavioral, numerical, safety, security, or other failure-related outcomes?</td>
<td>Confirms that the workflow evaluates target behavior.</td>
</tr>

<tr>
<td style="text-align:center;"><strong>4</strong></td>
<td>Is exploration repeated or iterative rather than limited to one fixed set of tests?</td>
<td>Separates fuzzing from one-shot evaluation.</td>
</tr>

<tr>
<td style="text-align:center;"><strong>5</strong></td>
<td>Does feedback, novelty, coverage, or failure information influence continued exploration?</td>
<td>Provides the strongest evidence of a fuzzing-style loop.</td>
</tr>

</tbody>
</table>

</div>

A study does not need to use traditional code coverage to qualify. Feedback may
instead come from:

- model behavior;
- neuron activation;
- API or operator execution;
- compiler paths;
- state novelty;
- scenario diversity;
- safety signals;
- prediction changes;
- differential behavior; or
- domain-specific failure indicators.

---

## Boundary Principle

The survey applies the following general rule:

> **A related technique is included when it contributes to an iterative,
> automated failure-discovery workflow that generates or mutates tests,
> executes the target, observes behavior, and continues exploration using
> feedback or failure signals.**

This rule allows the survey to include hybrid approaches while excluding work
whose contribution is limited to a standalone oracle, attack, adequacy metric,
constraint solver, or scenario generator.

## Related Companion Pages

- [Extended Background]({{ site.baseurl }}/background/extended-background.html)
- [Extended Taxonomy Definitions]({{ site.baseurl }}/background/taxonomy-definitions.html)
- [Study Selection and Multi-Stage Filtering]({{ site.baseurl }}/methodology/study-selection.html)
- [Search Strategy]({{ site.baseurl }}/methodology/search-strategy.html)
- [Extended Technique-Family Analysis]({{ site.baseurl }}/results/technique-families.html)
