# Reference Genome Maintainance

* [ChIP blacklisted region](https://www.encodeproject.org/annotations/ENCSR636HFF/)

**Generate Chromesome Sizes Reference Files**
```
#!/bin/bash

mm_dir=/home/pipkin/references/GRCm38.102
cd $mm_dir

samtools faidx Mus_musculus.GRCm38.dna_sm.toplevel.fa
cut -f1,2  Mus_musculus.GRCm38.dna_sm.toplevel.fa.fai > GRCm38.genome.sizes

hs_dir=/home/pipkin/references/GRCh38.102
cd $hs_dir

samtools faidx Homo_sapiens.GRCh38.dna_sm.toplevel.fa
cut -f1,2 Homo_sapiens.GRCh38.dna_sm.toplevel.fa.fai > GRCh39.genome.sizes
```
