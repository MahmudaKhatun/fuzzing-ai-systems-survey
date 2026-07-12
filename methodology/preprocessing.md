---
layout: default
title: Data Preprocessing
---

# Data Preprocessing

[← Back to Home]({{ site.baseurl }}/)

[← Data Collection]({{ site.baseurl }}/methodology/data-collection.html)

This page provides extended details of the metadata normalization,
consolidation, and deduplication process used before study screening in the
survey *Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The initial literature search retrieved **3,905 records** from ACM Digital
Library, ScienceDirect, Scopus, Semantic Scholar, and Google Scholar.
Because these sources used different metadata formats, the exported records
were standardized before filtering and eligibility assessment.

## Metadata Consolidation

Records collected from the five scholarly sources were combined into a
single dataset.

The consolidated dataset used a common structure containing the following
fields:

| Metadata field | Description |
|---|---|
| Title | Title of the study |
| Authors | Listed study authors |
| Publication year | Year associated with the publication |
| Venue | Conference, journal, workshop, or preprint venue |
| Source | Scholarly database from which the record was retrieved |
| Abstract | Available abstract text |
| DOI | Digital Object Identifier, when available |
| URL | Publisher, indexing, or publication link |
| Citation information | Citation metadata available from the source |

Standardizing these fields enabled records from different databases to be
compared and processed consistently.

## Metadata Normalization

Metadata formats differed across sources in field names, ordering, missing
values, and formatting conventions.

The normalization process included:

1. mapping source-specific fields to the common metadata schema;
2. standardizing title information for duplicate comparison;
3. consolidating author and publication information;
4. retaining DOI and URL information when available;
5. standardizing publication-year fields; and
6. preserving source information to support traceability.

The normalized records were then combined into a unified tabular dataset
using a Python-based processing workflow.

## Duplicate Detection

Because the same publication could appear in multiple scholarly databases,
duplicate removal was necessary before screening.

We used two primary matching mechanisms.

### Title-Based Duplicate Detection

Study titles were compared across the combined dataset to identify records
that referred to the same publication.

Title-based matching was useful when:

- the same study appeared in multiple databases;
- DOI information was unavailable;
- DOI values were missing from one or more records; or
- metadata fields differed across indexing sources.

Potential duplicate records identified through title matching were
consolidated before screening.

### DOI-Based Matching

DOI values were used as a second identifier for duplicate detection.

Records sharing the same DOI were treated as references to the same study,
even when differences existed in:

- title capitalization;
- author formatting;
- venue information;
- source-specific metadata; or
- URL structure.

Using both title-based and DOI-based matching reduced the risk of retaining
duplicate database records.

## Preprocessing Outcome

The preprocessing pipeline reduced the initial dataset as follows:

| Processing stage | Number of records |
|---|---:|
| Records retrieved from all sources | 3,905 |
| Unique records after normalization and deduplication | **1,996** |
| Duplicate or overlapping records removed | 1,909 |

The resulting **1,996 unique records** formed the input to the multi-stage
screening process.

## Relationship to Study Selection

After preprocessing, the 1,996 unique records were evaluated through:

1. automated keyword filtering;
2. precision-oriented filtering;
3. manual title and abstract screening;
4. backward and forward snowballing;
5. quality and eligibility assessment;
6. full-text eligibility screening; and
7. duplicate-version removal.

Detailed screening and eligibility procedures are available on the
[Study Selection and Multi-Stage Filtering page]({{ site.baseurl }}/methodology/study-selection.html).

The preprocessing stage removed duplicate database records before screening.
A separate final consistency check was later used to remove duplicate study
versions, such as cases in which both a preprint and a published version of
the same work remained in the candidate corpus.
