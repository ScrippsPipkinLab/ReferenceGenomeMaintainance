# Salmon index

## Updated: Jun 2nd, 2020 (updated hs, not mm)
> Huitian (Yolanda) Diao <br>
> salmon/0.14.1 <br>
> HPC Location: /gpfs/group/pipkin/hdiao/ref_resources <br>
> Pipkinlab Linux computer: ~/references

## Mus Musclus
### **0. Input genome reference file** <br>
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
[Related topic: choice of ensembl genome version](https://bioinformatics.stackexchange.com/questions/540/what-ensembl-genome-version-should-i-use-for-alignments-e-g-toplevel-fa-vs-p)
- Transcriptome: Mus_musculus.GRCm38.cdna.all.fa.gz, 11/19/19
- Gtf: Mus_musculus.GRCm38.99.gtf.gz, 11/22/19
- Genome: Mus_musculus.GRCm38.dna_sm.toplevel.fa.gz, 11/19/19
```
cd /gpfs/group/pipkin/hdiao/ref_resources
wget ftp://ftp.ensembl.org/pub/release-99/fasta/mus_musculus/cdna/Mus_musculus.GRCm38.cdna.all.fa.gz
gunzip Mus_musculus.GRCm38.cdna.all.fa.gz
wget ftp://ftp.ensembl.org/pub/release-99/gtf/mus_musculus/Mus_musculus.GRCm38.99.gtf.gz
gunzip Mus_musculus.GRCm38.99.gtf.gz
wget ftp://ftp.ensembl.org/pub/release-99/fasta/mus_musculus/dna/Mus_musculus.GRCm38.dna_sm.toplevel.fa.gz
gunzip Mus_musculus.GRCm38.dna_sm.toplevel.fa.gz
```

### **1.Salmon index generation** <br>
**Generated decoy-augmented transcriptomes according to updated guideline. Please use with selective-alignment (via the –validateMappings, –mimicBT2 or –mimicStrictBT2 flags)** <br>
1.0 Install Salmontools (JC did) <br>
1.1 Generate Decoy transcriptome <br>
```
#!/bin/bash
#PBS -l nodes=1:ppn=8

module load salmon
module load mashmap
module load bedtools

wkdir=/gpfs/group/pipkin/hdiao/ref_resources
cd $wkdir

cDNA_fa=/gpfs/group/pipkin/hdiao/ref_resources/Mus_musculus.GRCm38.cdna.all.fa
genome_gtf=/gpfs/group/pipkin/hdiao/ref_resources/Mus_musculus.GRCm38.99.gtf
genome_fasta=/gpfs/group/pipkin/hdiao/ref_resources/Mus_musculus.GRCm38.dna_sm.toplevel.fa

gdt_script=generateDecoyTranscriptome.sh

$gdt_script -a $genome_gtf  -t $cDNA_fa -g $genome_fasta -o . -j 8
```
1.2 Generate salmon index
```
#!/bin/bash

module load salmon

wk_dir=/gpfs/group/pipkin/hdiao/ref_resources

cd $wk_dir

cDNA_fa=/gpfs/group/pipkin/hdiao/ref_resources/Mus_musculus.GRCm38.cdna.all.fa
salmon index -t $cDNA_fa -i GRCm38.salmon.index --decoys decoys.txt -k 31
```

**tgMap file for Alevin downloaded from [Ensembl](http://useast.ensembl.org/biomart/martview), GRCm38.p6**


## Homo Sapiens
### **0. Input genome reference file** <br>
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
- Homo_sapiens.GRCh38.cdna.all.fa.gz, 3/4/20
- Gtf: Homo_sapiens.GRCh38.100.gtf.gz, 3/7/20
- Genome: Homo_sapiens.GRCh38.dna_sm.toplevel.fa.gz, 3/5/20

### **1.Salmon index generation** <br>
1.1 Generate Decoy transcriptome <br>
```
#!/bin/bash
#PBS -l nodes=1:ppn=8

module load salmon
module load mashmap
module load bedtools

wkdir=/gpfs/group/pipkin/hdiao/ref_resources/hs
cd $wkdir

cDNA_fa=/gpfs/group/pipkin/hdiao/ref_resources/hs/Homo_sapiens.GRCh38.cdna.all.fa
genome_gtf=/gpfs/group/pipkin/hdiao/ref_resources/hs/Homo_sapiens.GRCh38.100.gtf
genome_fasta=/gpfs/group/pipkin/hdiao/ref_resources/hs/Homo_sapiens.GRCh38.dna_sm.toplevel.fa

gdt_script=generateDecoyTranscriptome.sh

$gdt_script -a $genome_gtf  -t $cDNA_fa -g $genome_fasta -o . -j 8
```

1.2 Generate salmon index
```
#!/bin/bash

module load salmon

wk_dir=/gpfs/group/pipkin/hdiao/ref_resources/hs

cd $wk_dir

cDNA_fa=/gpfs/group/pipkin/hdiao/ref_resources/hs/Homo_sapiens.GRCh38.cdna.all.fa
salmon index -t $cDNA_fa -i GRCh38.salmon.index --decoys decoys.txt -k 31
```







