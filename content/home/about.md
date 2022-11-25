+++
widget = "blank"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 12  # Order that this section will appear.

title = "The PR2 database ecosystem"
subtitle = ""
+++

{{< figure library="true" src="tree_burki.png" class="img-lg" title="The eukaryotic tree. From Burki et al. 2019. The New Tree of Eukaryotes. Trends in Ecology & Evolution. DOI: 10.1016/j.tree.2019.08.008." lightbox="true" >}}

The PR<sup>2</sup> (Protist Ribosomal Reference) database ecosystem is a set of three interconnected 18S rRNA databases that are useful in particular for metabarcoding applications. This web site focuses on the PR<sup>2</sup> reference sequence database.

## The PR<sup>2</sup> reference sequence database

* Current version : 4.14.1  
* Last update : 25 November 2022  
* [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5031733.svg)](https://doi.org/10.5281/zenodo.5031733)
* Download: https://github.com/pr2database/pr2database/releases ![](https://img.shields.io/github/downloads/pr2database/pr2database/total.svg)
* [Web interface - NEW](https://app.pr2-database.org/pr2-database/)
* [Team](https://pr2-database.org/team/)

The PR<sup>2</sup> reference sequence database was initiated in 2010 in the frame of the BioMarks project from work that had developed in the previous ten years in the Plankton Group of the Station Biologique of Roscoff.  Its aim is to provide a reference database of carefully annotated 18S rRNA sequences using  eight unique taxonomic fields (from kingdom to species).  At present it contains almost [200,000 sequences](https://pr2database.github.io/pr2database/articles/pr2_01_stats.html#basic-statistics-1).  Although it focuses on protists, it also contains [sequences from metazoa, fungi and plants](https://pr2database.github.io/pr2database/articles/pr2_01_stats.html#division-level-1) as well a limited set 16S sequences from plastids and bacteria. A number of metadata fields are available for many sequences, including geo-localisation, whether it originates from a culture or a natural sample, host type etc... The annotation of PR<sup>2</sup> is performed by [experts]({{< ref "/documentation/PR2-taxonomic-groups.md" >}}) from each taxonomic groups.  One very important project in this respect is [EukRef]({{< ref "/eukref/about.md" >}}) which has recently decided to merge its effort with PR<sup>2</sup>. EukRef has built bioinformatics pipelines that have been used during three workshops dedicated to specific taxonomic groups.  As an example, part of the ciliate annotation originate from the first [EukRef workshop]({{< ref "/eukref/workshop_vancouver.md" >}}).

<!---
{{< figure src="https://pr2database.github.io/pr2database/articles/pr2_01_stats_files/figure-html/unnamed-chunk-9-1.png" class="img-sm" title="Representation of the different taxonomic groups within PR<sup>2</sup>." lightbox="true" >}}
-->

## The PR<sup>2</sup> primer database

* Current version : 1.1  
* Last update : 20 April 2022   
* Access:  https://app.pr2-primers.org
* [Contributors](https://pr2-database.org/team/#people_primers)

We have developed an interactive [pr2-primers database](https://app.pr2-primers.org/) focusing on the rRNA operon.  You can download primer and primer sets.  Primer pairs are evaluated against the PR<sup>2</sup> sequence database and you can test your own primers and primer sets. To know [more]({{< ref "/post/news/2021-01-18-pr2-primers.md" >}}).

## The metaPR<sup>2</sup> metabarcodes database

* Current version : 1.1  
* Last update : 30 April 2022  
* [![DOI](https://zenodo.org/badge/410160328.svg)](https://zenodo.org/badge/latestdoi/410160328)
* Access: https://shiny.metapr2.org
* [Contributors](https://pr2-database.org/team/#people_metapr2)

The metaPR<sup>2</sup> database contains processed 18S rRNA metabarcodes that are annotated with the PR<sup>2</sup> reference sequence database. Version 1.1 of the database contains 41 datasets corresponding to more than 4,000 samples and 90,000 ASVs. The database is accessible through both a web-based interface (https://shiny.metapr2.org) and an R package. To know [more]({{< ref "/post/news/2022-08-01-metapr2.md" >}}).

Citations
-----------

* Guillou, L., Bachar, D., Audic, S., Bass, D., Berney, C., Bittner, L., Boutte, C. et al. 2013. [The Protist Ribosomal Reference  database (PR<sup>2</sup>): a catalog of unicellular eukaryote Small Sub-Unit rRNA sequences with curated taxonomy](http://nar.oxfordjournals.org/lookup/doi/10.1093/nar/gks1160). Nucleic Acids Res. 41:D597–604.

* del Campo J., Kolisko M., Boscaro V., Santoferrara LF., Nenarokov S., Massana R., Guillou L., Simpson A., Berney C., de Vargas C., Brown MW., Keeling PJ., Wegener Parfrey L. 2018. [EukRef: Phylogenetic curation of ribosomal RNA to enhance understanding of eukaryotic diversity and distribution](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.2005849). PLOS Biology 16:e2005849. DOI: 10.1371/journal.pbio.2005849.

* Vaulot, D., Mahé, F., Bass, D., & Geisen, S. (2021). [pr2-primer : An 18S rRNA primer database for protists](https://onlinelibrary.wiley.com/doi/abs/10.1111/1755-0998.13465). Molecular Ecology Resources. DOI: 10.1111/1755-0998.13465

* Vaulot, D., Sim, C.W.H., Ong, D., Teo, B., Biwer, C., Jamy, M., Lopes dos Santos, A., 2022. [metaPR2: a database of eukaryotic 18S rRNA metabarcodes with an emphasis on protists](https://doi.org/10.1111/1755-0998.13674). Molecular Ecology Resources. DOI: 10.1111/1755-0998.13674





Issues and questions
-----------

* Send a message to the [PR2-database space on elements.io](https://matrix.to/#/#pr2-database:matrix.org)

* Report on [GitHub](https://github.com/vaulot/pr2_database/issues)

<!-- Place this tag where you want the button to render. https://buttons.github.io/-->
<a href="https://twitter.com/PR2database?ref_src=twsrc%5Etfw" data-show-count="false" class="twitter-follow-button">Follow @PR2database</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
