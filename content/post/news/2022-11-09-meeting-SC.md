---
authors:
- vaulot
- delcampo
categories:
- news
date: "2022-11-09"
weight: 10
draft: false
featured: false
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  placement: 2
  preview_only: false
projects: []
subtitle: ''
summary: The database contains metabarcodes from 41 datasets corresponding to more than 4,000 samples and 90,000 ASVs.
tags:
- News
- pr2
title: 'PR2 scientific committee meeting  by Zoom - 2022-11-10.'
---


**Participants**:
ramonm@icm.csic.es" <ramonm@icm.csic.es>; "Parfrey, Laura" <lwparfrey@botany.ubc.ca>; "Luciana Santoferrara" <Luciana.Santoferrara@hofstra.edu>; "kolisko@paru.cas.cz" <kolisko@paru.cas.cz>; "Javier del Campo" <fonamental@gmail.com>; "Ian Probert" <probert@sb-roscoff.fr>; "Guillou Laure" <laure.guillou@sb-roscoff.fr>; "Geisen, Stefan" <stefan.geisen@wur.nl>;  "Fabien Burki" <fabien.burki@ebc.uu.se>; "Adriana Lopes dos Santos (Asst Prof)" <adriana.lopes@ntu.edu.sg>

Full list of PR2 team can be found here: https://pr2-database.org/team/

## Presentations
* Daniel: the current state of the PR2 ecosystem (see attached pdf)
* Javier: the future implementation of PR2_annotation, the successor of EukRef pipeline (see attached pdf)

## Open discussion

### Annotation
* Laura suggested to better acknowledge annotators.  Daniel mentioned that they already appear in the web site.  One easy way to acknowledge them better would be to put them as co-authors to the Zenodo release which has DOI number (just checked this is really easy to do...)
* We should try to have an annotation workshop in 2023 in Barcelona which may be funded by the Moore Foundation.  The new implementation of EukRef should make things more easy and efficient.
* Fabien asked how sequences were added to PR2.  Daniel answered that at present it was a bit random and really dependent on the annotators.
* Ian suggested to have confidence levels for sequences.  We have now "reference" sequences but this is not really very well managed. This could be maybe improved during a workshop by testing a confidence level system
* Ramon mentioned that there were some chimera in Stramenopiles in particular some in the last part of the sequence in V9. He will try to report them as time goes.
  
### Improvements
* **Number of taxonomic levels** - We discussed whether we should increase the number of levels to accommodate recent changes at the root of the eukaryotic tree.  Daniel think this not a good idea as more levels make annotation more complex.  However, Daniel proposed that the work which has been done with Fabien, Mahwash and Javier will be adapted for the current eight levels. In fact Ramon is using a reduced number of levels which he thinks is often more adapted for analysis. He will send an example to Daniel for possible implementation into PR2.
* **Long reads** - Everyone agreed that it would be interesting to add long reads in view of the current development of long read metabarcoding.  Javier proposed to provide a first set of several thousands full operon sequences he extracted from genomes.  The idea of adding data from metagenomes would need to be carefully examined.  Adriana mentioned the existence of chimera in MAG assembled from Tara.  In contrast Ramon indicated that he obtained full operon from sorted cells using PacBio sequencing which were of very good quality.  Initially the long reads will not be annotated but we could also extract the different genes (18S, 28S, ITS1 and 2) without modifying too much the structure of the database since the PR2 accession number is based on the GenBank accession number plus the localization of the sequence (start_end).
  
### Project structure
* Daniel proposed to reduce the "Core Team" to Daniel and Javier and to have Fred Mahé and Laure part of the Scientific Committee (SC). 
* In addition Adriana, Stefan and Ian will be part of the SC. 
* The SC should try to meet more often (at least once every 6 months) and maybe also for specific topics.

### Funding
* It is critical at least to fund at least the infrastructure (MySQL database, Google Cloud virtual machine) which would be around 3 to 4,000 euros per year.
* One idea that emerged could be to link PR2 to the Roscoff Culture Collection which will ensure long term survival of the structure as well as the possibility to more easily get funding.  in fact Silva is now moving under the umbrella of the DSMZ and we could discuss collaboration with them.

### Presentations
* [The PR2 ecosystem](/files/2022-11-09-PR2-meeting.pdf)
