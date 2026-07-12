---
layout: default
title: Study Selection and Multi-Stage Filtering
---

# Study Selection and Multi-Stage Filtering

[← Back to Home]({{ site.baseurl }}/)

This page provides extended details of the screening, snowballing,
eligibility assessment, and final study-selection process used in the survey.

## Selection Overview

The initial search retrieved **3,905 records**. After metadata normalization
and deduplication, **1,996 unique records** remained for screening.

The selection process then proceeded through multiple stages:

1. Automated keyword filtering
2. Precision-oriented filtering
3. Manual title and abstract screening
4. Backward and forward snowballing
5. Quality and eligibility assessment
6. Full-text eligibility screening
7. Duplicate-version removal

## Stage 1: Automated Keyword Filtering

The first stage used AI-related and fuzzing-related keywords to remove clearly
irrelevant records.

This stage reduced the dataset from **1,996 to 1,365 records**.

## Stage 2: Precision Tightening

A stricter filtering stage required clearer evidence of both an AI-system
context and a fuzzing-related testing methodology.

After this stage, **187 candidate studies** remained for manual screening.

## Stage 3: Manual Title and Abstract Screening

The titles and abstracts of the 187 candidates were manually reviewed using
the predefined inclusion and exclusion criteria.

The review assessed whether each study:

- targeted an AI system;
- used a recognizable fuzzing-style workflow;
- involved input generation or mutation;
- executed the target system;
- used monitoring, feedback, or failure signals; and
- reported relevant testing outcomes.

This stage retained **45 studies**.

## Stage 4: Snowballing-Based Expansion

Backward and forward snowballing were used to identify relevant studies that
may have been missed because of indexing differences, terminology variation,
or search-interface limitations.

The snowballing process initially identified **1,854 candidate studies**.
Automated filtering reduced this set to **254 studies**, including:

- 43 backward-snowballing candidates
- 211 forward-snowballing candidates

After manual validation:

- 30 backward-snowballing studies were retained
- 137 forward-snowballing studies were retained

Therefore, snowballing contributed **167 studies**.

Combining these with the 45 studies retained from manual title and abstract
screening produced **212 candidate studies**.

## Quality and Eligibility Assessment

The 212 candidates underwent additional quality and eligibility assessment.

Four studies were removed because they did not provide sufficient relevance,
methodological clarity, evaluation detail, or eligibility as primary studies.

This produced **208 candidate studies** for full-text eligibility screening.

## Full-Text Eligibility Screening

The 208 candidates were assessed using the complete paper text.

Studies were excluded when they:

- did not use a recognizable fuzzing-style workflow;
- were only weakly related to fuzzing;
- used AI to improve conventional software fuzzing rather than fuzzing AI
  systems;
- were outside the scope of AI-system testing; or
- lacked sufficient methodological or evaluation detail.

After full-text screening, **127 eligible primary-study candidates** remained.

## Duplicate-Version Removal

Two duplicate study versions were identified during the final consistency
check.

For each duplicate pair, the published or more complete version was retained.

The final corpus therefore contained **125 primary studies**.

## Summary of Study Counts

| Stage | Number of studies |
|---|---:|
| Initial records | 3,905 |
| After deduplication | 1,996 |
| After Stage 1 | 1,365 |
| After Stage 2 | 187 |
| After manual title/abstract screening | 45 |
| Snowballing candidates before manual review | 254 |
| Retained from snowballing | 167 |
| Combined candidate set | 212 |
| After quality and eligibility assessment | 208 |
| After full-text eligibility screening | 127 |
| Final primary studies | 125 |
