---
layout: default
title: Annotation Quality Control
---

# Annotation Quality Control

[← Back to Home]({{ site.baseurl }}/)

[← LLM-Assisted Annotation and Manual Validation]({{ site.baseurl }}/methodology/llm-annotation.html)

This page provides extended details of the quality-control procedures used to
improve the consistency and reliability of the final annotation dataset for
the survey *Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The quality-control process was applied during and after manual validation and
focused on fields that were frequently ambiguous, overlapping, or
target-dependent.

## Frequently Confused Annotation Fields

Particular attention was given to distinctions that could affect the
consistency of the taxonomy.

### Testing Target vs. System Level

The **Testing Target** field identifies the concrete artifact directly
exercised by the fuzzer.

Examples include:

- a trained model;
- a framework API;
- an operator implementation;
- a compiler backend; or
- an integrated AI application.

The **System Level** field identifies the layer at which behavior or failure
is observed.

These fields were reviewed separately because the artifact exercised by a
fuzzer and the layer at which its effects become visible are not always the
same.

### Target Framework/Platform vs. Dataset or Model Architecture

The **Target Framework/Platform** field records the software ecosystem,
execution environment, compiler, backend, simulator, or platform under test.

Datasets, model architectures, and benchmark tasks were not treated as target
frameworks unless they directly represented the system or platform being
tested.

### Input Generation Strategy vs. Mutation Strategy

The **Input Generation Strategy** field describes how initial test inputs are
created or selected.

The **Mutation Strategy** field describes how existing inputs, programs,
prompts, models, graphs, or scenarios are modified during fuzzing.

These fields were separated because a study may use one mechanism for
generating seeds and a different mechanism for mutating them.

### Oracle Type vs. Failure Type

The **Oracle Type** field records how a failure is detected.

Examples include:

- specification-based checking;
- differential comparison;
- crash or exception detection; and
- inconsistency-based checking.

The **Failure Type** field records the abnormal behavior that is ultimately
reported.

Examples include:

- misclassification;
- crash/runtime error;
- numerical inconsistency;
- security vulnerability;
- safety violation; and
- performance bug.

These concepts were reviewed independently because the same failure type may
be detected using different oracle mechanisms.

## Review-Status Tracking

During annotation, we maintained auxiliary fields to support manual review and
consistency checking.

These fields recorded:

- review status;
- unresolved cases;
- disagreement notes;
- annotation justifications;
- evidence references;
- correction history; and
- comments on difficult classification decisions.

The auxiliary fields were used only for internal quality control and were not
treated as part of the main analysis dataset.

## Evidence-Based Manual Verification

All final labels were checked against the original papers.

Manual verification focused on evidence from sections such as:

- Abstract
- Methodology
- Evaluation
- Discussion
- Limitations
- Threats to validity
- Future work
- Conclusion

Labels were corrected when they were:

- unsupported by the paper;
- based only on related work or background content;
- broader than the available evidence;
- inconsistent with the annotation schema; or
- incompatible with the study's actual testing target or workflow.

## Quality Risks of LLM-Assisted Annotation

LLMs may infer labels from incomplete evidence or assign categories based on
terms that appear in unrelated sections of a paper.

Potential risks include:

- confusing the proposed approach with methods discussed in related work;
- inferring unsupported technique labels;
- assigning overly broad categories;
- overlooking target-specific distinctions;
- confusing oracle mechanisms with reported failures;
- generating summaries that omit important methodological details; and
- assigning labels from insufficient contextual evidence.

To reduce these risks:

1. LLM outputs were treated only as preliminary suggestions.
2. Two independent LLM systems were used.
3. Section-aware evidence was provided whenever possible.
4. Human annotators verified all final labels against the original papers.
5. A checker reviewed eligibility decisions and technical classifications.
6. Ambiguous cases were documented and resolved through re-examination of the
   source paper.

## Reported vs. Inferred Study Characteristics

Reported limitations, threats to validity, and future-work statements were
distinguished from reviewer-inferred observations.

When a limitation, threat, or future direction was explicitly stated by the
authors, it was recorded as reported evidence.

When a potential limitation could be reasonably inferred from the study
design but was not explicitly stated, the annotation used a clear prefix such
as:

> **Not explicitly stated. Possible inferred ...**

This distinction was used to avoid presenting reviewer interpretation as an
author-reported claim.

## Multi-Label Consistency

Several annotation dimensions allowed multiple labels.

A study could receive multiple labels when it:

- combined several technique families;
- used more than one input-generation strategy;
- applied multiple mutation mechanisms;
- used hybrid oracle designs;
- exposed several failure types; or
- evaluated multiple targets or platforms.

Multi-label assignments were manually reviewed to ensure that each label was
supported by evidence from the paper.

## Final Consistency Review

After eligibility review and disagreement resolution, the verified metadata
was consolidated into the final analysis-ready dataset.

The final review checked:

- consistency of controlled labels;
- completeness of bibliographic metadata;
- alignment between target and system-level fields;
- separation of generation and mutation strategies;
- consistency between oracle and failure labels;
- handling of duplicate study versions;
- resolution of reviewer comments; and
- removal of unresolved annotation conflicts.

The resulting dataset supported the quantitative and qualitative analyses
reported in RQ1--RQ4.

## Relationship to the Replication Package

The replication package contains the annotation schema, normalized taxonomy
labels, intermediate screening files, LLM-assisted annotation outputs, and
analysis-supporting materials.

The package is available on
[Zenodo](https://doi.org/10.5281/zenodo.21022814).

Further details on the annotation workflow are available on the
[LLM-Assisted Annotation and Manual Validation page]({{ site.baseurl }}/methodology/llm-annotation.html).
