---
authors:
- vaulot
categories:
- annotation
date: "2018-08-20"
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-11-21"
projects: []
tags:
- Documentation
- Database
- Taxonomy
title: 'How to contribute annotations'
subtitle: ''
summary: 'Detailed explanation for simple annotations'
---

## Steps

1. Contact one member of the [Core Team]({{< ref "/#people" >}})
2. Explain which group you want to annotate. It can be a genus, a class or any other taxonomic level.
3. We will send you an Excel file and a fasta file containing all existing  PR<sup>2</sup> sequences for the group you are expert in.
4. Follow the instructions below  to update or add data.
5. Send back the updated Excel file
6. Your contribution will be added to the next release of PR<sup>2</sup> (we are doing 2 to 3 releases per year).
7. You will be acknowledged as a [contributor]({{< ref "team" >}}) on the PR<sup>2</sup> web site


## Files provided

Two files will be provided to you

* An excel file with 2 sheets (taxonomy, sequences)
* A fasta file with the current t

Please edit the Excel file by marking all your changes in **yellow**.

### Excel - Taxonomy

{{< figure library="true" src="pr2_export_excel_taxonomy.png" class="img-lg" title="Taxonomy sheet." lightbox="true" >}}

* This sheet provides a summary of the taxonomy of the group with the number of sequences for each species (n).

### Excel - Sequences

{{< figure library="true" src="pr2_export_excel_sequences.png" class="img-lg" title="Sequences sheet." lightbox="true" >}}

* Each sequence has a unique identifier (pr2_accession) which is based on the GenBank accession (genbank_accession).
* For each sequence, the full taxonomic path is provided along with metadata (see [here]({{< ref "/documentation/pr2-fields" >}}) for a full description of the fields).

## Modifying or adding entries

### Excel - Taxonomy

{{< figure library="true" src="pr2_export_excel_taxonomy_change.png" class="img-lg" title="Taxonomy sheet - example of modification." lightbox="true" >}}

* You can change the ranks (supergroup to order) if necessary but you must make sure that you follow exactly the PR2 conventions which are detailed [here (see the second paragraph)]({{< ref "/documentation/pr2-structure" >}}). In particular, any taxonomic name can only appear once.  Use the \_X convention to distinguish different levels with the same name.
* You can also add new species as needed.

### Excel - Sequences

{{< figure library="true" src="pr2_export_excel_sequences_changes.png" class="img-lg" title="Update sequence entries." lightbox="true" >}}

* You can modify the taxonomy of a given entry or add new metadata.  If your metadata do not fit the existing columns, just add more columns and we will see how to incorporate them.
* Please see the figure above for some examples of changes
    * 1 - These entries are unchanged
    * 2 - These entries have been reassigned to a new species
    * 3 - These are new entries. Provide the following information
      * genbank_accession. We will download the sequence and all genbank metadata, so no need for you to do it
      * taxonomy assignation.  If the species is already present in the database you can just provide the species name
      * if the sequence is not limited to the 18S, but also contains the ITS, please provide the coordinates on the sequence of the start and end of the 18S rRNA gene.
    * 4 - You can also indicate whether the new sequence is a reference sequence. Reference sequences are have a high quality, preferentially full length and are representative a given taxon.


## Related information

* [Database structure]({{< ref "/documentation/pr2-structure" >}})
* [Detailed description of the fields]({{< ref "/documentation/pr2-fields" >}})