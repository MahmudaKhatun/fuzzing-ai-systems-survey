---
layout: default
title: Data Collection
---

# Data Collection

[← Back to Home]({{ site.baseurl }}/)

This page provides extended details of the data-collection process used in the
survey *Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The survey identified candidate studies through a systematic search conducted
across multiple scholarly sources. The search covered the period from
January 2015 to February 2026 and was followed by metadata consolidation,
normalization, deduplication, multi-stage screening, quality assessment, and
backward and forward snowballing.

## Data Sources

We searched five scholarly sources to improve coverage:

- ACM Digital Library
- ScienceDirect
- Scopus
- Semantic Scholar
- Google Scholar

These sources collectively cover major publication venues in software
engineering, software testing, security, systems, and artificial intelligence.

ACM Digital Library and ScienceDirect provided direct access to many relevant
conference and journal publications. Scopus, Semantic Scholar, and Google
Scholar broadened coverage and helped identify studies that were not indexed
consistently across individual publisher databases. IEEE-related publications
were also captured through indexing services such as Scopus and Google Scholar.

## Collection Process

The collection procedure differed across sources because of variations in
search interfaces, API availability, query syntax, and export mechanisms.

- **ACM Digital Library:** searched through the advanced search interface;
  records were exported in CSV format.
- **ScienceDirect:** searched through the Elsevier Search API.
- **Semantic Scholar:** queried through an automated workflow using the
  Semantic Scholar API.
- **Google Scholar:** queried and exported using Publish or Perish.
- **Scopus:** queried and exported using Publish or Perish.

All exported records were standardized into a common tabular format containing
the following fields:

- Title
- Authors
- Publication year
- Source
- Abstract
- DOI
- URL
- Citation information

The normalized records were then consolidated into a single candidate dataset
using a Python-based processing pipeline.

## Paper-Collection Workflow

![Paper collection process used in the survey]({{ site.baseurl }}/assets/images/paper-collection-process.png)

*Figure 1. Paper-collection process used to construct the preliminary candidate
pool for the survey.*

The workflow integrated records from all five scholarly sources, normalized
their metadata, and consolidated them into a unified dataset before screening
and eligibility assessment.

## Distribution Across Scholarly Sources

The initial literature search retrieved **3,905 records** across five
scholarly sources. Figure 2 shows the source-wise distribution of the
collected records.

![Distribution of collected records across scholarly sources]({{ site.baseurl }}/assets/images/database-source-distribution.png)

*Figure 2. Distribution of the 3,905 records collected across the five
scholarly sources used in the initial literature search.*

Semantic Scholar contributed the largest number of records (1,242), followed
by ACM Digital Library (1,000), Google Scholar (844), ScienceDirect (619),
and Scopus (200). The smaller Scopus count reflects tool and export
constraints.

Using multiple sources improved coverage and reduced dependence on the
indexing behavior or retrieval limits of any single database.

## Metadata Normalization and Deduplication

Because metadata formats differed across sources, the exported records were
normalized before filtering and deduplication.

The preprocessing workflow included:

1. normalization of common metadata fields, including title, authors, year,
   venue, abstract, DOI, and URL;
2. title-based duplicate detection;
3. DOI-based matching and deduplication; and
4. consolidation of duplicate records across scholarly sources.

After preprocessing and deduplication, **1,996 unique records** remained for
screening.

## Relationship to the Main Selection Process

The 1,996 unique records formed the starting point for the multi-stage
screening process reported in the main paper.

Subsequent stages included:

- automated keyword filtering;
- precision-oriented filtering;
- manual title and abstract screening;
- backward and forward snowballing;
- quality and eligibility assessment;
- full-text screening; and
- duplicate-version removal.

These steps resulted in the final corpus of **125 primary studies**.

Detailed inclusion and exclusion criteria, screening stages, and snowballing
procedures are available on the
[Study Selection and Multi-Stage Filtering page]({{ site.baseurl }}/methodology/study-selection.html).
