---
authors:
- vaulot
categories:
- documentation
date: "2018-08-10"
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-08-26"
projects: []
subtitle: ''
summary: Format of files provided
tags:
- Documentation
title: 'Format of PR2 flat files'
---

## List of files are provided for each release

**Important note** : All files are in UNIX format (end of lines are indicated Line Feed-LF only).  Please see at the bottom of the file how to converts the files to Windows format (end of lines are CR+LF). See at the bottom of this page how to convert.

* Two files for use with Qiime or Mothur.
  + **pr2_mothur.fasta.gz** contains all sequences in fasta format with the accession in the description line
  + **pr2_mothur.tax.gz** contains the taxonomy of each sequence separated from the accession number by a tabulation
      + Note :Qiime only use 7 taxonomical levels by default.
* **pr2_UTAX.fasta.gz** contains one fasta file with the accession number of the sequence and its full taxonomy on the description line in the UTAX format. It is suitable to use with USEARCH and VSEARCH.
* **pr2_dada2.fasta.gz** contains a [dada2](https://benjjneb.github.io/dada2/index.html) format compatible training file
* **pr2_taxo_long.fasta.gz** contains one fasta file with the accession number of the sequence, the name of the sequence and its full taxonomy on the description line. It is suitable to build a local database for BLAST search
* **pr2_metadata.csv.gz** contains a tabulation separated file with all the metadata from genbank as well as annotation made to the PR2 database.
* **pr2_merged.csv.gz** contains a tabulation separated file the full PR2 database including sequences, taxonomy and metadata.
* **R dataset**. See [detailed instructions](https://github.com/vaulot/pr2database/wiki/The-R-pr2database-package) on how to install and use

* [Link to latest release](https://github.com/vaulot/pr2_database/releases)

## Examples of format
### mothur fasta
```console
>AB353770.1.1740_U
ATGCTTGTCTCAAAGATTAAGCCATGCATGTCTCAGTATAAGCTTTTACATGGCGAAACTGCGAATGGCTCATTAAAACA
GTTACAGTTTATTTGAAGGTCATTTTCTACATGGATAACTGTGGTAATTCTAGAGCTAATACATGCGCCCAAACCCGACT
CCGTGGAAGGGTTGTATTTATTAGTTACAGAACCAACCCAGGTTCGCCTGGCCATTTGGTGATTCATAATAAACGAGCGA
ATTGCACAGCCTCAGCTGGCGATGTATCATTCAAGTTTCTGACCTATCAGCTTCCGACGGTAGGGTATTGGCCTACCGTG
GCAATGACGGGTAACGGAGAATTAGGGTTCGATTCCGGAGAGGGAGCCTGAGAAACGGCTACCACATCTAAGGAAGGCAG
CAGGCGCGCAAATTACCCAATCCTGACACAGGGAGGTAGTGACAAGAAATAACAATACAGGGCAACCATGTCTTGTA`
```

### mothur taxonomy
```console
AB353770.1.1740_U
Eukaryota;Alveolata;Dinophyta;Dinophyceae;Dinophyceae_X;Dinophyceae_XX;Peridiniopsis;Peridiniopsis_kevei;
KC672520.1.1801_U
Eukaryota;Opisthokonta;Fungi;Ascomycota;Pezizomycotina;Leotiomycetes;Leotiomycetes_X;Leotiomycetes_X_sp.;
```

### UTAX fasta
```console
>AB353770.1.1740_U;tax=k:Eukaryota,d:Alveolata,p:Dinophyta,c:Dinophyceae,o:Dinophyceae_X,f:Dinophyceae_XX,g:Peridiniopsis,s:Peridiniopsis_kevei
ATGCTTGTCTCAAAGATTAAGCCATGCATGTCTCAGTATAAGCTTTTACATGGCGAAACTGCGAATGGCTCATTAAAACA
GTTACAGTTTATTTGAAGGTCATTTTCTACATGGATAACTGTGGTAATTCTAGAGCTAATACATGCGCCCAAACCCGACT
CCGTGGAAGGGTTGTATTTATTAGTTACAGAACCAACCCAGGTTCGCCTGGCCATTTGGTGATTCATAATAAACGAGCGA
ATTGCACAGCCTCAGCTGGCGATGTATCATTCAAGTTTCTGACCTATCAGCTTCCGACGGTAGGGTATTGGCCTACCGT
```
### dada2 fasta
```console
>Eukaryota;Alveolata;Dinophyta;Dinophyceae;Dinophyceae_X;Dinophyceae_XX;Peridiniopsis;Peridiniopsis_kevei;
ATGCTTGTCTCAAAGATTAAGCCATGCATGTCTCAGTATAAGCTTTTACATGGCGAAACTGCGAATGGCTCATTAAAACA
GTTACAGTTTATTTGAAGGTCATTTTCTACATGGATAACTGTGGTAATTCTAGAGCTAATACATGCGCCCAAACCCGACT
```
### fasta long
```console
>AB353770.1.1740_U||Eukaryota|Alveolata|Dinophyta|Dinophyceae|Dinophyceae_X|Dinophyceae_XX|Peridiniopsis|Peridiniopsis_kevei
ATGCTTGTCTCAAAGATTAAGCCATGCATGTCTCAGTATAAGCTTTTACATGGCGAAACTGCGAATGGCTCATTAAAACA
GTTACAGTTTATTTGAAGGTCATTTTCTACATGGATAACTGTGGTAATTCTAGAGCTAATACATGCGCCCAAACCCGACT
CCGTGGAAGGGTTGTATTTATTAGTTACAGAACCAACCCAGGTTCGCCTGGCCATTTGGTGATTCATAATAAACGAGCGA
```

### metadata
```console
pr2_accession	genbank_accession	gb_date	gb_locus	gb_definition	gb_organism	gb_strain	gb_culture_collection	gb_clone	gb_isolate	gb_isolation_source	gb_specimen_voucher	gb_host	gb_collection_date	gb_environmental_sample	gb_country	gb_lat_lon	gb_collected_by	gb_note	gb_publication	gb_authors	gb_journal	pr2_main_id	pr2_metadata_id	pr2_sample_type	pr2_ocean	pr2_latitude	pr2_longitude	pr2_sequence_origin	pr2_size_fraction	pr2_size_fraction_min	pr2_size_fraction_max	eukref_name	eukref_env_material	eukref_env_biome	eukref_biotic_relationship	eukref_specific_host	eukref_geo_loc_name	pubmed_id	metadata_remark
AB353770.1.1740_U	AB353770		PLN	Peridiniopsis cf. kevei gene for 18S rRNA, partial sequence.									26-juil.-03		Japan: Toyama, Tomi-iwa Canal Park							6	3830												
KC672520.1.1801_U	KC672520		ENV	Uncultured fungus clone nco62b12c1 18S ribosomal RNA gene, partial				nco62b12c1		skin, plantar heel		Homo sapiens						Subject Code: 1006; symmetry: right; sampling technique: swab"				7	136373	environmental														23698366
```

### merged
```console
pr2_main_id	pr2_accession	genbank_accession	start	end	label	taxo_id.x	species	chimera	chimera_remark	added_date	added_version	removed_date	removed_version	edited_date	edited_version	edited_by	edited_remark	remark	taxo_id.y	kingdom	supergroup	division	class	order	family	genus	taxo_edited_date	taxo_edited_version	taxo_removed_date	taxo_removed_version	taxo_remark	reference	seq_id	sequence	sequence_length	ambiguities	pr2_metadata_id	gb_date	gb_locus	gb_definition	gb_organism	gb_strain	gb_culture_collection	gb_clone	gb_isolate	gb_isolation_source	gb_specimen_voucher	gb_host	gb_collection_date	gb_environmental_sample	gb_country	gb_lat_lon	gb_collected_by	gb_note	pubmed_id	gb_publication	gb_authors	gb_journal	eukref_name	eukref_env_material	eukref_env_biome	eukref_biotic_relationship	eukref_specific_host	eukref_geo_loc_name	pr2_sample_type	p2_sample_method	pr2_ocean	pr2_latitude	pr2_longitude	pr2_sequence_origin	pr2_size_fraction	pr2_size_fraction_min	pr2_size_fraction_max	metadata_remark	metadata_select	sequence_label
AB353770.1.1740_U	AB353770	1	1740	U	2014	Peridiniopsis_kevei												2014	Eukaryota	Alveolata	Dinophyta	Dinophyceae	Dinophyceae_X	Dinophyceae_XX	Peridiniopsis								ATGCTTGTCTCAAAGATTAAGCCATGCATGTCTCAGTATAAGCTTTTACATGGCGAAACTGCGAATGGCTCATTAAAACAGTTACAGTTTATTTGAAGGTCATTTTCTACATGGATAACTGTGGTAATTCTAGAGCTAATACATGCGCCCAAACCCGACTCCGTGGAAGGGTTGTATTTATTAGTTACAGAACCAACCCAGGTTCGCCTGGCCATTTGGTGATTCATAATAAACGAGCGAATTGCACAGCCTCAGCTGGCGATGTATCATTCAAGTTTCTGACCTATCAGCTTCCGACGGTAGGGTATTGGCCTACCGTGGCAATGACGGGTAACGGAGAATTAGGGTTCGATTCCGGAGAGGGAGCCTGAGAAACGGCTACCACATCTAAGGAAGGCAGCAGGCGCGCAAATTACCCAATCCTGACACAGGGAGGTAGTGACAAGAAATAACAATACAGGGCAACCATGTCTTGTAATTGGAATGAGTAGAATTTAAATCCCTTTACGAGTATCCATTGGAGGGCAAGTCTGGTGCCAGCAGCCGCGGTAATTCCAGCTCCAATAGCGTATATTAAAGTTGTTGCGGTTAAAAAGCTCGTAGTTGGATTTCTGTCGAAGGAGACCGGTCCGCCCTCTGGGTGAGTATCTGGATCTCTTTGGACATCTTCTTGGGGAACGTATCTGCACTTCATTGTGCGGTGCGGTACTCAAGACTTTTACTTTGAGGAAATTAGAGTGTTTCAAGCAGGCACACGCCTTGAATACATTAGCATGGAATAATAAGATAGGACCTCGGTTCTATTTTGTTGGTTTCTAGAGCTGAGGTAATGATTAATAGGGATAGTTGGGGGCATTCGTATTTAACTGTCAGAGGTGAAATTCTTGGATTTGTTAAAGACGGACTACTGCGAAAGCATTTGCCAAGGATGTTTTCATTGATCAAGAACGAAAGTTAGGGGATCGAAGACGATCAGATACCGTCGTAGTCTTAACCATAAACCATGCCGACTAGAGATTGGAGGTCGTTATCCGTACGACTCCTTCAGCACCTTATGAGAAATCAAAGTCTTTGGGTTCCGGGGGGAGTATGGTCGCAAGGCTGAAACTTAAAGGAATTGACGGAAGGGCACCACCAGGAGTGGAGCCTGCGGCTTAATTTGACTCAACACGGGGAAACTTACCAGGTCCAGACATAGTAAGGATTGACAGATTGATAGCTCTTTCTTGATTCTATGGGTGGTGGTGCATGGCCGTTCTTAGTTGGTGGAGTGATTTGTCTGGTTAATTCCGTTAACGAACGAGACCTTAACCTGCTAAATAGTGACACATTACCCCGGTAATGTGGGTTACTTCTTAGAGGGACTTTGCGTGTCTAACGCAAGGAAGTTTGAGGCAATAACAGGTCTGTGATGCCCTTAGATGTTCTGGGCTGCACGCGCGCTACACTGATGCGCTCAACGAGTTTATGACCTTGCCCGGAAGGGTTGGGTAATCTTGTTAAAACGCATCGTGATGGGGATAGATTATTGCAATTATTAATCTTCAACGAGGAATTCCTAGTAAGCGCGAGTCATCAGCTCGTGCTGATTAAGTCCCTGCCCTTTGTACACACCGCCCGTCGCTCCTACCGATTGAGTGATCCGGTGAATAATTCGGACCGCAGCATTTGTCAGTTCCTGACTCATGCCGTGGAAAGTCTAGTGAACCTTATCACTTAGAGGAAGGAGAAGTCGTAACA	1740	0	3830		PLN	Peridiniopsis cf. kevei gene for 18S rRNA, partial sequence.									26-juil.-03		Japan: Toyama, Tomi-iwa Canal Park
```

## Converting files from UNIX to Windows format
All files are in UNIX format (end of lines are indicated Line Feed-LF only).  Please see at the bottom of the file how to converts the files to Windows format (end of lines are CR+LF).

1. Install [Notepad++](https://notepad-plus-plus.org/)  

2. Open the files to convert (e.g. for mothur the .fasta and .tax files)  

![](./../notepad_unix.png)

3. Convert the end of lines  

![](./../notepad_convert_lines.png)  

4. Now the file should like the image below (red arrow)
5. Save the file under the same name by clicking on the disk icon (blue arrow)

![](./../notepad_windows_line.png)
