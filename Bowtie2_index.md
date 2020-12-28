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

```
Fatal Python error: Py_Initialize: Unable to get the locale encoding
  File "/opt/applications/python/2.7.11/gnu/lib/python2.7/encodings/__init__.py", line 123
    raise CodecRegistryError,\
                            ^
SyntaxError: invalid syntax

Current thread 0x00007feed3703740 (most recent call first):
/var/spool/slurm/d/job276169/slurm_script: line 7: 26458 Aborted                 bowtie2-build Mus_musculus.GRCm38.dna.toplevel.fa GRCm38_bowtie2

Fatal Python error: Py_Initialize: Unable to get the locale encoding
  File "/opt/applications/python/2.7.11/gnu/lib/python2.7/encodings/__init__.py", line 123
    raise CodecRegistryError,\
                            ^
SyntaxError: invalid syntax

Current thread 0x00007f22eff55740 (most recent call first):
/var/spool/slurm/d/job276169/slurm_script: line 11: 26459 Aborted                 bowtie2-build Homo_sapiens.GRCh38.dna.toplevel.fa GRCh38_bowtie2
```
