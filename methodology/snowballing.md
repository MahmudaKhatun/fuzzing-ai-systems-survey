---
layout: default
title: Backward and Forward Snowballing
---

# Backward and Forward Snowballing

[← Back to Home]({{ site.baseurl }}/)

[← Study Selection and Multi-Stage Filtering]({{ site.baseurl }}/methodology/study-selection.html)

This page provides extended details of the backward and forward snowballing
process used to improve the coverage of the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

Snowballing complemented the database search by identifying potentially
relevant studies that may have been missed because of terminology variation,
indexing differences, incomplete metadata, or search-interface limitations.

## Why Snowballing Was Necessary

Terminology in AI-system fuzzing is fragmented across research communities.

Relevant studies may describe fuzzing or fuzzing-adjacent testing approaches
using terms such as:

- robustness testing;
- differential testing;
- compiler testing;
- adversarial testing;
- automated test generation;
- mutation-based testing;
- metamorphic testing; or
- coverage-guided testing.

Consequently, some relevant studies may not explicitly use the term
*fuzzing* in their titles, abstracts, or indexed metadata.

To reduce this recall risk, we complemented the database search with both
backward and forward snowballing.

## Backward Snowballing

Backward snowballing examined the reference lists of the studies retained
after the initial screening process.

The goal was to identify earlier studies that:

- introduced relevant fuzzing techniques;
- proposed related AI-system testing methods;
- were cited as methodological foundations; or
- were not retrieved through the original database queries.

The backward-snowballing process produced an initial candidate set that was
subsequently deduplicated, filtered, and manually reviewed.

## Forward Snowballing

Forward snowballing examined studies that cited the papers retained after the
initial screening process.

Citing studies were retrieved using:

- Google Scholar; and
- Semantic Scholar.

Forward snowballing helped identify more recent studies that extended,
adapted, evaluated, or compared previously identified AI-system fuzzing
techniques.

## Automated Snowballing Support

The snowballing process was supported by automated scripts to improve
consistency and reduce the amount of irrelevant material requiring manual
review.

Filtering and consolidation were performed using Python and Excel.

The workflow included:

1. DOI-based deduplication;
2. removal of studies already present in the candidate corpus;
3. filtering using testing-related indicators; and
4. filtering using AI-related indicators.

## Testing-Related Indicators

The automated scope filter considered testing-related terms such as:

- fuzz;
- fuzzing;
- test;
- testing;
- coverage;
- differential;
- metamorphic;
- mutation; and
- oracle.

These indicators were used to retain studies that potentially involved
automated testing, input exploration, feedback, or failure detection.

## AI-Related Indicators

The automated scope filter also considered AI-related terms such as:

- DNN;
- deep learning;
- machine learning;
- LLM;
- framework;
- compiler;
- operator;
- automatic differentiation; and
- reinforcement learning.

These indicators helped distinguish AI-system testing studies from work
focused only on conventional software.

## Snowballing Candidate Reduction

The combined backward and forward snowballing process initially identified
**1,854 candidate studies**.

After automated filtering and deduplication, **254 candidate studies**
remained for manual review.

The 254 candidates consisted of:

| Snowballing direction | Candidates before manual review |
|---|---:|
| Backward snowballing | 43 |
| Forward snowballing | 211 |
| **Total** | **254** |

## Manual Validation

The 254 snowballing candidates were manually evaluated using the same
inclusion and exclusion criteria applied during the main study-selection
process.

For each candidate, we examined whether the study:

- targeted an AI system;
- involved a recognizable fuzzing-style workflow;
- used automated input generation or mutation;
- executed the system under test;
- incorporated monitoring, feedback, or failure signals;
- reported relevant testing outcomes; and
- provided sufficient methodological and evaluation detail.

After manual validation, **167 studies** were retained.

The retained studies consisted of:

| Snowballing direction | Retained studies |
|---|---:|
| Backward snowballing | 30 |
| Forward snowballing | 137 |
| **Total** | **167** |

## Contribution to the Candidate Corpus

The initial database-screening process retained **45 studies** after manual
title and abstract screening.

Snowballing contributed an additional **167 retained studies**.

Therefore:

```text
45 studies from database screening
+ 167 studies from snowballing
= 212 candidate studies
