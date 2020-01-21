# Salmon index

### Updated: Jan 20, 2020
> Huitian (Yolanda) Diao <br>
> salmon/0.14.1
> Location: /gpfs/group/pipkin/hdiao/ref_resources/GRCm38.salmon.index

**0. Input genome reference file** <br>
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

**1.Salmon index generation** <br>
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




