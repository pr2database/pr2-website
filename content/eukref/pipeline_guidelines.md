---
authors:
- delcampo
categories:
- eukref
date: "2019-08-08"
weight: 10
draft: false
featured: false
lastmod: "2019-11-29"
projects: []
subtitle: ''
summary: Guidelines to perform the taxonomic annotation
tags:
- EukRef
title: 'Taxonomy classification guidelines'
---
#### General guidelines
* EukRef follows PR2 and uses a [9 level taxonomy](https://pr2-database.org/documentation/pr2-taxonomy-9-levels/) (domain, supergroup, division, subdivision, class, order, family, genus, species).
* You can navigate the existing taxonomy on the PR2 web interface.
* Please make yourself familiar with the [PR2 rules](https://pr2-database.org/documentation/pr2-structure/):
  * Taxonomic names cannot appear twice at different levels. For example “Stramenopiles” cannot appear at both the supergroup and Division levels.
  * Taxa names should only contain letters, numbers (to remove ambiguities) and underscore.
  * The key linking sequences to taxonomy is the **species level**.  So the species level should always be annotated.
*   Be conservative in your taxonomic annotation (e.g. clades that are being annotated should normally be backed up by other analyses).
*   Use names that have been previously applied to groups in other publications. You can also consult other databases such as WoRMS, AlgaeBase). In particular try to stick to the taxonomic conventions for your community (for example for algae taxa ending by _phyceae_ correspond to classes).
*   Novel environmental clades identified here may be an exception, but must follow the <span style="text-decoration: underline;">Novel Environmental Clades</span> guidelines below.
*   In the case of empty levels, propagate from a high hierarchical level down to fill in blanks. Use the PR2 convention, i.e. if a level is unknown you use the level above with an _X appended and the propagate down with _XX, _XXX etc…
*   If you have a genus that is paraphyletic, keep the binomial for the least inclusive column (species name) and annotate corrected genus name in genus column.You can create several genera on the model genus_1, genus_2 etc…


In case you run into problems, several options are available.

*   Search the literature for other publications (phylogenies or classification or taxonomic descriptions) that can guide your decision. You should assemble literature for your clade prior to annotating to guide your work overall, and search again when you become stuck.
*   Ask yourself, are you really annotating at the right level? (e.g. if 18S is not informative for the for the genus level for your group you should not add genus level annotations).
*   Describe your question in a post to the [element.io EukRef discussion group](https://matrix.to/#/!MmBdeJsUKnndAPaVYe:matrix.org?via=matrix.org).
*   Send your question to a taxonomic expert for your group (perhaps another [PR2 curator](https://pr2-database.org/team/), your adviser, or an author of publications on your group). [E-mail](mailto:fonamental@gmail.com) us if you need help finding an expert.

#### Specific cases

###### Important clades that have no taxonomic name

Clades that have formal taxon names but the larger clade does not have a name. Options:

* If a name has been applied to a group previously, use this name.
* If an informal name exists. Treat these like environmental sequence rules.
* If the existing informal name is generic (e.g. clade A or clade 1), a prefix should be added to the existing informal name based on the higher taxonomy. This name should be distinguishable from any other environmental clades. Use long names rather than short names. As an exemple use "Haptophyta_clade3" and NOT "HAP3".
* If no informal name exists but the group is important and warrants a name you can apply a new informal name consisting of a prefix based on the next higher level that has a name and a clade name. Hopefully these cases will be very rare.

###### Naming Environmental clades

Only name lineages that are:

* Well-supported by bootstrap / posterior probabilities or possibly by clear 18S sequence signatures.
* Composed of two or more clearly distinct sequence types, ideally from two or more different studies.
* If they are composed from only one study, make sure that the sequences are from different samples.
* **<span style="color: #ff0000;">Do NOT create clades from isolated sequences, especially long-branches.</span>**

For the name, use the rules above plus:

* Number related lineages in some arbitrary order (for instance chronological order of their first appearance in a paper).
* Even if a lineage later disappears, never re-use the same number again to avoid confusion (e.g. MAST5 no longer exists and the name should not be re-used).

###### Isolated sequences
Isolated sequences must be treated with caution, as they are likely to be chimeric or bad-quality sequence:

*   Rigorously check isolated sequences and remove any that are chimeric or poor-quality from your reference alignment.
*   When isolated sequences look genuine (are not chimeras), they can be kept in the reference alignment because they may carry useful environmental information;
*   Single-sequence 18S types that do not seem problematic should be identified by the lowest group to which they can be assigned (for example, Dinophyceae_XXX_sp.).  This annotation should be done at the **species level**.

If you have any question or suggestion, please post it to the [element.io EukRef discussion group](https://matrix.to/#/!MmBdeJsUKnndAPaVYe:matrix.org?via=matrix.org).
