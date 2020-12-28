# Bowtie2 index

## Updated: Dec. 28, 2020 (updated both hs & mm)
> Huitian (Yolanda) Diao <br>
> bowtie2/2.4.2 <br>
> HPC Location: /gpfs/group/pipkin/hdiao/ref_resources <br>

## Mus Musclus
### **0. Input genome reference file** <br>
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
[Related topic: choice of ensembl genome version](https://bioinformatics.stackexchange.com/questions/540/what-ensembl-genome-version-should-i-use-for-alignments-e-g-toplevel-fa-vs-p)
- Release 100, updated March 2020

## Homo Sapiens
### **0. Input genome reference file** <br>
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
- Homo_sapiens.GRCh38.cdna.all.fa.gz, 3/4/20
- Gtf: Homo_sapiens.GRCh38.100.gtf.gz, 3/7/20
- Genome: Homo_sapiens.GRCh38.dna_sm.toplevel.fa.gz, 3/5/20

## Codes
```
#!/bin/bash

module load bowtie2

# mm
cd /gpfs/group/pipkin/hdiao/ref_resources/mm/release100
bowtie2-build Mus_musculus.GRCm38.dna.toplevel.fa GRCm38_bowtie2

# hs
cd /gpfs/group/pipkin/hdiao/ref_resources/hs/release100
bowtie2-build Homo_sapiens.GRCh38.dna.toplevel.fa GRCh38_bowtie2
```
