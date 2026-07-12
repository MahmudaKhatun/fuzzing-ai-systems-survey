---
layout: default
title: Study Selection and Multi-Stage Filtering
---

# Study Selection and Multi-Stage Filtering

[← Back to Home]({{ site.baseurl }}/)

[← Data Collection]({{ site.baseurl }}/methodology/data-collection.html)

This page provides extended details of the inclusion and exclusion criteria,
multi-stage screening process, and snowballing-based expansion used to identify
the final corpus of primary studies.

## Study Selection: Inclusion and Exclusion Criteria

We defined inclusion and exclusion criteria to identify studies that were
directly relevant to fuzzing AI systems.

### Inclusion Criteria

A study was included if it satisfied the following criteria:

- It was published within the January 2015–February 2026 search window.
- It proposed, evaluated, or empirically analyzed a fuzzing technique targeting
  AI systems, including ML/DL/LLM models, DL frameworks and libraries, AI
  compilers/backends, or system-level AI applications.
- It involved a recognizable fuzzing-style workflow, such as automated input
  generation or mutation, target execution, monitoring or feedback, and failure
  reporting.
- It provided sufficient technical detail to support metadata extraction and
  classification.

### Exclusion Criteria

A study was excluded if it satisfied any of the following criteria:

- It used AI, ML, DL, or LLMs to improve fuzzing of conventional software,
  rather than fuzzing AI systems.
- It targeted AI systems but did not use a fuzzing-style testing approach.
- It was unrelated to AI-system testing.
- It focused only on adversarial-attack optimization without a fuzzing-style
  workflow.
- It was a survey, review article, book chapter, short abstract, poster,
  tutorial, or other non-primary study.
- It was a short workshop paper that did not provide sufficient methodological
  or evaluation detail for systematic annotation.
- It was outside the selected publication period.
- It was not written in English.
- It was a duplicate record or an earlier preprint version of an already
  included published work.

Using these criteria, we first screened titles and abstracts to remove clearly
irrelevant records. We then applied the multi-stage filtering process described
below to refine the candidate set and identify the final primary studies.

---

## Multi-Stage Filtering

We applied a multi-stage filtering process to systematically refine the
dataset.

### Stage 1: Automated Keyword Filtering

An initial filtering step removed clearly irrelevant records using keyword
matching.

The filtering considered AI-related terms such as:

- machine learning
- deep learning
- neural network
- LLM
- large language model
- transformer
- foundation model
- model robustness

These terms were combined with fuzzing-related indicators such as:

- fuzz
- fuzzing
- fuzz testing
- coverage-guided
- robustness testing

This stage reduced the dataset from **1,996 unique records to 1,365 records**.

### Stage 2: Precision Tightening

A stricter filtering stage was then applied to ensure stronger alignment with
the survey scope.

This stage required explicit evidence of both:

1. an AI-system context; and
2. a fuzzing-related testing methodology.

After this step, **187 studies** remained as candidates for manual title and
abstract screening.

### Stage 3: Manual Title and Abstract Screening

We manually screened the titles and abstracts of the 187 candidate studies
using the predefined inclusion and exclusion criteria.

For each candidate, we examined whether the study:

- targeted an AI system;
- involved a recognizable fuzzing-style workflow;
- used input generation or mutation;
- executed the target system;
- incorporated monitoring, feedback, or failure signals; and
- reported relevant testing outcomes.

When necessary, abstracts were examined in terms of their context, objective,
approach, and findings to support a more accurate relevance assessment.

This stage retained **45 studies** for further verification and inclusion.

---

## Stage 4: Snowballing-Based Expansion

To improve recall, we complemented the database search with backward and
forward snowballing.

The snowballing process initially identified **1,854 candidate studies**.
Automated filtering reduced this set to **254 candidates**, including
43 backward-snowballing and 211 forward-snowballing studies.

After manual validation, **167 studies** were retained:

- 30 from backward snowballing
- 137 from forward snowballing

Together with the 45 studies retained after manual title and abstract
screening, this produced a combined candidate corpus of **212 studies**.

The detailed rationale, automation workflow, filtering indicators, and
intermediate snowballing results are available on the
[Backward and Forward Snowballing page]({{ site.baseurl }}/methodology/snowballing.html).


---

## Final Quality and Eligibility Assessment

After multi-stage filtering and snowballing, the combined candidate corpus
contained **212 studies**.

We then applied additional quality and eligibility checks before full-text
screening. Studies were re-examined when their relevance, methodological
clarity, evaluation detail, or eligibility as primary studies required
further verification.

This assessment removed **4 studies**, resulting in **208 candidate studies**
for full-text eligibility screening.

## Full-Text Eligibility Screening

The complete text of each of the 208 candidate studies was reviewed against
the predefined inclusion and exclusion criteria.

Studies were excluded when they:

- did not contain a recognizable fuzzing-style workflow;
- were only weakly related to fuzzing;
- used AI, ML, DL, or LLMs to improve fuzzing of conventional software rather
  than fuzzing AI systems;
- were outside the scope of AI-system testing;
- lacked sufficient methodological or evaluation detail; or
- were short or incomplete studies that could not support systematic
  annotation.

After full-text eligibility screening, **127 studies** were retained as
eligible primary-study candidates.

The 208 candidate studies also formed the input to the full-text eligibility
review and LLM-assisted annotation workflow described on the
[LLM-Assisted Annotation page]({{ site.baseurl }}/methodology/llm-annotation.html).

## Duplicate-Version Removal

During the final consistency check, we identified two duplicate study
versions in which both a preprint and a later published version of the same
work appeared in the corpus.

For each duplicate pair, we retained the published or more complete version
and removed the duplicate version.

This final step reduced the corpus from **127 to 125 primary studies**.

---

## Final Study-Selection Outcome

The complete study-selection process is summarized below.

| Selection stage | Number of records/studies |
|---|---:|
| Initial records collected | 3,905 |
| Unique records after deduplication | 1,996 |
| After Stage 1 automated filtering | 1,365 |
| After Stage 2 precision tightening | 187 |
| After manual title and abstract screening | 45 |
| Initial snowballing candidate pool | 1,854 |
| Snowballing candidates after automated filtering | 254 |
| Retained after manual snowballing review | 167 |
| Combined candidate corpus | 212 |
| After quality and eligibility assessment | 208 |
| After full-text eligibility screening | 127 |
| Final primary studies | **125** |
