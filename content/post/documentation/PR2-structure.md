---
authors:
- vaulot
categories:
- documentation
date: "2018-08-12"
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-08-12"
projects: []
subtitle: ''
summary: Database and taxonomy structure
tags:
- Documentation
title: 'Database structure'
---
## Database structure (tables and fields)
Table | Fields | Comment  
--- | ---  | ---
pr2_main | pr2_accession, genbank_accession, species, editing hitory |  
pr2_sequence | genbank_accession, sequence | linked to pr2_main by genbank_accession  
pr2_metadata | metadata from GenBank and from published references |  linked to pr2_main by genbank_accession
pr2_taxonomy | kingdom -> species, editing history |  linked to pr2_main by species

![pr2 database structure](./../pr2_database_structure_4_9_0.png)

## Taxonomy structure
* 8 levels : Kingdom / Supergroup / Division / Class / Order / Family / Genus / Species
* All taxonomy paths are unique. For example for a given Class, all higher levels are similar (Division -> Supergroup -> Kingdom)
* No taxon can appear at different levels. For example "Stramenopiles" cannot appear at both the Supergroup and Division levels. 

#### Rules for naming taxonomic levels
* No space (use underscore).  For example Home_sapiens
* If species is not known use "Genus_sp." (note the . after sp).  The Genus level can be a level with Xs (see next rule): e.g. "Stramenopiles_XXXX_sp.",
* If level _i_ is unknown
     * if level _i-1_ is known, use level _i-1_ followed by "_X" , e.g. "Stramenopiles_X" at Division level
     * if level _i-1_ is unknown, use level _i-1_ followed by "X" , e.g. "Stramenopiles_XX" at Class level

## Rules for sequences
* Minimum length = 500 bp
* Maximum number of ambiguities (N) = 20
* No more than 2 consecutives N (so sequences such as ..ATGNNNAT.. are removed)

## Construction of PR2 id (pr2_accession)
Accession.Start.End_X  
For example AF530536.1.1695_U
* AF530536 : GenBank accession number
* 1 : Start of the 18S rRNA in the GenBank sequence
* 1695 : Start of the 18S rRNA in the GenBank sequence
* X can take any of the following values  
       * G: genomic sequence containing a described intron (rDNA)  
       * R: the previous genomic rRNA sequence, without the intron(s)  
       * U: no intron described, but intron(s) may be present  
       * UC: introns were detected in silico and removed from the sequence (putative rRNA)]  


#### History of database structure changes

PR2 version | Table | Field | Action | Comment  
--- | --- | --- | ---  | ---
4.12.0 | pr2_main | gene  | A | 18S_RNA, 16S_RNA
| | | organelle | A |  nucleus, plastid, mitochondria, nucleomorph, apicoplast (left empty for cyanobacteria)
| | pr2_metadata | gb_organelle | A |  import the corresponding gb field
| | | pr2_sequence_origin | M |  add other possibilities such as genome and metagenome
| | | pr2_continent, pr2_country, pr2_country_lat, pr2_country_lon | A |  geographical origin extracted from gb_country field, gb_isolation_source, eukref_geo_loc_name
| | | pr2_location, pr2_location_lat, pr2_location_lon | A |  geographical origin extracted from gb_country field, gb_isolation_source, eukref_geo_loc_name
| | | pr2_sea, pr2_sea_lat, pr2_sea_lon | A |  geographical origin extracted from gb_country field, gb_isolation_source, eukref_geo_loc_name
| |pr2_sequence | sequence_hash | A |  hash value of the sequence (using R function [digest::sha1](https://cran.r-project.org/web/packages/openssl/vignettes/crypto_hashing.html)
| |pr2_taxonomy | taxon_trophic_mode | A |  detailed trophic mode (e.g. "C-fixation constitutive; Mixotroph") - for future use
4.11.1 | pr2_metadata | gb_reference | A |  Contains the whole REFERENCE field from GenBank
 |  | eukref_publication eukref_authors eukref_journal | M |  Merged into gb_publication, gb_authors, gb_journal
4.11.0 | pr2_metadata | eukref_publication eukref_authors eukref_journal eukref_notes | A | Added
4.11.0 | pr2_metadata | pr2_xxx | M | fields annotated by Eukref renamed back to eukref_xxx
4.11.0  | pr2_main | taxo_id | R | not used anymore since linked is done by species (this will be probably reinstated later on a different form using a different format for the taxonomy table).
4.9 | pr2_metadata | eukref_xxx | M | renamed to pr2_xxx to reflect the fact that these fields will also be updated independantly of EukRef
4.9 | pr2_main | reference_sequence | A | designate sequences that can be used as reference e.g. for alignment  
4.8 | pr2_main, taxo | xx_date (e.g. edited_date) | R | redundant with xx_version (e.g. edited_version) fields  
4.8 | pr2_sequence | sequence_length | M | Minimum length is now 500 bp.  

Action : A=Added/R=Removed/M=Modified
