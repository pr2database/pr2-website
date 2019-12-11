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
* [How to use the R package](./documentation/pr2-r-package/)

**SQLite database**

* [Download](https://github.com/pr2database/pr2database/releases/download/v4.12.0/pr2_version_4.12.0.sqlite.gz)

## PR2 primer database
We are also developing a [PR<sup>2</sup> primer database](https://github.com/pr2database/pr2-primers) focusing on the rRNA operon.

* [Primers used to amplify 18S rRNA](https://github.com/pr2database/pr2-primers/wiki/18S-rRNA-primers)
* [Primer sets (fwd/rev) used for metabarcoding of 18S rRNA](https://github.com/pr2database/pr2-primers/wiki/18S-rRNA-primer-sets)
