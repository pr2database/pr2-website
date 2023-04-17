---
authors:
- vaulot

categories:
- news
date: "2023-04-15"
weight: 10
draft: false
featured: false
projects: []
subtitle: ''
summary:Using PR2 reference database version 5.0.
tags:
- News
- Version
title: 'PR2-primers version 2.0.0'
---

We are very pleased to announce the new [pr2-primers](https://app.pr2-primers.org/) version 2.0.0. 

The major change is the use of [PR2 database version 5.0.0](https://app.pr2-database.org) that implements a [new taxonomy structure](https://pr2-database.org/documentation/pr2-taxonomy-9-levels/) with 9 levels instead of 8.  Moreover the inclusions of prokaryotic and plastid sequences in PR2 allows to test primers against these groups.

The application should also load faster because of the use the [qs R library](https://cran.r-project.org/web/packages/qs/vignettes/vignette.html) for file storage.

Finally 24 primers and 9 primer sets have been added to the database.

---

Please let us know of any problem you encounter with this release on [GitHub](https://github.com/pr2database/pr2-primers-shiny/issues).


