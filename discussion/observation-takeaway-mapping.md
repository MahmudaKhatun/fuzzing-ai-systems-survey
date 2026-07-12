---
layout: default
title: Observation-to-Take-away Mapping
---

# Observation-to-Take-away Mapping

[← Back to Home]({{ site.baseurl }}/)

This page provides the complete mapping between the observations reported
across RQ1--RQ4 and the five take-away messages presented in the discussion
of the survey.

The mapping preserves the connection between the evidence reported in the
results and the broader synthesis presented in the discussion.

## Complete Mapping

<p><em>
Summary of key observations from RQ1--RQ4 and their mapping to take-away messages.
</em></p>

<div style="overflow-x:auto;">

<table>
<thead>
<tr>
<th style="text-align:center;">Obs.</th>
<th style="text-align:center;">Scope</th>
<th>Key observation</th>
<th style="text-align:center;">Take-away</th>
</tr>
</thead>

<tbody>

<tr>
<td style="text-align:center;"><strong>O1</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Research on fuzzing AI systems becomes substantially more active after 2021.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O2</strong></td>
<td style="text-align:center;">RQ1</td>
<td>The research landscape expands from model-level fuzzing toward broader AI-system targets, including frameworks/libraries, compiler backends, and system-level AI applications.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O3</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Recent studies show greater target diversity, indicating a shift toward a more system-oriented view of AI fuzzing.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O4</strong></td>
<td style="text-align:center;">RQ1</td>
<td>The 2026 count should be interpreted as partial coverage because the search window includes publications only up to February 2026.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O5</strong></td>
<td style="text-align:center;">RQ1</td>
<td>The literature is concentrated in software engineering, software testing, and reliability venues.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O6</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Both conference and journal venues play important roles, showing that the area is supported by fast-moving conference publication and archival journal dissemination.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O7</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Preprints also contribute to rapid dissemination, especially for emerging topics where techniques and tools evolve quickly.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O8</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Model-level fuzzing remains the dominant target, reflecting the influence of DNN and ML testing research.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O9</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Frameworks and libraries form a substantial target category, showing that AI-system failures may also arise from APIs, operators, runtime behavior, and implementation inconsistencies.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O10</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Compiler/backend and system-level fuzzing are smaller but important areas that extend fuzzing to lower-level execution components and end-to-end AI-enabled systems.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O11</strong></td>
<td style="text-align:center;">RQ1</td>
<td>AI fuzzing is evolving toward cross-layer testing across models, frameworks/libraries, compilers/backends, and system-level applications.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O12</strong></td>
<td style="text-align:center;">RQ1</td>
<td>Overall, the research landscape is recent, concentrated, and increasingly cross-layer.</td>
<td style="text-align:center;">T1</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O13</strong></td>
<td style="text-align:center;">RQ2</td>
<td>Mutation-based and coverage-guided fuzzing remain the dominant technique families.</td>
<td style="text-align:center;">T2</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O14</strong></td>
<td style="text-align:center;">RQ2</td>
<td>Input generation and mutation strategy reveal differences that are hidden by high-level technique-family labels.</td>
<td style="text-align:center;">T2</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O15</strong></td>
<td style="text-align:center;">RQ2</td>
<td>Learning-based and LLM/prompt-guided fuzzing are becoming important for complex and highly structured input spaces.</td>
<td style="text-align:center;">T2</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O16</strong></td>
<td style="text-align:center;">RQ2</td>
<td>Constraint-guided and differential testing are strongly connected to frameworks, libraries, and compiler/backend targets.</td>
<td style="text-align:center;">T2</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O17</strong></td>
<td style="text-align:center;">RQ2</td>
<td>AI fuzzing techniques are increasingly hybrid rather than single-family.</td>
<td style="text-align:center;">T2</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O18</strong></td>
<td style="text-align:center;">RQ3</td>
<td>Specification-based oracles are the most common, but they are often partial rather than complete behavioral specifications.</td>
<td style="text-align:center;">T3</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O19</strong></td>
<td style="text-align:center;">RQ3</td>
<td>Differential oracles are especially useful for framework/library and compiler/backend targets where comparable implementations or execution paths exist.</td>
<td style="text-align:center;">T3</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O20</strong></td>
<td style="text-align:center;">RQ3</td>
<td>Crash/exception oracles remain important for component-level AI software testing because they are practical and do not require complete semantic specifications.</td>
<td style="text-align:center;">T3, T4</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O21</strong></td>
<td style="text-align:center;">RQ3</td>
<td>Inconsistency-based oracles address the lack of exact expected outputs in model-level testing.</td>
<td style="text-align:center;">T3, T4</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O22</strong></td>
<td style="text-align:center;">RQ3</td>
<td>Oracle construction is frequently hybrid and target-dependent.</td>
<td style="text-align:center;">T3</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O23</strong></td>
<td style="text-align:center;">RQ4</td>
<td>Misclassification remains the dominant failure type, reflecting the strong emphasis on model-level fuzzing.</td>
<td style="text-align:center;">T4</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O24</strong></td>
<td style="text-align:center;">RQ4</td>
<td>Component-level fuzzing frequently exposes crashes and numerical inconsistencies in frameworks/libraries and compiler/backend targets.</td>
<td style="text-align:center;">T4</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O25</strong></td>
<td style="text-align:center;">RQ4</td>
<td>Security and safety failures are smaller but important categories, especially for high-impact AI systems.</td>
<td style="text-align:center;">T4</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O26</strong></td>
<td style="text-align:center;">RQ4</td>
<td>Specialized failure types show that AI fuzzing is expanding beyond prediction correctness.</td>
<td style="text-align:center;">T4</td>
</tr>

<tr>
<td style="text-align:center;"><strong>O27</strong></td>
<td style="text-align:center;">RQ4</td>
<td>Failure detection is target-dependent and often multi-label.</td>
<td style="text-align:center;">T4</td>
</tr>

</tbody>
</table>

</div>
