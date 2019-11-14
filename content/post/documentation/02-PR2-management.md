---
authors:
- vaulot
categories:
- documentation
date: "2018-08-10"
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-08-28"
projects: []
subtitle: ''
summary: The PR2 database is mostly managed by R scripts.
tags:
- Documentation
title: 'Database management'
---

## Accessing

The PR2 database is formatted as MySQL database which is accessed by the [Navicat software](https://www.navicat.com/)


## Importing and verifying new or updated data

The management of the PR2 database is done almost completely under R using in particular the tidyverse and Biostrings libraries.

Here are some examples of scripts:

* [version 4.10](https://vaulot.github.io/pr2/PR2_update_4.10.0_pr2_original.html)
* [version 4.9](https://vaulot.github.io/pr2/PR2_update_4.9.0_DinoRef.html)
