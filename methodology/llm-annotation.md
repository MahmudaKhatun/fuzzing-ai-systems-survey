---
layout: default
title: LLM-Assisted Annotation and Manual Validation
---

# LLM-Assisted Annotation and Manual Validation

[← Back to Home]({{ site.baseurl }}/)

[← Annotation Schema]({{ site.baseurl }}/methodology/annotation-schema.html)

This page provides extended details of the LLM-assisted annotation and
human-validation workflow used in the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The workflow used large language models to support evidence extraction and
preliminary annotation, followed by two-stage human validation. LLM outputs
were treated only as candidate annotations and were not used as final labels.

## Annotation Workflow

The annotation process began with the **208 candidate studies** retained after
quality and eligibility assessment.

The workflow consisted of the following stages:

1. full-text extraction from the original papers;
2. section-aware text organization;
3. LLM-assisted eligibility review and preliminary annotation;
4. annotator verification;
5. checker validation;
6. disagreement documentation and resolution; and
7. finalization of the analysis-ready dataset.

## Full-Text Extraction

The original PDF of each candidate study served as the primary evidence source.

We used **PyMuPDF** to extract metadata and full-text content from the papers.

The extracted text was divided into manageable chunks and, where possible,
organized according to paper sections such as:

- Abstract
- Introduction
- Methodology
- Evaluation
- Discussion
- Limitations
- Conclusion

Section-aware organization helped reduce the risk of assigning labels based on
methods mentioned only in background or related-work sections.

## LLM Systems

We used two LLM systems to obtain independent preliminary annotations:

- **GPT-5.4-mini**
- **Claude Opus 4.6**

Using two models reduced dependence on a single system and provided an
additional basis for identifying ambiguous or inconsistent annotations.

## Prompt and Evidence Design

The LLMs received:

- the predefined annotation schema;
- field definitions;
- allowed labels, where applicable;
- section-aware evidence extracted from each paper; and
- instructions to classify only the paper's proposed technique.

The prompts explicitly instructed the models not to assign labels based only
on techniques discussed in background or related-work sections.

The generated outputs included:

- preliminary eligibility judgments;
- candidate field-level labels;
- short summaries;
- supporting evidence snippets; and
- notes for potentially ambiguous cases.

These outputs were used only to support human review.

## Preliminary Annotation Fields

The LLM-assisted workflow supported extraction and organization of information
for fields such as:

- Testing Target
- System Level
- AI Paradigm
- Target Framework/Platform
- Technique Name
- Technique Family
- Input Generation Strategy
- Mutation Strategy
- Oracle Type
- Oracle Construction
- Failure Type
- Reported Limitations
- Threats to Validity
- Future Work
- Observed Gap
- Main Contribution
- Notes

The complete field definitions are available on the
[Annotation Schema page]({{ site.baseurl }}/methodology/annotation-schema.html).

## Two-Stage Human Validation

All preliminary annotations were subjected to human review.

### Stage 1: Annotator Review

An annotator compared the LLM-generated labels with the original paper.

The review focused on evidence from sections such as:

- Abstract
- Methodology
- Evaluation
- Discussion
- Limitations
- Conclusion

Unsupported, ambiguous, overly broad, or inconsistent labels were corrected
based on evidence from the original study.

The annotator also reviewed full-text eligibility and identified studies that:

- were non-fuzzing;
- were only weakly related to fuzzing;
- used AI to improve fuzzing of conventional software rather than fuzzing AI
  systems;
- fell outside the scope of AI-system testing; or
- lacked sufficient methodological or evaluation detail.

### Stage 2: Checker Validation

A checker independently reviewed:

- eligibility decisions;
- assigned labels;
- supporting evidence;
- agreement status;
- disagreement notes; and
- annotation justifications.

When the two LLM outputs differed, or when the annotator and checker identified
an uncertain case, the original paper was re-examined.

Disagreements were documented and resolved collaboratively before the dataset
was finalized.

## Annotator-Checker Agreement

The initial annotator-checker agreement was:

| Validation outcome | Count |
|---|---:|
| Agreements | 144 |
| Candidate studies reviewed | 208 |
| Initial agreement | **69.2%** |

We interpret the **144 of 208 agreement value (69.2%)** as a diagnostic measure
of annotation difficulty rather than as a formal inter-rater reliability
score.

The annotation task combined:

- full-text eligibility assessment;
- multi-label classification;
- target-dependent coding; and
- normalization of overlapping technical concepts.

The workflow also used checker validation followed by consensus resolution,
rather than independent final coding.

For these reasons, we did not treat the agreement value as a formal
inter-rater reliability statistic.

## Common Sources of Disagreement

Disagreements mainly involved borderline or overlapping cases, including:

- distinguishing AI-system fuzzing from AI-assisted fuzzing;
- determining whether a study contained a recognizable fuzzing-style workflow;
- identifying the primary testing target;
- distinguishing testing target from system level;
- separating input-generation strategy from mutation strategy;
- differentiating oracle type from failure type;
- assigning overlapping technique-family labels;
- distinguishing learning-based from LLM/prompt-guided approaches; and
- assigning multi-label oracle or failure categories.

Each disagreement was rechecked against the original paper and documented with
supporting notes or justification.

## Final Annotation Outcome

After:

- full-text eligibility review;
- annotator verification;
- checker validation;
- disagreement resolution; and
- duplicate-version removal,

the final corpus contained **125 primary studies**.

For these studies, the verified bibliographic and technical metadata formed the
analysis-ready dataset used in RQ1--RQ4.

## Role of LLMs in the Workflow

LLMs were used to support:

- evidence extraction;
- preliminary classification;
- summarization;
- organization of paper-level information; and
- identification of potentially inconsistent cases.

LLMs did **not** determine the final eligibility decisions or final taxonomy
labels.

All final classifications and interpretations were established through human
review, evidence checking, manual correction, and consensus resolution.

Further details on consistency checking and annotation safeguards are available
on the
[Annotation Quality Control page]({{ site.baseurl }}/methodology/quality-control.html).
