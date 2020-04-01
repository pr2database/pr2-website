---
authors:
- vaulot
categories:
- documentation
date: "2020-04-01"
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2020-04-01"
projects: []
subtitle: ''
summary: Instruction to download and use
tags:
- Documentation
- Database
- Files
title: 'SQLite database'
---

## File provided

* **pr2_version_x.y.z.sqlite.gz**: compressed version of the PR<sup>2</sup> database under SQLite.

## Database structure

Four tables are provided

* pr2_main
* pr2_sequence  
* pr2_metadata
* pr2_taxonomy

Please see [here]({{< ref "/documentation/PR2-structure" >}}) for the detailed structure of the database

## Using the database

### R

You can use the package [RSQLite](https://db.rstudio.com/databases/sqlite/) to interact with the database.

### DBeaver database interface

We recommend using [DBeaver](https://dbeaver.io/), an open source Universal database interface that can read a variety of database formats (MySQL, MariaSQL, SQlite...)

{{< figure library="true" src="pr2_sqlite_01.png" class="img-lg" title="Using the DBeaver interface to read the  PR<sup>2</sup> SQLite database." lightbox="true" >}}
