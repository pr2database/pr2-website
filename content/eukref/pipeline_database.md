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
title: 'Pipeline database'
---
During the curation phase, you will go back and forth between your tree, a tab delimited database file, and the literature to curate taxonomy strings and add environmental metadata. You should work with the database file in excel or similar program. Remember to save often and back up this file.

**Database Structure**:

| **Accession** | **Taxonomy** | **Name** | **Metadata** |

At its most basic, your database will consistent the GenBank accession number, taxonomy, species (or clone) name, and environmental metadata in tab delimited format. The taxonomy and environmental metadata will each be composed of multiple columns. You will modify these through your curation efforts using your tree and additional information as necessary. You must keep track of annotation decisions and sources in a notes file so these can be documented in publications and/or used as the reference in the future. In the curation pipeline, you used the script [eukref_gbmetadata.py](https://github.com/eukref/eukref/blob/master/eukref_gbmetadata.py) to pull most of the following information from GenBank. This is your starting point for manual curation.

<span style="text-decoration: underline;">**Structure of your  metadata database**</span>

 See example file on the ciliates [ciliates_metadata_db](https://raw.githubusercontent.com/eukref/curation/master/EukRef_Ciliophora/EUKREF-CILIOPHORA.tsv).

 **Accession**: In all cases use the GenBank accession number as the sequence identifier.

 **Taxonomy: see the EukRef [Classification guidelines](http://eukref.org/classification-guidelines/).**

*   <span style="text-decoration: underline;">Unlimited ranks:</span> The curated taxonomy should be included in your database as multiple columns, with each column being roughly equivalent in level (evolutionary distance). You can use as many columns as needed.
*   <span style="text-decoration: underline;">Gaps in the taxonomy</span>: Of course, not all lineages require the same number of ranks, so you will have gaps. Deal with these by repeating the rank below (column to the right). Blanks will cause problems during annotation.
*   <span style="text-decoration: underline;">Initial population of taxonomy</span>: Taxonomy strings can originally be populated using GenBank taxonomy.

For more information regarding Taxonomy check our **[Classification guidelines](http://eukref.org/classification-guidelines/)**.

**Name**: Species name or clone name from GenBank. Even if the species/genus name is wrong! You should correct the name in the taxonomy entries.

**Metadata**: Use the automatically entered metadata columns from the eukref_gbmetadata.py script as a starting point, and add the columns requested below.  You can add additional columns that are informative.  Information will come from the GenBank entry and also from the publications related to this sequence.  Columns requested document the origin of the sequence and the environmental information pertaining to this sequence. You will have several categories of metadata information. This information will enable you to make ecological insights from your database. We adopted standardized metadata annotation: [MIxS](http://wiki.gensc.org/index.php?title=MIMARKS) (Minimum Information about any (x) Sequence) and [EnvO](http://www.environmentontology.org/annotation-guidelines) (Environmental Ontology):

*   **source***: does this sequence come from a culture or an environmental sequence? Three options here: [culture | isolate | environmental]. You can add this information by parsing the source column.
*   <span style="color: #3366ff;">**env_material**</span>: The environmental material level refers to the material that was displaced by the sample, or material in which a sample was embedded, prior to the sampling event. Environmental material terms are generally mass nouns. Examples include air, soil, or water. EnvO (v 2013-06-14) terms can be found via the link: [www.environmentontology.org/Browse-EnvO](http://www.environmentontology.org/Browse-EnvO). You can add this information by parsing the environmental_sample column.
*   <span style="color: #3366ff;">**env_biome**</span>: Biomes are defined based on factors such as plant structures, leaf types, plant spacing, and other factors like climate. Biome should be treated as the descriptor of the broad ecological context of a sample. Examples include: desert, taiga, deciduous woodland, or coral reef. EnvO (v 2013-06-14) terms can be found via the link: [www.environmentontology.org/Browse-EnvO](http://www.environmentontology.org/Browse-EnvO). You can add this information by parsing the environmental_sample column.
*   <span style="color: #3366ff;">**biotic_relationship**</span>:  [free living|parasite|commensal|symbiont]. You can infer this information from the host column.
*   <span style="color: #3366ff;">**specific_host**</span>: For symbiotic lineages. Host taxonomy ID (taxid) from NCBI.  Should be automatically populated with eukref_gbmetadata.py script.  If it is not, search at [NCBI](http://www.ncbi.nlm.nih.gov/Taxonomy/taxonomyhome.html/) using the host as the query.
*   <span style="color: #3366ff;">**geo_loc_name**</span>: The geographical origin of the sample as defined by the country or sea name followed by specific region name. Country or sea names should be chosen from the [INSDC country list](http://insdc.org/country.html), or the [GAZ ontology (v 1.512)](http://purl.bioontology.org/ontology/GAZ). You can add this information by parsing the country and environmental_sample column.

>**source** **is** not MIMARKS items

**If you have any question or suggestion please feel free to add it to the comment section below, visit our [forum](https://groups.google.com/forum/#!forum/eukref) or send us an [e-mail](mailto:info@eukref.org)**
