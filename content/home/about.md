+++
widget = "blank"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 12  # Order that this section will appear.

title = "About PR2"
subtitle = ""
+++

{{< figure library="true" src="tree_burki.png" class="img-lg" title="The eukaryotic tree. From Burki et al. 2019. The New Tree of Eukaryotes. Trends in Ecology & Evolution. DOI: 10.1016/j.tree.2019.08.008." lightbox="true" >}}

Current version : 4.14.0  
Last update : 25 June 2021  
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5031733.svg)](https://doi.org/10.5281/zenodo.5031733)

## The PR<sup>2</sup> sequence database
The PR<sup>2</sup> sequence database was initiated in 2010 in the frame of the BioMarks project from work that had developed in the previous ten years in the Plankton Group of the Station Biologique of Roscoff.  Its aim is to provide a reference database of carefully annotated 18S rRNA sequences using  eight unique taxonomic fields (from kingdom to species).  At present it contains about 184,000 sequences. A number of metadata fields are available for many sequences, including geo-localisation, whether it originates from a culture or a natural sample, host type etc... The annotation of PR2 is performed by [experts]({{< ref "/documentation/PR2-taxonomic-groups.md" >}}) from each taxonomic groups.  One very important project in this respect is [EukRef]({{< ref "/eukref/about.md" >}}) which has recently decided to merge its effort with PR<sup>2</sup>. EukRef has built bioinformatics pipelines that have been used during three workshops dedicated to specific taxonomic groups.  As an example, part of the ciliate annotation originate from the first [EukRef workshop]({{< ref "/eukref/workshop_vancouver.md" >}}).


{{< figure src="https://pr2database.github.io/pr2database/articles/pr2_01_stats_files/figure-html/unnamed-chunk-9-1.png" class="img-sm" title="Representation of the different taxonomic groups within PR<sup>2</sup>." lightbox="true" >}}

## The PR<sup>2</sup> primer database

We have developed in 2020 an interactive [pr2-primers database](https://app.pr2-primers.org/) focusing on the rRNA operon.  You can download primer and primer sets.  Primer pairs are evaluated against the PR<sup>2</sup> sequence database and you can test your own primers.

Citations
-----------

Guillou, L., Bachar, D., Audic, S., Bass, D., Berney, C., Bittner, L., Boutte, C. et al. 2013. [The Protist Ribosomal Reference     database (PR<sup>2</sup>): a catalog of unicellular eukaryote Small Sub-Unit rRNA sequences with curated taxonomy](http://nar.oxfordjournals.org/lookup/doi/10.1093/nar/gks1160). Nucleic Acids Res. 41:D597–604.

del Campo J., Kolisko M., Boscaro V., Santoferrara LF., Nenarokov S., Massana R., Guillou L., Simpson A., Berney C., de Vargas C., Brown MW., Keeling PJ., Wegener Parfrey L. 2018. [EukRef: Phylogenetic curation of ribosomal RNA to enhance understanding of eukaryotic diversity and distribution](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.2005849). PLOS Biology 16:e2005849. DOI: 10.1371/journal.pbio.2005849.

Issues
-----------

Report on [GitHub](https://github.com/vaulot/pr2_database/issues)

<!-- Place this tag where you want the button to render. https://buttons.github.io/-->
<a href="https://twitter.com/PR2database?ref_src=twsrc%5Etfw" data-show-count="false" class="twitter-follow-button">Follow @PR2database</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
