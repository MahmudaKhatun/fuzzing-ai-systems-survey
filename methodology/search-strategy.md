---
layout: default
title: Search Strategy
---

# Search Strategy

[← Back to Home]({{ site.baseurl }}/)

[← Data Collection]({{ site.baseurl }}/methodology/data-collection.html)

This page provides the complete search-query design used in the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The literature search covered the **January 2015–February 2026 search
window** and was designed to identify studies on fuzzing AI systems across
models, frameworks and libraries, compiler backends, and integrated
AI-enabled applications.

## Search-Query Design

The search strategy was designed to maximize recall and reduce the risk of
missing relevant studies.

Because terminology varies across research communities, the search considered
not only papers that explicitly used the term *fuzzing*, but also related
terms associated with:

- fuzz testing;
- coverage-guided fuzzing;
- coverage-guided testing;
- mutation testing;
- grey-box fuzzing;
- black-box fuzzing;
- robustness testing;
- machine learning;
- deep learning;
- neural networks;
- large language models;
- foundation models;
- DL frameworks and libraries;
- AI runtimes;
- model deployment; and
- neural-network compilers.

The broad search intentionally retrieved fuzzing-related and
fuzzing-adjacent studies. These candidates were later evaluated using the
predefined inclusion and exclusion criteria, particularly the requirement
that an included study contain a recognizable fuzzing-style workflow
involving:

1. input generation or mutation;
2. target execution;
3. monitoring, feedback, or failure signals; and
4. failure reporting.

## Database-Specific Search Strategy

Search interfaces differ in:

- supported Boolean syntax;
- query-length limits;
- phrase-search behavior;
- indexing coverage;
- export functionality; and
- retrieval limits.

Therefore, we used:

- a **comprehensive query** for Semantic Scholar, Google Scholar, Scopus, and
  ScienceDirect; and
- a **simplified query** for the ACM Digital Library.

Both query forms retained the same conceptual focus on fuzzing and
AI-system testing.

## Comprehensive Search Query

The following query was used for Semantic Scholar, Google Scholar, Scopus,
and ScienceDirect.

```text
(Fuzzing OR
"Fuzz Testing" OR
"Coverage-Guided Fuzzing" OR
"Coverage-Guided Testing" OR
"Mutation Testing" OR
"Greybox Fuzzing" OR
"Blackbox Fuzzing")

AND

("Machine Learning" OR
"Deep Learning" OR
"Neural Network" OR
"Deep Neural Network" OR
DNN OR
CNN OR
RNN OR
LSTM OR
Transformer OR
"Large Language Model" OR
LLM OR
"Foundation Model" OR
GAN)

AND

(TensorFlow OR
PyTorch OR
Keras OR
MXNet OR
Caffe OR
ONNX OR
TorchScript OR
TensorRT OR
OpenVINO OR
JAX OR
MindSpore)

AND

("Deep Learning Libraries" OR
"Model Inference" OR
"AI Runtime" OR
"Model Deployment" OR
"Model Serving" OR
"ML Pipeline" OR
"Training Pipeline" OR
"Neural Network Compiler")
```

## Simplified Search Query for ACM Digital Library

The ACM Digital Library used a shorter query because of query-length and
formatting limitations in the advanced-search interface.

```text
(Fuzzing OR
"Fuzz Testing" OR
"Coverage-Guided Testing" OR
"Coverage-Guided Fuzzing" OR
"Mutation-Based Testing" OR
"Mutation Testing" OR
"Greybox Fuzzing" OR
"Blackbox Fuzzing")

AND

("Deep Neural Networks" OR
"Neural Networks" OR
"Machine Learning" OR
"Deep Learning" OR
"Large Language Models" OR
LLM OR
Transformer OR
"Foundation Model" OR
"Deep Learning Frameworks")
```

## Search Recall and Scope

Although the queries were intentionally broad, database search alone could
still miss relevant studies because AI-system fuzzing uses fragmented
terminology.

For example, relevant work may be described using terms such as:

- robustness testing;
- differential testing;
- compiler testing;
- metamorphic testing;
- adversarial testing;
- test generation; or
- coverage-guided testing.

Some relevant studies may therefore omit one or more search concepts from
their titles, abstracts, or indexed metadata.

To reduce this risk, database search was complemented by:

- manual title and abstract screening;
- backward snowballing;
- forward snowballing; and
- full-text eligibility assessment.

Detailed snowballing procedures are available on the
[Backward and Forward Snowballing page]({{ site.baseurl }}/methodology/snowballing.html).

## Search Sources and Export Mechanisms

The queries were applied across five scholarly sources:

| Scholarly source | Search or export mechanism |
|---|---|
| ACM Digital Library | Advanced search interface and CSV export |
| ScienceDirect | Elsevier Search API |
| Semantic Scholar | Semantic Scholar API and automated retrieval |
| Google Scholar | Publish or Perish |
| Scopus | Publish or Perish |

The resulting records were normalized and consolidated before
deduplication and multi-stage screening.

Further details are available on the
[Data Collection page]({{ site.baseurl }}/methodology/data-collection.html).
