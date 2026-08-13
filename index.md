---
layout: default
title: Fuzzing AI Systems
---

# Fuzzing AI Systems

## Foundations, Techniques, and Open Challenges

This website provides companion materials for our systematic survey of
fuzzing techniques for AI systems.

The survey synthesizes 125 primary studies and examines the research
landscape, testing targets, technique families, input-generation and mutation
strategies, test oracles, failure types, recurring challenges, and future
research directions.

## Companion Materials

### Background

- [Extended Background]({{ site.baseurl }}/background/extended-background.html)
- [Boundary with Related Testing Techniques]({{ site.baseurl }}/background/boundary-related-techniques.html)
- [Extended Taxonomy Definitions]({{ site.baseurl }}/background/taxonomy-definitions.html)

### Methodology

- [Data Collection]({{ site.baseurl }}/methodology/data-collection.html)
- [Search Strategy]({{ site.baseurl }}/methodology/search-strategy.html)
- [Data Preprocessing]({{ site.baseurl }}/methodology/preprocessing.html)
- [Study Selection and Multi-Stage Filtering]({{ site.baseurl }}/methodology/study-selection.html)
- [Backward and Forward Snowballing]({{ site.baseurl }}/methodology/snowballing.html)
- [Annotation Schema]({{ site.baseurl }}/methodology/annotation-schema.html)
- [LLM-Assisted Annotation]({{ site.baseurl }}/methodology/llm-annotation.html)
- [Quality Control and Manual Validation]({{ site.baseurl }}/methodology/quality-control.html)

### Results

- [Chronological Evolution]({{ site.baseurl }}/results/chronological-evolution.html)
- [Venue Distribution]({{ site.baseurl }}/results/venue-distribution.html)
- [Extended Technique-Family Analysis]({{ site.baseurl }}/results/technique-families.html)
- [Technique-to-Study Mapping]({{ site.baseurl }}/results/technique-study-mapping.html)
- [Oracle-to-Study Mapping]({{ site.baseurl }}/results/oracle-study-mapping.html)
- [Failure-to-Study Mapping]({{ site.baseurl }}/results/failure-study-mapping.html)
- [Primary Studies]({{ site.baseurl }}/results/primary-studies.html)

### Discussion

- [Observation-to-Take-away Mapping]({{ site.baseurl }}/discussion/observation-takeaway-mapping.html)
- [Extended Challenge Synthesis]({{ site.baseurl }}/discussion/challenge-synthesis.html)

## Survey Paper

The submitted preprint version of the survey paper is available through the following public records:

- [Preprints.org version](https://www.preprints.org/manuscript/202608.0874/v1)
- [HAL Open Archive version](https://hal.science/hal-05695635)

This version corresponds to the manuscript submitted to *ACM Computing Surveys*
and may differ from the final published version after peer review.

## Replication Package

The replication package is available on
[Zenodo](https://doi.org/10.5281/zenodo.21022814).

It includes the selected-study list, extracted metadata, annotation schema,
normalized taxonomy labels, intermediate screening files, LLM-assisted
annotation outputs, figure sources, and analysis scripts.

Full-text PDFs of the reviewed studies are not redistributed because of
copyright restrictions.

## Citation

If you use this survey, companion website, or replication package, please cite:

Mahmuda Khatun, Mostafijur Rahman Akhond, Wuyang Dai, Gias Uddin, and Song Wang. 2026. *Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*. Preprints.org. https://www.preprints.org/manuscript/202608.0874/v1

```bibtex
@misc{khatun2026fuzzing,
  title     = {Fuzzing AI Systems: Foundations, Techniques, and Open Challenges},
  author    = {Khatun, Mahmuda and Akhond, Mostafijur Rahman and Dai, Wuyang and Uddin, Gias and Wang, Song},
  year      = {2026},
  publisher = {Preprints.org},
  doi       = {10.20944/preprints202608.0874.v1},
  url       = {https://www.preprints.org/manuscript/202608.0874/v1},
  note      = {Also available at HAL: https://hal.science/hal-05695635}
}
```

