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
title: 'Pipeline overview'
---
### **A. IN-HOUSE INSTALLATION**

>**Software needed. **Tools necessary to install to run the pipeline are listed below. You should install each of these programs on your computer.

>*   [usearch](http://www.drive5.com/usearch/) (version 7.01 or 8.*; free 32-bit version is fine)
>*   [vsearch](https://github.com/torognes/vsearch)
>*   [MAFFT](https://mafft.cbrc.jp/alignment/software/); If preferred other software like [SINA](https://www.arb-silva.de/aligner/sina-download/)* or [INFERNAL](http://eddylab.org/infernal/) can be also used
>*   [trimAL](http://trimal.cgenomics.org/) (version 1.2)
>*   [RAxML](http://sco.h-its.org/exelixis/web/software/raxml/index.html) (version 8 or newer). You can find some tips on the use of RAxML at the bottom of the page.
>*   [FastTree](http://meta.microbesonline.org/fasttree/)
>*   [BLAST+ (version 2.2.22)](http://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=Download)
>*   [Python](https://www.python.org/) (should already be installed)
>*   [Biopython](http://biopython.org/)
>*   [AliView](http://www.ormbunkar.se/aliview/)
>*   [FigTree](http://tree.bio.ed.ac.uk/software/figtree/)
>*   [EukRef pipeline](github: https://github.com/eukref/pipeline)

>###### *Please remember, if you choose to use SINA alignment, that you have to provide a reference alignment in ARB format. Easiest way to get one is to downloaded from [https://www.arb-silva.de/download/arb-files/](https://www.arb-silva.de/download/arb-files/)

>Use [TextWrangler](http://www.barebones.com/products/textwrangler/) or equivalent text editor for taking notes about the curation process, modifying scripts, and viewing files. **Do NOT use Word or equivalent**.

**OR**

###  B. DOWNLOAD AND INSTALL VIRTUAL MACHINE FILE

This is an alternative for users who have trouble installing all the software components or users who just want to get a "ready-to-use" package.

Virtual machine installation:

**Step 1.** install [Vagrant](https://www.vagrantup.com/) software for your operating system (in Ubuntu and other Linux distributions you can use the distributions package installer, i.e.: sudo apt-get install vagrant).

**Step 2.** Install the necessary plugin:

```
vagrant plugin install vagrant-disksize
```

**Step 3.** Deploy and start the virtual machine

```
cat > Vagrantfile <<EOF
Vagrant.configure("2") do |config|
  config.vm.box = "serafimn/eukref"
  config.disksize.size = "80GB"
end
EOF

vagrant up
```

**Step 4.** log into the virtual machine

```
vagrant ssh
```

**Step 5.** Download nucleotide NCBI database using provided script

```
cd eukref
./download_NCBI_nt_db.sh
```

**Step 6.** Start using the eukref pipeline



### C. EUKREF PIPELINE


This document outlines the procedure for gathering sequences and generating an alignment and tree.

**Step 0.** Decide upon the scope of the group you will initially curate. Your group should be of a manageable size in terms of taxonomic breadth and total available sequences (e.g. a subset of Rhizaria or diatoms rather than the entire clade). It will be more useful for you and EukRef in general to finish curation of a smaller group. You can expand later.
---
**Step 1.** Generate a curated starting sequence set, alignment, and tree for your group. This initial sequence set will form the basis of your entire curation effort. Therefore it is critical that these sequences are well-curated, and you need an alignment of these sequences and a reliable phylogenetic tree built from them. There are multiple ways to get this initial sequence set, but in each case, you should ensure it meets the criteria below. Additionally, you need a file that contains diverse outgroups: 5-10 sequences from all of the neighboring clades (e.g., if you are working on ciliates you should include apicomplexa, dinoflagellates, and stramenopiles). This alignment MUST be untrimmed (e.g. contain all gaps) so that additional sequences can be added. The initial tree must be checked to make sure it covers the diversity of the group and reflects phylogenetic relationships expected based on current research/literature.  Any errant sequences need to be removed from the alignment.

Criteria for the initial set of sequences, alignment, and tree:

*   The initial set of sequences should be small, ~200 sequences or fewer, so that you can easily check the resulting alignment and tree.
*   Sequences should cover the breadth of the clade, including divergent groups.
*   The alignment and tree should have outgroups included to detect sequences that branch outside of your clade.
*   The alignment should be untrimmed
*   The tree produced from this alignment should display expected relationships and problematic sequences should be removed.

Three possible ways to get your initial alignment:

*   You may already have a curated starting alignment and tree from previous work. In this case, you are ready to go after checking your tree and alignment. **Proceed to Step 5**.
*   Download sequences from GenBank based on taxonomy. This will target the sequences from cultured isolates or those that were identified in other ways (e.g. morphologically identified and picked). **Proceed to Step 2**.
*   Alternatively, you may wish to start with the SILVA or PR2 set of sequences for your group. You must ensure that these sequences meet the criteria above. **Proceed to Step 2**.

---
**Step 2. Retrieve an initial set of sequences and cluster**

NOTE 1: Users can choose a different similarity threshold if desired. For example, you may wish to work at 99% identity for small clades. In this case, replace 0.97 with 0.99 throughout.

NOTE 2: In all commands, you must substitute your clade name for "NAME".

**2a)** Retrieve initial sequences using GenBank, PR2 or SILVA

Recommended: SILVA or [PR2 database](https://github.com/vaulot/pr2_database). Use the grep command to pull out your sequences of interest. Note that clade names often differ in these different databases.

```
grep –A 1 -i “NAME” silva_reference_database.fasta > NAME.fasta
```

```
grep –A 1 -i “NAME” PR2_reference_database.fasta > NAME.fasta

```

[GenBank](http://www.ncbi.nlm.nih.gov/genbank/) - [use advanced search at NCBI](http://www.ncbi.nlm.nih.gov/nuccore/advanced), or add the text below to the [NCBI query box.](http://www.ncbi.nlm.nih.gov/nuccore) Replace XXXX with the Taxonomy ID. Find the Taxonomy ID by searching [NCBI taxonomy](http://www.ncbi.nlm.nih.gov/Taxonomy/taxonomyhome.html/):

_txidXXXX[Organism:exp] (18S OR SSU) NOT (mitochondrial OR mitochondria OR complete genome)_

This will target targeted cultured isolates or isolates that were morphologically identified

After you have downloaded your sequences, clean fasta headers to contain the GenBank accession number only.

```
sed 's/gi\|[0-9]*\|gb\|//' NAMEgb.fasta | sed 's/\..*//' > NAME.fasta
```

**2b)** Cluster your sequences to produce a manageable number of sequences using usearch (two commands). Similarity threshold is set at 97% here but can be adjusted by changing the "-id" command.  These commands choose the longest sequence as the representative sequence for each cluster. We will use also this step to remove sequences shorter than 500 bp. You will use these representative sequences for your initial alignment/tree.

```
usearch -sortbylength NAME.fasta -fastaout NAME.sorted.fasta -minseqlength 500 -notrunclabels
```

```
usearch -cluster_smallmem NAME.sorted.fasta -id 0.97 -centroids NAME.clustered.fasta -uc NAME.clusters -notrunclabels
```

---

**Step 3. Build initial alignment.**

**3a)** Assemble a set of close outgroup sequences. Outgroup sequences must be full-length. You should include outgroups from all of the clades that are neighbors to your group of interest, 5-10 sequences per group. These should be chosen based on your knowledge (ask for help if needed). You can get outgroup sequences from GenBank, SILVA or PR2\. See step 2 for details. Add your outgroup sequences to clustered starting sequences (NAME.clustered.fasta file)

**3b)** Align using MAFFT. Use the default MAFFT algorithm (command below) unless there is a specific reason to use a different algorithm or approach. (Experience users can use different preferred alignment program)

```
mafft --reorder --auto NAME.clustered.fasta > NAME_aligned.fasta
```

or use INFERNAL

```
cmalign --outformat AFA -o NAME_aligned_infernal.fasta SSUref.cmm NAME.clustered.fasta
```

```
sed 's/\./-/g' NAME_aligned_infernal.fasta > NAME_aligned.fasta
```

or use SINA*

```
./sina -i NAME.clustered.fasta -o NAME_aligned.fasta --outtype fasta --ptdb REFERENCE_ALN.ARB
```

*Please remember, if you choose to use SINA alignment, that you have to provide a reference alignment in ARB format. Easiest way to get one is to downloaded from [https://www.arb-silva.de/download/arb-files/](https://www.arb-silva.de/download/arb-files/)

**3c)** Trim the alignment using trimal.

```
trimal -in NAME_aligned.fasta -out NAME.trimal.fasta -gt 0.3 -st 0.001
```

---

**Step 4. Build an initial tree.**

**4a)** Build a phylogenetic tree using RAxML.

```
raxmlHPC-PTHREADS-SSE3 -T 4 -m GTRCAT -c 25 -e 0.001 -p 31415 -f a -N 100 -x 02938 -n NAME -s NAME.trimal.fasta -w /full/path/to/output_directory
```

Constraint trees: You can use a constraint tree in RAxML (-g option), which will allow you to “dictate” how some part of the tree should look like based on previously published relationships for your clade, for example, based on morphology and/or multigene phylogeny. Constraint trees should be used with caution and should ONLY constrain robust relationships (those observed in multiple studies) since it is desirable to avoid fitting the tree into your personal favorite topology. All taxa in the constraint tree must be in the alignment and names in the alignment an in the constraint tree must match exactly. Moreover, constraint tree cannot contain taxa not present in the alignment. Constrained trees can be edited in [Mesquite](https://www.mesquiteproject.org/).

Alternatively, you can use FastTree, which is very easy to install and gives you "quick and dirty" tree, in case you don't want to or can't wait for RAxML tree or in cases when the number of taxa is too high (more than several thousand).

```
fasttreeMP -gtr -nt NAME.trimal.fasta > NAME.tre
```

**4b)** Visualize tree using FigTree. Identify errant sequences to be removed. **Go back to step 3** to refine alignment, remove errant sequences and repeat as necessary until you have a high quality starting initial alignment and tree. If your tree does not reflect known relationships you may wish to use a constraint tree in step 4a.  **Proceed to step 5** once you are happy with your tree/alignment. You will need the unaligned set of sequences (without outgroups) as input for step 5 (initial_DS.fas).

---

**Step 5. Download databases**

**5a)** Download and unpack [databases.tar.gz](https://github.com/eukref/eukref/blob/master/databases.tar.gz):

```
tar -xvf databases.tar.gz

```

Inside the unpacked "databases" directory you will find three files: Reference_DB.fas and gb203_pr2_all_10_28_97p_noorg.fasta, and tax_d.bin.  These files are used for filtering results within eukref_gbretrieve.py. All three files must be in the current working directory where you run the eukref_gbrtrieve.py script in Step 6.

**5b)** Locate a copy of GenBank nt database in use at your institution or on your server.  [at the EukRef workshop there is a copy on the Amazon server]. GenBank NT should ideally be downloaded to a server. There will be more than 40 files totaling more than 30 GB. Downloading can take several hours. You may wish to install and use a tool like wget.  In a workshop setting download one time and allow access for all participants.

Make a new folder called DATABASE_FOLDER. From [ftp://ftp.ncbi.nlm.nih.gov/blast/db/](ftp://ftp.ncbi.nlm.nih.gov/blast/db/) download taxdb.tar.gz and all nt_.tar.gz files. Also, download all nt_.tar.gz.md5 files.

Unpack with the following command:

```
for i in nt*; do tar -xvf $i ; done
```

Run md5 checksum to ensure all files are fully downloaded.

**5c)** Before running the pipeline run the following commands:

```
export BLASTDB=/path/to/DATABASE_FOLDER
```

(you can also add BLASTDB to your PATH permanently)

---

**Step 6. Retrieve all sequences that belong to your clade.**

**6a)**Run the [eukref_gbretrieve.py](https://github.com/eukref/eukref/blob/master/eukref_gbretrieve.py) script. This script will run in a loop until no new sequences are retrieved. This may take several hours for large groups.

<span style="text-decoration: underline;">Inputs:</span>

**-i** Unaligned fasta file of your clustered starting set of sequences (the output of **Step 2**, NAME.clustered.fasta). Should be refined version, with any errant sequences detected in tree inspection during **Step 4** removed. Should NOT include outgroups. Fasta headers must either be in standard GenBank format (>gi|ginumber|gb|accession| ), or have the accession number followed by a space (>accession )
**-dbnt** (/path/to/DATABASE_FOLDER/nt)GenBank NT file from **Step 5c** .
**-dbsi** (Reference_DB.udb)PR2 SSU reference database plus representative bacteria, used for filtering results. Must be in current working directory.
**-n** Number of sequences retrieved from GenBank per blasted sequence. recommended: 100
**-p** Number of CPUs.
**-g** Name of the most inclusive group you are working with from PR2 taxonomy. Find in the PR2 taxonomy file (ReferenceDB.fas) by grep.
**-m** Blast method. recommended: megablast
**-idsi** PR2 Blast cut-off (nothing less than 70% similar will be retrieved).
**-idnt** GenBank Blast cut-off (average similarity to everything on the original database).

Example command, update with your information.

```
python eukref_gbretrieve.py -i current_DB.fasta -dbnt /scratch/NCBI_NT/nt -dbsi ../../Reference_DB.fas -n 100 -p 8 -g NAME -m megablast -idsi 75 -idnt 90 -td tax_d.bin
```

<span style="text-decoration: underline;">Outputs:</span>

*   Reference set of sequences (current_DB.fas).
*   Reference sequences with only accessions in header for downstream use (current_DB_final.fas).
*   List of accession numbers (accessions_current_DB.txt).
*   A fasta file of short reads (<500 bp), and of chimeras will also be generated.

**6b)** Format sequences and metadata.Run the [eukref_gbmetadata.py](https://github.com/eukref/eukref/blob/master/eukref_gbmetadata.py) script to pull taxonomy and environmental information from GenBank records to 1) generate your initial reference database, and 2) reformat the fasta headers for easier annotation in a tree.

First, download the GenBank format for all sequences retrieved in step 6a from [NCBI batch entrez](https://www.ncbi.nlm.nih.gov/sites/batchentrez?). Upload accessions ( accessions_current_DB.txt).  Click the retrieve records link.  Click "send to" then download as GenBank(full) file (.gb extension).  This will download the gb file for all of your accessions. Save as gb_metadata.gb

<span style="text-decoration: underline;">Inputs:</span>

**-gb** Genbank flat file
**-i** fasta file output from step 6a (current_DB_final.fasta)
**--outgroup** outgroup fasta file
**-t** reference taxonomy file (pr2_4.11_full.txt)

```
python eukref_gbmetadata.py -gb gb_metadata.gb -i current_DB_final.fasta -o annotated_DB_for_tree.fasta -m metadata.txt -t /path/to/pr2_4.11_full.txt --outgroup outgroup_filtered.fasta
```

<span style="text-decoration: underline;">Outputs:</span>

*   metadata.txt: metadata file (tab delimited format) that includes taxonomy from GenBank, reference taxonomy, environmental data available in the GenBank record, and the publication associated with an accession.
*   annotated_DB_for_tree.fasta: fasta file with headers labeled for easier curation. We will use the PR2 taxonomic strings or alternatively the GenBank taxonomic string if the sequence is not in PR2\. The outgroup_filtered.fasta will be added as well to this fasta file.

---

**Step 7. Build an alignment with the reference sequences**

**7a)** Cluster sequences using usearch

```
usearch -sortbylength annotated_DB_for_tree.fasta -fastaout current_DB.sorted.fasta -minseqlength 64 -notrunclabels
```

[su_note]If the FASTA file to be clustered contains long (e.g. genomic) sequences, it is likely that the clustering step will run out of memory. Check the screen output of this “usearch -sortbylength” step, which indicates the length of the longest sequence found within the file; this should not exceed 5,000 (the hard limit imposed in Step 5).[/su_note]

NOTE: you should choose the -id (similarity threshold for clustering) that is appropriate for your group.

```
usearch -cluster_smallmem current_DB.sorted.fasta -id 0.97 -centroids current_DB.clustered.fasta -uc current_DB.clusters.uc -notrunclabels
```

**7b)** Align using MAFFT. If there is not a specific reason to use a different approach to use the default mafft algorithm.  See instructions below for alignments with groups known to be difficult.

```
mafft --reorder --auto current_DB.clustered.fasta > current_DB_aligned.fasta
```

or  use INFERNAL:

```
cmalign --outformat AFA -o current_DB_aligned_infernal.fasta SSUref.cmm current_DB.clustered.fasta
```

```
sed 's/\./-/g' current_DB_aligned_infernal.fasta > current_DB_aligned.fasta
```

or use SINA*:

```
./sina -i NAME.clustered.fasta -o NAME_aligned.fasta --outtype fasta --ptdb REFERENCE_ALN.ARB
```

*Please remember, if you choose to use SINA alignment, that you have to provide a reference alignment in ARB format. Easiest way to get one is to downloaded from [https://www.arb-silva.de/download/arb-files/](https://www.arb-silva.de/download/arb-files/)

It is critical to open and check your alignment in Aliview software (or similar) to see if there are misaligned blocks or sequences. Make sure you look at the entire length of the alignment. If the alignment is not good you will not produce a good tree.  If you have a poor alignment you can 1) align according to a template (seed) alignment, the command below, or 2) modify your alignment by hand.

If you already have a curated alignment for your group you can use it as a template (seed) to align your new sequences with the following command.

```
mafft --reorder --genafpair --maxiterate 1000 --retree --anysymbol --seed template_curated_alignment.fasta current_DB.OUTGROUP.clustered.fasta > current_DB_aligned.fasta
```

Remember to open your alignment file and check before proceeding.

**7c)** Trim the alignment using trimal

```
trimal -in current_DB_aligned.fasta -out current_DB_trim.fasta -gt 0.3 -st 0.001
```

---

**Step 8. Build RaxML trees and clean up.**

**8a)** Build a phylogenetic tree using RAxML. NOTE: do not use more threads (-T option) than available processors. Typically no more than 4 on a laptop and potentially many more on a cluster. NOTE: you can add a backbone constraint tree with the option -g.  This should be done if clades within your group are always monophyletic in the literature (e.g. in phylogenomic or multigene analyses), but are not monophyletic in 18S trees. The sequences (tips) in this constraint tree must be in your alignment (they should be a subset of your sequences), and the names must match exactly.

```
raxmlHPC-PTHREADS-SSE3 -T 4 -m GTRCAT -c 25 -p 31415 -x 20398 -d -f a -N 100 -n NAME -s current_DB.trim.fasta –w /full/path/to/output_directory
```

Alternatively, you can use FastTree (is a faster algorithm in case you don’t want or can’t wait for the RAxML results, it will give you a "quick and dirty" tree).

```
fasttreeMP -gtr -nt current_DB.trim.fasta > NAME_fasttree.tre
```

---

**Step 9. Visualize your tree, identify errant sequences that should be removed.**

Download your tree e.g. "RAxML_bestTree.clade". Open tree in FigTree and annotate taxa with either "remove" for taxa you wish to remove, or you can modify/add to the existing name. You can only annotate taxa, NOT nodes or clades.  You can select entire clades to annotate all taxa at once. Annotated nodes cannot be collapsed (annotations within the collapsed node will not be reported).
"Save as" the tree with annotations for example "RAxML_bestTree.clade_annotated.tre", which is a nexus file.

<span style="text-decoration: underline;">Inputs:</span>

**-t** RAxML_bestTree.clade_annotated.tre
**-m** metadata.txt

```
python eukref_treeparse.py -t RAxML_bestTree.clade_annotated.tre -m metadata.txt
```

<span style="text-decoration: underline;">Output:</span>

*   metadata_out.txt

The “metadata_out.txt” will be your tab-delimited metadata file with "remove" in the last column for the sequences you want to remove.  You can sort your metadata_out.txt file in excel to get all of the accessions of sequences that should be removed from your tree. Save these accessions to be removed in a file called accessions_remove.txt.

<span style="text-decoration: underline;">Inputs:</span>

**-i** current_DB.clustered.fasta
**-s** accessions_remove.txt

```
python eukref_filter_fasta.py -i current_DB.clustered.fasta -s accessions_remove.txt -o current_DB.cleaned.fasta
```

<span style="text-decoration: underline;">Output:</span>

*   current_DB.cleaned.fasta

Go back to**Step 7** to align and build a new tree, repeat until you are happy with your current set of sequences.

---

**Step 10. Build Reference Tree.**

Once you are happy with the set of sequences in your tree and your alignment you are ready to build your final reference tree. Your final, trimmed alignment is in input into RAxML. NOTE: you can add a backbone constraint tree with the option -g.  The sequences (tips) in this constraint tree must be in your alignment (they should be a subset of your sequences), and the names must match exactly.

```
raxmlHPC-PTHREADS-SSE3 -T 4 -m GTRCAT -c 25 -p 31415 -x 20398 -d -f a -N 100 -n NAME -s final_DB.trim.fasta –w /full/path/to/output_directory
```

---

**Step 11. Moving from tree to annotations.  Expanding annotations to all sequences.**

**11a)** Use the script [eukref_metatrim.py](https://github.com/eukref/eukref/blob/master/eukref_metatrim.py) Trim your metadata file to include only representative sequences of clusters -- these are the sequences in your tree.

<span style="text-decoration: underline;">Inputs:</span>

**-i** current_DB.cleaned.fasta is the fasta file with your clustered sequences containing only the sequences used in your reference tree. 

**-m** metadata.txt is your metadata file from eukref_gbmetadata.py.

```
python eukref_metatrim.py -i current_DB.cleaned.fasta -m metadata.txt -o metadata_ref.txt

```

<span style="text-decoration: underline;">Outputs:</span>

**-o** metadata_ref.txt, which only has the accessions in your reference tree. This will make annotating easier.

**11b)** You need to annotate classification your metadata_ref.txt. Note that you should have GenBank taxonomy and SILVA taxonomy in your metadata_ref.txt file so you know the starting point. In many cases, it will be easiest to annotate clades directly on your reference tree. You can annotate the tree and then export annotations to your metadata_ref.txt file using the instructions below.

Download your reference tree e.g. "RAxML_bestTree.clade". Open tree in FigTree and annotate taxa with the name of the taxon. You can only annotate the taxa, NOT nodes or clades.  You can select entire clades to annotate all taxa at once. Annotated nodes cannot be collapsed (annotations within the collapsed node will not be reported).
"Save as" the tree with annotations for example "RAxML_bestTree.clade_annotated.tre", which is a nexus file.

Run script eukref_treeparse.py to add annotations in your tree to your metadata_ref.txt file. 

<span style="text-decoration: underline;">Inputs:</span>

**-t** RAxML_bestTree.clade_annotated.tre
**-m** metadata_ref.txt

```
python eukref_treeparse.py -t RAxML_bestTree.clade_annotated.tre -m metadata_ref.txt
```

<span style="text-decoration: underline;">Outputs:</span>

*   The “metadata_ref_out.txt” will be your tab-delimited metadata file that includes the Accession Number of representative for your clusters and the annotations that you made on the tree in the last column.

**11c)** Use the script [eukref_metaexpand.py](https://github.com/eukref/eukref/blob/master/eukref_metaexpanse.py) to expand your curation to all sequences within the clusters.

<span style="text-decoration: underline;">Inputs:</span>

**-i** metadata.txt is the initial metadata file you got
**-r** metadata_ref_out.txt is the reference metadata you just added annotations to
**-c** current_DB.clusters.uc is the cluster file (.uc) from usearch. Use the most recent version if you clustered multiple times.

```
python eukref_metaexpand.py -i metadata.txt -r metadata_ref_out.txt -c current_DB.clusters.uc -o metadata_ref_expanded.txt
```

<span style="text-decoration: underline;">Outputs:</span>

**-o** metadata_ref_expanded.txt is the expanded annotated metadata file

---

**Step 12. Create a reference database.**

Now the taxonomy and metadata curation fun begin! See **[Building your database](http://eukref.org/building-your-reference-database/)** page for details.

**If you have any question or suggestion please feel free to add it to the comment section below, visit our [forum](https://groups.google.com/forum/#!forum/eukref) or send us an [e-mail](mailto:info@eukref.org)**

>**RAxML tips**
>*   MPI vs. PTHREADS: If you're running RAxML on your laptop, use PTHREADS. If you're running RAxML on a server/cluster with a lot of cores (>4), please consider using MPI (or HYBRID) version as it allows for better parallelization. In both cases, make absolutely sure that the number of threads/MPI processes you use is equal to the number of CPU cores you have.
>*   GTRCAT vs. GTRGAMMA: GTRCAT model is faster to compute compared to the standard GAMMA model, and might better
    account for among-site heterogeneity as it has more rate categories (default: 25). However, it shouldn't be used on alignments with few taxa (<50-100) because of the risk of overparametrization.
>*   +I models: we generally do not recommend using GTRCATI/GTRGAMMAI, since the use two orthogonal approaches to model rate heterogeneity, which might lead to problems in numerical optimization.
>*   Please refer to RAxML manual for further details: http://sco.h-its.org/exelixis/resource/download/NewManual.pdf
