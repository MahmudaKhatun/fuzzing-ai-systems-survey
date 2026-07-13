---
layout: default
title: Failure Analysis and Study Mapping
---

# Failure Analysis and Study Mapping

[← Back to Home]({{ site.baseurl }}/)

[← Oracle Analysis and Study Mapping]({{ site.baseurl }}/results/oracle-study-mapping.html)

This page provides the extended analysis and complete study-level mapping for
the failure types reported in the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

RQ4 examines the types of failures exposed by fuzzing techniques for AI
systems. Each selected study was classified according to its reported failure
type. The categories are not mutually exclusive because some studies expose
more than one kind of failure.

## Failure-Type Distribution

| Failure type | Number of studies |
|---|---:|
| Misclassification | 49 |
| Crash/runtime error | 33 |
| Numerical inconsistency | 29 |
| Security vulnerability | 8 |
| Safety violation | 6 |
| Performance bug | 2 |
| Behavioral inconsistency | 1 |
| Coverage deficiency | 1 |
| Incorrect or degraded code summarization | 1 |
| ADS inconsistent steering behavior | 1 |
| ADS safety/perception failure | 1 |
| Translation errors | 1 |

The complete clickable PID mapping is provided in the
[Detailed Study-Level Mapping](#detailed-study-level-mapping) section.

---

## Misclassification

Misclassification is the most frequently reported failure type, appearing in
**49 studies**.

This category includes:

- incorrect predictions;
- changed labels;
- degraded task outputs;
- unstable decisions; and
- incorrect behavior triggered by generated, mutated, or semantically
  transformed inputs.

Misclassification is especially common in model-level fuzzing because many
studies evaluate whether a fuzzed input changes or degrades model behavior.

Examples include:

- **DeepHunter** (<a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>), which treats a changed prediction
  between an original seed and its mutant as error-inducing behavior;
- **CtrlFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p012">P012</a>), which targets model-level failures caused
  by generated test inputs;
- **DLRegion** (<a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>);
- **GradFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p040">P040</a>); and
- **DeepCNP** (<a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>).

The dominance of misclassification reflects the strong representation of
model-level testing in the corpus.

---

## Crash and Runtime Errors

Crash/runtime errors appear in **33 studies**.

This category includes:

- crashes;
- uncaught exceptions;
- assertion failures;
- segmentation faults;
- abnormal termination;
- compiler failures;
- invalid execution states; and
- other severe runtime errors.

These failures are common in framework/library and compiler/backend testing,
where generated:

- API calls;
- tensor operations;
- model graphs;
- tensor programs;
- compiler inputs;
- intermediate representations; or
- backend executions

may reach invalid or poorly tested execution states.

Examples include:

- **NNsmith** (<a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>), which reports compiler crashes and other
  execution failures;
- **DocTer** (<a href="{{ site.baseurl }}/results/primary-studies.html#p017">P017</a>), which exposes severe DL API failures,
  including segmentation faults, floating-point exceptions, aborts, and bus
  errors;
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>), which detects crashes and unexpected
  exceptions during tensor-compiler fuzzing;
- **NeuRI** (<a href="{{ site.baseurl }}/results/primary-studies.html#p006">P006</a>); and
- **Ache-Fuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p011">P011</a>).

Crash/runtime failures remain important because they are directly observable
and do not require a complete semantic specification.

However, crash-only detection may miss silent numerical, behavioral, or
security-relevant defects.

---

## Numerical Inconsistency

Numerical inconsistency appears in **29 studies**.

This category includes:

- divergent outputs;
- inconsistent numerical results;
- unstable computations;
- optimization-induced differences;
- device-dependent divergence;
- backend inconsistency; and
- cross-implementation output mismatch.

It is especially important for framework/library and compiler/backend testing,
where semantically equivalent executions may produce unexpectedly different
results.

Examples include:

- **TensorJSFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>);
- **HIRGEN** (<a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>), which detects inconsistent results across
  original, optimized, and semantically mutated high-level IRs;
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>), which compares optimized and non-optimized
  executions;
- **DeepDiffer** (<a href="{{ site.baseurl }}/results/primary-studies.html#p091">P091</a>);
- **D3** (<a href="{{ site.baseurl }}/results/primary-studies.html#p095">P095</a>); and
- **FUEL** (<a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a>).

**YANHUI** (<a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>) is associated with both crash/runtime error and
numerical inconsistency because framework-level model-optimization bugs may
involve execution failures as well as inconsistent optimized behavior.

Numerical inconsistency requires careful interpretation because small
floating-point or implementation-level differences may be acceptable, while
larger or semantically meaningful differences may indicate defects.

---

## Security Vulnerabilities

Security vulnerabilities appear in **8 studies**.

This category includes security-relevant defects in:

- AI frameworks;
- DL libraries;
- APIs;
- operators;
- runtime components;
- model-serving infrastructure; or
- AI-enabled software.

Examples include:

- **ConFL** (<a href="{{ site.baseurl }}/results/primary-studies.html#p111">P111</a>);
- **ACETest** (<a href="{{ site.baseurl }}/results/primary-studies.html#p113">P113</a>);
- **DKFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p116">P116</a>);
- **Orion** (<a href="{{ site.baseurl }}/results/primary-studies.html#p087">P087</a>); and
- **HFUZZER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p122">P122</a>).

Some of these studies report concrete vulnerabilities, including
CVE-associated issues.

Although security vulnerabilities appear less frequently than
misclassification, crashes, or numerical inconsistency, they are important
because defects in AI software infrastructure can affect confidentiality,
integrity, availability, and downstream applications.

---

## Safety Violations

Safety violations appear in **6 studies**.

This category captures failures that violate:

- task-level safety requirements;
- environment-level constraints;
- policy-level expectations;
- driving rules;
- collision-avoidance conditions; or
- other domain-specific safety requirements.

Safety violations are mainly associated with autonomous-driving,
reinforcement-learning, and system-level AI applications.

Examples include:

- **DriveFuzz** (<a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>), which detects collisions, traffic
  infractions, immobility, and other safety-critical driving misbehavior;
- **ReinSeed** (<a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>);
- **ScenarioFuzz-LLM** (<a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a>);
- the map-aware RL fuzzing approach (<a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>); and
- the RL testing and repair framework (<a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>).

Safety-oriented failures are fewer in number but highly important because they
occur in systems where incorrect behavior may have real-world consequences.

---

## Performance Bugs

Performance bugs appear in **2 studies**:

- the study on differential performance bugs in ML libraries
  (<a href="{{ site.baseurl }}/results/primary-studies.html#p045">P045</a>); and
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>).

These failures involve unexpected performance degradation, inefficient
optimization behavior, or other execution-time anomalies.

Performance bugs show that AI fuzzing can expose quality problems beyond
functional correctness.

---

## Specialized and Domain-Specific Failures

Several failure categories appear only once but capture important
target-specific behaviors.

### Behavioral Inconsistency

**DeepRoad** (<a href="{{ site.baseurl }}/results/primary-studies.html#p049">P049</a>) reports behavioral inconsistency in an
autonomous-driving setting.

### Coverage Deficiency

**DeepHC** (<a href="{{ site.baseurl }}/results/primary-studies.html#p167">P167</a>) reports coverage deficiency as a target of its
test-generation process.

### Incorrect or Degraded Code Summarization

**CoCoFuzzing** (<a href="{{ site.baseurl }}/results/primary-studies.html#p180">P180</a>) reports degraded code-summarization
behavior in neural code models.

### ADS Inconsistent Steering Behavior

**FuzzScene** (<a href="{{ site.baseurl }}/results/primary-studies.html#p198">P198</a>) reports inconsistent steering behavior in
autonomous-driving systems.

### ADS Safety or Perception Failure

**SimsV** (<a href="{{ site.baseurl }}/results/primary-studies.html#p197">P197</a>) targets perception- and safety-related failures
in simulated autonomous-driving scenarios.

### Translation Errors

**DiFuzzNMT** (<a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a>) reports translation errors in neural machine
translation.

These categories show that AI fuzzing increasingly considers task-specific and
domain-specific failures rather than only prediction errors or runtime crashes.

---

## Relationship Between Testing Target and Failure Type

Failure type is closely related to the AI-system layer under test.

### Model-Level Studies

Model-level studies mainly report:

- misclassification;
- prediction changes;
- robustness failures;
- behavioral inconsistency;
- numerical instability; and
- degraded task outputs.

These failures are centered on model behavior.

### Framework/Library and Compiler/Backend Studies

Component-level studies more often report:

- crashes;
- runtime exceptions;
- assertion failures;
- numerical inconsistencies;
- performance bugs;
- operator defects; and
- security vulnerabilities.

These failures arise because fuzzing exercises executable software components,
including APIs, tensor operations, compiler passes, optimization paths,
backends, and runtime systems.

### System-Level Studies

System-level studies report broader failures such as:

- safety violations;
- policy-level failures;
- trajectory problems;
- perception failures;
- steering inconsistencies; and
- other domain-specific behavioral errors.

This variation shows that a single failure definition is insufficient for all
AI-system targets.

---

## Multi-Label Failure Detection

Several studies expose more than one type of failure.

Examples include:

- **HIRGEN** (<a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>) — crash/runtime error + numerical
  inconsistency;
- **TzER** (<a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>) — crash/runtime error + numerical inconsistency
  + performance bug;
- **DeepHunter** (<a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>) — misclassification + numerical
  inconsistency;
- **YANHUI** (<a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>) — crash/runtime error + numerical
  inconsistency; and
- the RL testing and repair framework (<a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>) —
  misclassification + safety violation.

These examples show that one fuzzing workflow may expose several kinds of
defects.

Failure labels should therefore be interpreted as overlapping dimensions
rather than mutually exclusive categories.

---

## Main Findings

The failure analysis supports five main observations:

1. **Misclassification remains the dominant failure type**, reflecting the
   strong emphasis on model-level fuzzing.
2. **Framework/library and compiler/backend fuzzing frequently expose crashes
   and numerical inconsistencies.**
3. **Security and safety failures are less frequent but important for
   high-impact AI systems.**
4. **Specialized failure categories show that AI fuzzing is expanding beyond
   prediction correctness.**
5. **Failure detection is target-dependent and frequently multi-label.**

Overall, the failure model in AI fuzzing must go beyond crashes and exceptions.

The corpus includes:

- incorrect predictions;
- runtime failures;
- numerical inconsistencies;
- security vulnerabilities;
- safety violations;
- performance bugs; and
- specialized domain-level failures.

This diversity indicates that models, frameworks/libraries, compiler
backends, and integrated AI applications require different failure
definitions and detection mechanisms.

---

## Detailed Study-Level Mapping

Each PID below links to the corresponding entry in the
[Primary Studies catalogue]({{ site.baseurl }}/results/primary-studies.html),
which provides the full title, authors, publication year, venue, BibTeX key,
and DOI or publication link.

<div style="overflow-x:auto;">

<table style="width:100%; min-width:900px;">
<thead>
<tr>
<th>Failure type</th>
<th style="text-align:center;"># Studies</th>
<th>Primary studies</th>
</tr>
</thead>
<tbody>

<tr>
<td><strong>Misclassification</strong></td>
<td style="text-align:center;">49</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p012">P012</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p018">P018</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p022">P022</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p024">P024</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p025">P025</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p027">P027</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p030">P030</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p031">P031</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p033">P033</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p038">P038</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p039">P039</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p040">P040</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p042">P042</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p044">P044</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p050">P050</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p051">P051</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p058">P058</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p060">P060</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p061">P061</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p136">P136</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p137">P137</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p140">P140</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p142">P142</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p146">P146</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p147">P147</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p152">P152</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p153">P153</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p154">P154</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p157">P157</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p158">P158</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p160">P160</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p162">P162</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p169">P169</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p170">P170</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p172">P172</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p174">P174</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p176">P176</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p178">P178</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p182">P182</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p200">P200</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p201">P201</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p202">P202</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p204">P204</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p208">P208</a></td>
</tr>

<tr>
<td><strong>Crash/runtime error</strong></td>
<td style="text-align:center;">33</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p002">P002</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p005">P005</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p006">P006</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p010">P010</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p011">P011</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p013">P013</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p017">P017</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p019">P019</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p026">P026</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p034">P034</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p035">P035</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p036">P036</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p041">P041</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p068">P068</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p069">P069</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p076">P076</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p077">P077</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p078">P078</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p079">P079</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p081">P081</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p083">P083</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p088">P088</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p089">P089</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p096">P096</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p101">P101</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p103">P103</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p104">P104</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p133">P133</a></td>
</tr>

<tr>
<td><strong>Numerical inconsistency</strong></td>
<td style="text-align:center;">29</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p008">P008</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p009">P009</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p014">P014</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p015">P015</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p016">P016</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p020">P020</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p021">P021</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p029">P029</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p036">P036</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p040">P040</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p086">P086</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p090">P090</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p091">P091</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p095">P095</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p099">P099</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p100">P100</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p106">P106</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p119">P119</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p120">P120</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p144">P144</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p148">P148</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p156">P156</a></td>
</tr>

<tr>
<td><strong>Security vulnerability</strong></td>
<td style="text-align:center;">8</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p043">P043</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p087">P087</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p111">P111</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p113">P113</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p114">P114</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p116">P116</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p121">P121</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p122">P122</a></td>
</tr>

<tr>
<td><strong>Safety violation</strong></td>
<td style="text-align:center;">6</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p165">P165</a></td>
</tr>

<tr>
<td><strong>Performance bug</strong></td>
<td style="text-align:center;">2</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p045">P045</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a></td>
</tr>

<tr>
<td><strong>Behavioral inconsistency</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p049">P049</a></td>
</tr>

<tr>
<td><strong>Coverage deficiency</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p167">P167</a></td>
</tr>

<tr>
<td><strong>Incorrect or degraded code summarization</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p180">P180</a></td>
</tr>

<tr>
<td><strong>ADS inconsistent steering behavior</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p198">P198</a></td>
</tr>

<tr>
<td><strong>ADS safety/perception failure</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p197">P197</a></td>
</tr>

<tr>
<td><strong>Translation errors</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a></td>
</tr>

</tbody>
</table>

</div>

> **Note:** Categories are not mutually exclusive because some studies report
> multiple failure types.
