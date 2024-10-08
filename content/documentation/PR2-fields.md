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
lastmod: "2023-04-06"
projects: []
subtitle: ''
summary: Detailed information on PR2 reference database fields
tags:
- Documentation
- Database
title: 'Database fields'
---

We are providing as part of the pr2database package two data frames as functions:

* pr2_database(): the main PR2 reference database containing both 18S rRNA and plastid 16S rRNA sequences
* pr2_taxonomy(): the main PR2 reference database containing both 18S rRNA and plastid 16S rRNA sequences

## pr2_database()

The PR2 reference database is provided as a data frame called through the function**pr2database::pr2_database()**.  This is a join between the following tables:

* pr2_main
* pr2_taxonomy
* pr2_sequence
* pr2_metadata
* pr2_countries
* pr2_traits
* pr2_assign_silva
* eukribo_v2

The metadata contains several types of fields:

* gb_ : originating from the GenBank entry
* eukref_ : annotated by the Eukref project
* pr2_ : annotated by pr2 such latitude and longitude
* eukribo_ : from the EukRibo database
* silva_ : from the Silva database

### Detailed description of fields
Fields | Comment  
---  | ---
pr2_accession|PR2 specific accession number
genbank_accession|Genbank accession number (without the vresion)
start|Start of sequence in Genbank entry
end|End of sequence in Genbank entry
label|Label explaining origin of sequence
 |G: genomic sequence containing a described intron (rDNA)
 |R: the previous genomic rRNA sequence, without the intron(s)
 |U: no intron described, but intron(s) may be present
 |UC: introns were detected in silico and removed from the sequence (putative rRNA)
gene|18S_rRNA or 16S_rRNA
organelle|nucleus, plastid, mitochondria, nucleomorph, apicoplast (left empty for cyanobacteria)
reference_sequence|= 1, this is a reference sequence that can be used for example for alignements
added_version|PR2 version when sequence was added
remark|Remark concerning  the sequence
domain|rank 1
supergroup|rank 2
division|rank 3
subdivision|rank 4
class|rank 5
order|rank 6
family|rank 7
genus|rank 8
species|Assigned species - rank 9
reference|Reference in the litterature concerning  the taxonomy
sequence|Sequence
sequence_length|Length of sequence
ambiguities|Number of ambiguities
sequence_hash|Hash value of sequence
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
pr2_sample_type|PR2: e.g. culture, isolate, environmental, unknown
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
mixoplanton|from the [Mixoplankton database (MDB)](https://doi.org/10.1111/jeu.12972)
 | * CM - Constitutive Mixoplankton
 | * GNCM - Generalist Non-Constitutive Mixoplankton
 | * pSNCM - plastidic Specialist Non-Constitutive Mixoplankton
 | * eSNCM - endosymbiotic Specialist Non-Constitutive Mixoplankton
metadata_remark|PR2: Any remark on metadata
eukribo_UniEuk_taxonomy_string| Taxonomy assignment from [EukRibo database]( https://doi.org/10.5281/zenodo.6327890)
eukribo_V4| Information about presence and completeness V4 region from [EukRibo database]( https://doi.org/10.5281/zenodo.6327890)
eukribo_V9| Information about presence and completeness V9 region from [EukRibo database]( https://doi.org/10.5281/zenodo.6327890)
silva_taxonomy| taxonomy from [Silva version 138]( https://www.arb-silva.de/documentation/release-138/)
