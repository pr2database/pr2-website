+++
# A Recent Blog Posts section created with the Pages widget.
# This section displays recent blog posts from `content/post/`.

widget = "blank"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 15  # Order that this section will appear.

title = "Get the PR2 database"
subtitle = ""
+++
Current version : 4.12.0  
Last update : 8 August 2019  
DOI : [10.6084/m9.figshare.5913181](https://doi.org/10.6084/m9.figshare.5913181)  

The PR<sup>2</sup> database is provided in 3 different formats:  

**Flat files for use with mothur, dada2, blast etc...**   

* [Download latest release](https://github.com/pr2database/pr2database/releases)
* [Details of file provided](./post/documentation/03-pr2-files/)

**R package pr2database**  

* Use the following code under R
``` r
install.packages(devtools)
devtools::install_github("pr2database/pr2database")
```
* [Examples of use](./post/documentation/pr2-r-database-package/)

**SQLite database**

* [Download](https://github.com/pr2database/pr2database/releases/download/v4.12.0/pr2_version_4.12.0.sqlite.gz)


Citation
-----------

Guillou, L., Bachar, D., Audic, S., Bass, D., Berney, C., Bittner,
    L., Boutte, C. et al. 2013. [The Protist Ribosomal Reference
    database (PR<sup>2</sup>): a catalog of unicellular eukaryote Small
    Sub-Unit rRNA sequences with curated
    taxonomy](http://nar.oxfordjournals.org/lookup/doi/10.1093/nar/gks1160).
    Nucleic Acids Res. 41:D597–604.

Issues
-----------

Report on [GitHub](https://github.com/vaulot/pr2_database/issues)
