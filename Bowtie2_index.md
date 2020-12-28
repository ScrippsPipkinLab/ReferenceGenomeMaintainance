# Bowtie2 index

## Updated: Dec. 28, 2020 (updated both hs & mm)
> Huitian (Yolanda) Diao <br>
> bowtie2/2.4.2 <br>
> HPC Location: /gpfs/group/pipkin/hdiao/ref_resources <br>

## Mus Musclus
### **0. Input genome reference file** <br>
[Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
[Related topic: choice of ensembl genome version](https://bioinformatics.stackexchange.com/questions/540/what-ensembl-genome-version-should-i-use-for-alignments-e-g-toplevel-fa-vs-p)
- Release 102, updated Oct 2020
- Used softmasked toplevel DNA fasta

## Homo Sapiens
### **0. Input genome reference file** <br>
Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
- Release 102, updated Oct 2020
- Used softmasked toplevel DNA fasta

## Codes
```
#!/bin/bash

cd /home/pipkin/references/GRCm38.102
bowtie2-build Mus_musculus.GRCm38.dna_sm.toplevel.fa GRCm38

cd /home/pipkin/references/GRCh38.102
bowtie2-build Homo_sapiens.GRCh38.dna_sm.toplevel.fa GRCh38
```
