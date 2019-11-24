---
authors:
- vaulot
categories:
- documentation
date: "2018-09-10"
weight: 10
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-11-15"
projects: []
subtitle: ''
summary: Detailed information on PR2 fields
tags:
- Documentation
- Database
title: 'Database fields'
---

## General structure
The PR2 database is provided as a data frame.  This is a join between the following tables:

* pr2_main
* pr2_taxonomy
* pr2_sequence
* pr2_metadata

The metadata contains three types of fields:

* gb_ : originating from the GenBank entry
* eukref_ : annotated by the Eukref project
* pr2_ : annotated by pr2 such latitude and longitude

## Detailed description of fields
Fields | Comment  
---  | ---
pr2_main_id|ID of PR2 entry in table pr2_main
pr2_accession|PR2 specific accession number
genbank_accession|Genbank accession number (without the vresion)
start|Start of sequence in Genbank entry
end|End of sequence in Genbank entry
label|Label explaining origin of sequence
|
|G: genomic sequence containing a described intron (rDNA)
|R: the previous genomic rRNA sequence, without the intron(s)
|U: no intron described, but intron(s) may be present
|UC: introns were detected in silico and removed from the sequence (putative rRNA)
gene|18S_rRNA or 16S_rRNA
organelle|nucleus, plastid, mitochondria, nucleomorph, apicoplast (left empty for cyanobacteria)
species|Assigned species - rank 8
chimera|= 1, the sequence is chimeric
chimera_remark|Comment on reason why the sequence was mentionned as chimeric
reference_sequence|= 1, this is a reference sequence that can be used for example for alignements
added_version|PR2 version when sequence was added
removed_version|PR2 version when sequence was removed
edited_version|PR2 version when sequence assignation was edited
edited_by|Who edited the assignation
edited_remark|Remark concerning the assignation
remark|Remark concerning  the sequence
taxo_id|ID of the species in table pr2_taxonomy
kingdom|rank 1
supergroup|rank 2
division|rank 3
class|rank 4
order|rank 5
family|rank 6
genus|rank 7
taxon_trophic_mode|e.g. symbiotic
taxo_edited_version|PR2 version when taxonomy path was edited
taxo_edited_by|Who edited the taxonomy path
taxo_removed_version|PR2 version when species and taxonomy path was removed
taxo_remark|Remark concerning  the taxonomy
reference|Reference in the litterature concerning  the taxonomy
seq_id|ID of the sequence in table pr2_sequence
sequence|Sequence
sequence_length|Length of sequence
ambiguities|Number of ambiguities
sequence_hash|Hash value of sequence
pr2_metadata_id|ID of metadata in table pr2_metadata
gb_date|Genbank: Date
gb_locus|Genbank: Locus
gb_definition|Genbank: Definition
gb_organism|Genbank: Organism
gb_taxonomy|Genbank: Taxonomy
gb_strain|Genbank: Strain
gb_culture_collection|Genbank: Culture Collection
gb_clone|Genbank: Clone
gb_isolate|Genbank: Isolate
gb_isolation_source|Genbank: Isolation Source
gb_specimen_voucher|Genbank: Voucher
gb_host|Genbank: Host
gb_collection_date|Genbank: Date of Collection
gb_environmental_sample|Genbank: Environmental Sample
gb_country|Genbank: Country
gb_lat_lon|Genbank: lat Lon
gb_collected_by|Genbank: Collected by
gb_note|Genbank: Note
gb_references|Genbank: Full references not parsed
gb_publication|Genbank: Publication
gb_authors|Genbank: Authors
gb_journal|Genbank: Journal
pubmed_id|Genbank: Pubmed ID
eukref_name|Eukref: Name use in EukRef, usually either the species name or the clone name
eukref_source|Eukref: Source of the sequence : Isolate or Environmental
eukref_env_material|Eukref: uses ENVO keywords
eukref_env_biome|Eukref: uses ENVO keywords
eukref_biotic_relationship|Eukref: eg parasite
eukref_specific_host|Eukref: Specific Host annotated
eukref_geo_loc_name|Eukref: Location name annotated
eukref_notes|Eukref: Notes made during Eukref annotation
pr2_sample_type|PR2: e.g. water, ice
pr2_sample_method|PR2: e.g. filtration, flow cytometry sorting
pr2_latitude|PR2: Parsed from GenBank entry
pr2_longitude|PR2: Parsed from GenBank entry
pr2_ocean|PR2: e.g. Arctic Ocean
pr2_sea|PR2: e.g. North Sea
pr2_sea_lat|PR2: latitude of sea or ocean
pr2_sea_lon|PR2: longitude of sea or ocean
pr2_continent|PR2: e.g. Asia
pr2_country|PR2: e.g. France
pr2_country_geocode|PR2: 2 letter code from genonames - e.g. FR
pr2_country_lat|PR2: latitude of country
pr2_country_lon|PR2: longitude of country
pr2_location|PR2: from gb_country field - e.g. Paris, France
pr2_location_geoname|PR2: e.g. Paris
pr2_location_geotype|PR2: e.g. bay
pr2_location_lat|PR2: latitude of location
pr2_location_lon|PR2: longtitude of location
pr2_sequence_origin|PR2: clone library, metabarcode, PCR
pr2_size_fraction|PR2: Name of size fraction, e.g. pico, nano
pr2_size_fraction_min|PR2: Minimum size filtered, e.g. 0.2 µm
pr2_size_fraction_max|PR2: Maximum size filtered, e.g. 20 µm
metadata_remark|PR2: Any remark on metadata
