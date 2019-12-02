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
summary:
tags:
- EukRef
title: 'Classification guidelines'
---
**General guidelines**

*   Be conservative in your taxonomic annotation (e.g. Clades that are being annotated should normally be backed up by other analyses).
*   Use names that have been previously applied to groups in other publications.
*   Novel environmental clades identified here may be an exception, but must follow the <span style="text-decoration: underline;">Novel Environmental Clades</span> guidelines below.
*   In the case of empty levels, propagate from a low hierarchical level up to fill in blanks.
*   Use as many levels (ranks) as needed.
*   Always keep the name of the sequence from GenBank (this will be the species binomial or the clone name generally). This name can also go into the least inclusive column in your taxonomy unless you are correcting problems or it creates incongruencies.
*   If you have a genus that is paraphyletic, keep the binomial for the least inclusive column (species name) and annotate corrected genus name in genus column.
*   In cases of uncertainty you can label levels ambiguous.

Several options  to do if you run into problems

*   Search the literature for other publications (phylogenies or classification or taxonomic descriptions) that can guide your decision. You should assemble literature for your clade prior to annotating to guide your work overall, and search again when you become stuck.
*   Ask yourself, are you really annotating at the right level? (e.g. if 18S is not informative for the for the genus level for your group you should not add genus level annotations).
*   Describe your question in a post to the [EukRef Google group](https://groups.google.com/forum/#!forum/eukref).
*   Send your question to a taxonomic expert for your group (perhaps another [EukRef curator](http://eukref.org/curators/), your adviser, or an author of publications on your group). **[e-mail](mailto:info@eukref.org)** us if you need help finding an expert.

**Specific cases:**

<span style="text-decoration: underline;">Important clades that have no taxonomic name</span>

Clades that have formal taxon names but the larger clade does not have a name. Options:

*   If a name has been applied to a group previously, use this name.
*   If an informal name exists. Treat these like environmental sequence rules –

 * -if the existing informal name is generic (e.g. Clade A), a 3-4 letter prefix should be added to the existing informal name, similar to environmental clades in front of the clade name given in a publication.
 * -This name should be distinguishable from enviro clades. In the case clades were just numbered in a publication the name should be HAP_clade3 and NOT HAP3

*   If no informal name exists but the group is important and warrants a name you can apply a new informal name consisting of the 3-4 letter prefix and a clade name. Hopefully these cases will be very rare.

<span style="text-decoration: underline;">Naming Environmental clades</span>

*   Only name lineages that are:
    *   Well-supported by bootstrap / posterior probabilities or possibly by clear 18S sequence signatures.
    *   Composed of two or more clearly distinct sequence types, ideally from two or more different studies.
    *   <span style="color: #ff0000;">Do NOT name isolated sequences, especially long-branches.</span>

>Isolated sequences must be treated with caution, as they are likely to be chimeric or bad-quality sequence:
>*   <span style="color: #ff0000;">Do NOT name isolated sequences.</span>
>*   Rigorously check isolated sequences and remove any that are chimeric or poor-quality from your reference alignment.
>*   When isolated sequences look genuine (are not chimeras), they can be kept in the reference alignment because they may carry useful environmental information;
>*   Single-sequence 18S types that do not seem problematic should be identified simply by their clone name – they should not be named.

*   Use a 3-5 capital letters code matching the clade containing the environmental lineage. In many cases this will be an inclusive clade (e.g. many lineages of MAST or HAP Haptophytes).
*   Use numbers again after an underscore for sublineages (e.g. HAP3-2).
*   Number the lineages in some arbitrary order (for instance chronological order of their first appearance in a paper).
*   Even if a lineage later disappears, never re-use the same number again to avoid confusion (e.g. MAST5 no longer exists).

**If you have any question or suggestion please feel free to add it to the comment section below, visit our [forum](https://groups.google.com/forum/#!forum/eukref) or send us an [e-mail](mailto:info@eukref.org)**
