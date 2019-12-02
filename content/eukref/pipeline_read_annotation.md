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
title: 'HTES reads annotation'
---
>**Software needed** Tools necessary to install to run the pipeline are listed below. You should install each of these programs on your computer. Links to software for installations and description can be found at http://eukref.org/tools
>*   [QIIME](http://qiime.org/)
>*   [RaxML](http://sco.h-its.org/exelixis/web/software/raxml/index.html) (version 8 or newer).
>Note: Use TextWrangler, TextEdit or equivalent text editor for taking notes about the curation process, modifying scripts, and viewing files. Should NOT use Word or equivalent.

<span style="color: #ff0000;">Note that these are rough guidelines for the moment.</span>

Align short reads against your reference alignment using [QIIME align_seqs.py](http://qiime.org/scripts/align_seqs.html), then use [RAxML-EPA](http://sco.h-its.org/exelixis/web/software/epa/index.html) to place short reads in your tree. Input files:

*   fasta file of unaligned HTES sequences. This can be all eukaryotes or something specific to your group [unaligned_HTESreads.fas]
*   Curated alignment for your group in fasta format. Must have gaps included – this is your template. [curated_alignment_clade.fas]
*   Phylogenetic tree based on your curated alignment in newick format. You will need to export your tree as newick from FigTree. [RAxML_bestTreeNAME.tre]

Percent identity threshold – how similar should environmental sequences be to your curated sequences to be kept. We recommend setting this threshold to 90% or 95% initially to only pull out sequences from your clade. However, this should be tested empirically, it will vary by group.

**1)** Run the align_seqs.py script within QIIME.

```
align_seqs.py -i unaligned_HTESreads.fas -t curated_alignment_clade.fas -o HTESreads_aligned.fas –p 90
```

**2)** Concatenate aligned HTES reads to your curated alignment. The alignment will be used to build the tree.

```
cat HTESreads_aligned.fas curated_alignment_clade.fas > HTESreads_aligned_plus_curated.fas
```

**3)** Now the alignment needs to be filtered to remove gaps and possible to remove hypervariable positions. This can be done in QIIME with the command below, or with another program.

```
filter_alignment.py -i HTESreads_aligned_plus_curated.fas -g 0.99 -s -e 0.0001 –o HTESreads_aligned_plus_curated_filtered.fas
```

**4)** Place short reads in your reference tree using RaxML-EPA. The –f v option is the EPA placement. Learn more about it here. Use your reference tree here.

```
raxmlHPC-PTHREADS-SSE3 -f v -G 0.2 -m GTRCAT -n EPARUN -s HTESreads_aligned_plus_curated_filtered.fas -t RAxML_bestTreeNAME.tre -T 4
```

**5)** clean the tree so that you can view it in FigTree

```
sed 's/QUERY___//g' RAxML_labelledTree.EPARUN | sed 's/\[I[0-9]*\]//g' > RAxML_placement_tree_NAME.tre
```

**If you have any question or suggestion please feel free to add it to the comment section below, visit our [forum](https://groups.google.com/forum/#!forum/eukref) or send us an [e-mail](mailto:info@eukref.org)**
