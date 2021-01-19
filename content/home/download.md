+++
# A Recent Blog Posts section created with the Pages widget.
# This section displays recent blog posts from `content/`.

widget = "blank"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 15  # Order that this section will appear.

title = "Get the PR2 database"
subtitle = ""
+++
## PR2 sequence database
The PR<sup>2</sup> database is provided in 3 different formats:  

**Flat files for use with mothur, QIIME2, dada2, blast etc...**   

* [Download latest release](https://github.com/pr2database/pr2database/releases)
* [Details of file provided](./documentation/pr2-files/)

**R package pr2database**  

* Use the following code under R
``` r
install.packages(devtools)
devtools::install_github("pr2database/pr2database")
```
* [How to use the R package](https://pr2database.github.io/pr2database/articles/pr2database.html)

**SQLite database**

* [Download](https://github.com/pr2database/pr2database/releases)

* [How to use the SQLite database](./documentation/pr2-sqlite/)

## PR2 primer database
We have developed an interactive [pr2-primers database](https://app.pr2-primers.org/) focusing on the rRNA operon.  You can download primer and primer sets.  Primer pairs are evaluated agains the PR<sup>2</sup> sequence database.


