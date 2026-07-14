---
layout: default
title: Oracle Analysis and Study Mapping
---

# Oracle Analysis and Study Mapping

[← Back to Home]({{ site.baseurl }}/)

[← Technique-to-Study Mapping]({{ site.baseurl }}/results/technique-study-mapping.html)

This page provides the extended analysis and complete study-level mapping for
the test oracles examined in the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

RQ3 asks how fuzzing studies determine whether a generated test exposes a
failure. This question is particularly important for AI systems because an
exact expected output is often unavailable for arbitrary inputs.

We analyze two related but distinct dimensions:

1. **Oracle type** — the high-level principle used to identify a failure; and
2. **Oracle construction** — the mechanism used to implement or approximate
   that principle in practice.

The categories are not mutually exclusive because a study may use multiple
oracle types or combine several construction mechanisms.

## Distribution Overview

### Oracle Types

| Oracle type | Number of studies |
|---|---:|
| Specification-based | 44 |
| Differential | 35 |
| Crash/Exception | 26 |
| Inconsistency-based | 25 |

### Oracle-Construction Mechanisms

| Oracle construction | Number of studies |
|---|---:|
| Rules/constraints | 62 |
| Heuristic | 34 |
| Multiple models | 14 |
| Reference implementation | 12 |
| Multiple backends | 2 |
| Multiple frameworks/libraries | 2 |

The complete clickable PID mapping is provided in the
[Detailed Study-Level Mapping](#detailed-study-level-mapping) section.

---

## Oracle Types

### Specification-Based Oracles

Specification-based oracles check whether system behavior satisfies predefined:

- rules;
- constraints;
- metamorphic relations;
- safety requirements;
- validity conditions; or
- domain-specific expectations.

They are the most common oracle type, appearing in **44 studies**.

Many of these specifications are partial rather than complete. Instead of
providing an exact expected output for every test input, they define conditions
that acceptable behavior should satisfy.

Examples include:

- **MDPFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p019">P019</a>), which uses task- and policy-level failure
  conditions;
- **DriveFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>), which evaluates driving behavior against
  scenario-level safety and quality requirements; and
- system-level autonomous-driving and reinforcement-learning studies that use
  trajectory, policy, safety, or environment-level conditions.

The dominance of specification-based oracles shows that AI fuzzing frequently
relies on partial specifications and domain knowledge rather than complete
input-output ground truth.

### Differential Oracles

Differential oracles compare behavior across:

- models;
- model variants;
- implementations;
- frameworks;
- libraries;
- compiler backends;
- software versions;
- devices; or
- reference executions.

They appear in **35 studies**.

A differential oracle treats unexpected disagreement among comparable
executions as a potential failure signal.

Examples include:

- **NNsmith** (<a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>), which compares compiled model outputs with a
  reference implementation;
- **TensorJSFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>), which uses comparison-based checking in
  DL framework testing;
- **FlashFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>), which compares CPU and GPU executions for
  output or exception divergence; and
- **DeepDiffer** (<a href="{{ site.baseurl }}/results/primary-studies.html#p091">P091</a>), which applies priority-guided
  differential fuzzing to DL compilers.

Differential oracles are especially useful for framework/library and
compiler/backend targets because these targets often provide multiple
comparable execution paths.

Their main challenge is distinguishing true defects from acceptable
differences caused by floating-point variation, approximation,
nondeterminism, or device-specific behavior.

### Crash/Exception Oracles

Crash/exception oracles treat the following as failures:

- runtime crashes;
- uncaught exceptions;
- assertion failures;
- segmentation faults;
- abnormal termination;
- invalid execution states; or
- other severe runtime errors.

They appear in **26 studies**.

This oracle type is particularly common in framework/library and
compiler/backend fuzzing because generated:

- API calls;
- tensor operations;
- computation graphs;
- compiler programs;
- optimization sequences; or
- backend executions

may trigger immediate runtime failures.

For example, **DocTer** (<a href="{{ site.baseurl }}/results/primary-studies.html#p017">P017</a>) generates DL API inputs and reports
severe failures such as segmentation faults, floating-point exceptions,
aborts, and bus errors.

Crash/exception oracles are practical because they do not require a complete
semantic specification of the expected output.

However, they mainly expose explicit runtime failures and may miss silent
numerical, behavioral, or semantic defects.

### Inconsistency-Based Oracles

Inconsistency-based oracles detect:

- unstable predictions;
- unexpected behavioral changes;
- numerical instability;
- output inconsistency;
- semantic deviations; or
- violations of expected behavioral relations.

They appear in **25 studies** and are common in model-level testing.

Examples include:

- **DeepCNP** (<a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>);
- **DLRegion** (<a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>);
- **DeepHunter** (<a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>);
- **DeepRoad** (<a href="{{ site.baseurl }}/results/primary-studies.html#p049">P049</a>); and
- **CAGFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>).

These studies identify failures through prediction changes, behavioral
deviations, transformed-input inconsistencies, or other forms of unstable
behavior when exact expected labels are unavailable.

Inconsistency-based oracles directly address a central problem in AI testing:
many failures cannot be identified using one exact expected output.

---

## Target-Dependent Oracle Patterns

Oracle choice varies substantially by testing target.

### Framework/Library and Compiler/Backend Targets

These studies frequently use:

- differential comparison;
- reference implementations;
- multiple backends;
- multiple frameworks or libraries; and
- crash/exception detection.

These targets often provide comparable execution paths and observable runtime
failures.

For example:

- **NNsmith** (<a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>) compares compiled outputs against reference
  execution;
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>) checks result inconsistency, performance
  degradation, crashes, and unexpected exceptions; and
- **HIRGEN** (<a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>) checks crashes, IR-level result
  inconsistencies, and hardware-level differences.

### Model-Level Targets

Model-level studies more often use:

- specification-based checking;
- inconsistency-based checking;
- metamorphic relations;
- robustness constraints;
- prediction differences; and
- numerical-deviation thresholds.

These mechanisms help compensate for the absence of exact ground truth for
arbitrary generated inputs.

### System-Level Targets

System-level studies typically use:

- domain-specific safety rules;
- scenario-level constraints;
- policy-level behavior;
- trajectory requirements;
- environment-level validity conditions; and
- task-specific failure definitions.

This pattern appears in autonomous-driving and reinforcement-learning fuzzing,
including **DriveFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>), **AV-FUZZER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p069">P069</a>),
and **ScenarioFuzz-LLM** (<a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a>).

---

## Oracle Construction

### Rules and Constraints

Rules/constraints are the most common oracle-construction mechanism, appearing
in **62 studies**.

This category includes:

- manually defined specifications;
- domain rules;
- validity constraints;
- safety requirements;
- metamorphic relations;
- behavioral invariants;
- threshold-based rules; and
- task-specific acceptance conditions.

The frequency of this mechanism reflects the need to express partial,
target-specific expectations when exact outputs are unavailable.

### Heuristic Construction

Heuristic construction appears in **34 studies**.

Heuristic oracles use practical approximations such as:

- suspicious-behavior indicators;
- empirical thresholds;
- tool-specific checks;
- approximate comparison criteria;
- prediction-difference signals;
- abnormal-performance indicators; or
- custom failure scores.

For example:

- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>) uses practical checks for inconsistency,
  performance degradation, crashes, and unexpected exceptions;
- **FlashFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>) uses tolerance-based output comparison and
  exception-divergence checks across devices; and
- model-level fuzzers may use confidence, prediction difference, coverage, or
  other approximate signals to identify suspicious behavior.

Heuristic construction is flexible, but its reliability depends on the
quality and calibration of the selected signal.

### Multiple Models

Comparison across multiple models appears in **14 studies**.

This construction mechanism checks whether several models or model variants
behave consistently on the same or related inputs.

It is useful when no single model can serve as an unquestioned source of truth,
but agreement or disagreement across models provides an informative failure
signal.

### Reference Implementations

Reference-implementation oracles appear in **12 studies**.

A trusted implementation, unoptimized execution, baseline system, or reference
backend is used as the comparator.

Examples include:

- **NNsmith** (<a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>);
- **ExAIS** (<a href="{{ site.baseurl }}/results/primary-studies.html#p020">P020</a>);
- **Predoo** (<a href="{{ site.baseurl }}/results/primary-studies.html#p021">P021</a>);
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>); and
- **TorchProbe** (<a href="{{ site.baseurl }}/results/primary-studies.html#p089">P089</a>).

This mechanism can provide a strong comparison baseline, although its
reliability depends on the correctness and independence of the reference.

### Multiple Backends

Comparison across multiple backends appears in **2 studies**:

- **FlashFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>); and
- **FUEL** (<a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a>).

This mechanism checks whether equivalent executions remain consistent across
hardware or backend configurations.

### Multiple Frameworks or Libraries

Comparison across multiple frameworks or libraries appears in **2 studies**:

- **Gandalf** (<a href="{{ site.baseurl }}/results/primary-studies.html#p119">P119</a>); and
- **COMET** (<a href="{{ site.baseurl }}/results/primary-studies.html#p120">P120</a>).

Cross-framework comparison is useful when semantically equivalent
implementations are available in more than one AI software ecosystem.

---

## Hybrid and Multi-Signal Oracle Design

Several studies combine multiple oracle types or construction mechanisms.

For example:

- **NNsmith** (<a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>) uses differential comparison against a
  reference execution while also detecting compiler crashes and inconsistent
  results.
- **HIRGEN** (<a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>) combines crash detection, result
  inconsistency among original, optimized, and semantically mutated high-level
  IRs, and cross-device comparison.
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>) checks optimized and non-optimized executions
  for inconsistency, detects performance degradation, and records crashes or
  unexpected exceptions.
- **FlashFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>) performs differential checking across CPU
  and GPU executions and treats both output divergence and exception
  divergence as potential defects.

These examples show that oracle design in AI fuzzing is frequently hybrid and
target-dependent rather than tied to one failure signal.

---

## Main Findings

The oracle analysis supports five main observations:

1. **Specification-based oracles are the most common, but they are usually
   partial rather than complete.**
2. **Differential oracles are especially useful for framework/library and
   compiler/backend targets.**
3. **Crash/exception oracles remain important for component-level AI software
   testing.**
4. **Inconsistency-based oracles help address the lack of exact expected
   outputs in model-level testing.**
5. **Oracle construction is frequently hybrid and strongly dependent on the
   target, available comparators, and observable failure behavior.**

Overall, no single oracle type provides a complete solution across all
AI-system targets.

The results motivate stronger:

- semantic oracles;
- numerical oracles;
- metamorphic relations;
- safety-aware checks;
- domain-specific specifications; and
- hybrid oracle designs

that can better capture failures across models, frameworks/libraries,
compiler backends, and integrated AI applications.

---

## Detailed Study-Level Mapping

Each PID below links to the corresponding entry in the
[Primary Studies catalogue]({{ site.baseurl }}/results/primary-studies.html),
which provides the full title, authors, publication year, venue, BibTeX key,
and DOI or publication link.

<details open>
<summary><strong>Oracle Types</strong></summary>

<div style="overflow-x:auto;">

<table style="width:100%; min-width:900px;">
<thead>
<tr>
<th>Oracle type</th>
<th style="text-align:center;"># Studies</th>
<th>Primary studies</th>
</tr>
</thead>
<tbody>

<tr>
<td><strong>Specification-based</strong></td>
<td style="text-align:center;">44</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p012">P012</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p019">P019</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p020">P020</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p026">P026</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p035">P035</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p043">P043</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p050">P050</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p058">P058</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p068">P068</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p069">P069</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p088">P088</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p099">P099</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p106">P106</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p122">P122</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p133">P133</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p136">P136</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p137">P137</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p140">P140</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p147">P147</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p148">P148</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p152">P152</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p153">P153</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p157">P157</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p158">P158</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p160">P160</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p162">P162</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p165">P165</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p169">P169</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p172">P172</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p174">P174</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p178">P178</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p180">P180</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p182">P182</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p197">P197</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p200">P200</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p201">P201</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p202">P202</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p208">P208</a></td>
</tr>

<tr>
<td><strong>Differential</strong></td>
<td style="text-align:center;">35</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p008">P008</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p009">P009</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p010">P010</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p013">P013</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p014">P014</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p015">P015</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p016">P016</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p018">P018</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p029">P029</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p036">P036</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p038">P038</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p042">P042</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p045">P045</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p051">P051</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p060">P060</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p077">P077</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p086">P086</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p089">P089</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p090">P090</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p091">P091</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p095">P095</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p100">P100</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p119">P119</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p120">P120</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p156">P156</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p170">P170</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p176">P176</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p204">P204</a></td>
</tr>

<tr>
<td><strong>Crash/Exception</strong></td>
<td style="text-align:center;">26</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p002">P002</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p005">P005</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p006">P006</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p011">P011</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p017">P017</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p034">P034</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p076">P076</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p077">P077</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p078">P078</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p079">P079</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p081">P081</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p083">P083</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p087">P087</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p096">P096</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p101">P101</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p103">P103</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p104">P104</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p111">P111</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p113">P113</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p114">P114</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p116">P116</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p121">P121</a></td>
</tr>

<tr>
<td><strong>Inconsistency-based</strong></td>
<td style="text-align:center;">25</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p021">P021</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p022">P022</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p024">P024</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p025">P025</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p027">P027</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p030">P030</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p031">P031</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p033">P033</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p039">P039</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p040">P040</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p041">P041</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p044">P044</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p049">P049</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p061">P061</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p142">P142</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p144">P144</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p146">P146</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p154">P154</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p167">P167</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p198">P198</a></td>
</tr>

</tbody>
</table>

</div>

</details>




<details open>
<summary><strong>Oracle-Construction Mechanisms</strong></summary>

<div style="overflow-x:auto;">

<table style="width:100%; min-width:900px;">
<thead>
<tr>
<th>Oracle construction</th>
<th style="text-align:center;"># Studies</th>
<th>Primary studies</th>
</tr>
</thead>
<tbody>

<tr>
<td><strong>Rules/constraints</strong></td>
<td style="text-align:center;">62</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p005">P005</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p009">P009</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p010">P010</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p012">P012</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p017">P017</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p019">P019</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p026">P026</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p035">P035</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p039">P039</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p041">P041</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p043">P043</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p049">P049</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p050">P050</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p058">P058</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p061">P061</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p068">P068</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p069">P069</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p077">P077</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p079">P079</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p081">P081</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p083">P083</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p088">P088</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p095">P095</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p099">P099</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p100">P100</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p106">P106</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p122">P122</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p133">P133</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p136">P136</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p137">P137</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p140">P140</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p144">P144</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p147">P147</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p148">P148</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p152">P152</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p153">P153</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p157">P157</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p158">P158</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p160">P160</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p162">P162</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p165">P165</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p169">P169</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p172">P172</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p174">P174</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p176">P176</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p178">P178</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p180">P180</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p182">P182</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p198">P198</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p200">P200</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p201">P201</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p202">P202</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p204">P204</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p208">P208</a></td>
</tr>

<tr>
<td><strong>Heuristic</strong></td>
<td style="text-align:center;">34</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p002">P002</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p011">P011</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p022">P022</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p024">P024</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p025">P025</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p027">P027</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p030">P030</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p031">P031</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p033">P033</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p034">P034</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p040">P040</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p044">P044</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p045">P045</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p076">P076</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p078">P078</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p087">P087</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p096">P096</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p101">P101</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p103">P103</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p104">P104</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p111">P111</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p113">P113</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p114">P114</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p116">P116</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p121">P121</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p142">P142</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p146">P146</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p154">P154</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p167">P167</a></td>
</tr>

<tr>
<td><strong>Multiple models</strong></td>
<td style="text-align:center;">14</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p006">P006</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p008">P008</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p013">P013</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p014">P014</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p016">P016</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p018">P018</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p036">P036</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p038">P038</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p051">P051</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p060">P060</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p156">P156</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p170">P170</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a></td>
</tr>

<tr>
<td><strong>Reference implementation</strong></td>
<td style="text-align:center;">12</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p015">P015</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p020">P020</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p021">P021</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p029">P029</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p042">P042</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p086">P086</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p089">P089</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p090">P090</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p091">P091</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p197">P197</a></td>
</tr>

<tr>
<td><strong>Multiple backends</strong></td>
<td style="text-align:center;">2</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a></td>
</tr>

<tr>
<td><strong>Multiple frameworks/libraries</strong></td>
<td style="text-align:center;">2</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p119">P119</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p120">P120</a></td>
</tr>

</tbody>
</table>

</div>

</details>

> **Note:** Categories are not mutually exclusive because some studies use
> multiple oracle types or combine several oracle-construction mechanisms.
