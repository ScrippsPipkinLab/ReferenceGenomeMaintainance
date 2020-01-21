# Salmon index

### Updated: Jan 20, 2020
> Huitian (Yolanda) Diao <br>
> salmon/0.14.1

**0. Input genome fasta file** <br>
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html), Mus_musculus.GRCm38.cdna.all.fa.gz, 11/19/19
```
cd /gpfs/group/pipkin/hdiao/ref_resources
wget ftp://ftp.ensembl.org/pub/release-99/fasta/mus_musculus/cdna/Mus_musculus.GRCm38.cdna.all.fa.gz
gunzip Mus_musculus.GRCm38.cdna.all.fa.gz
```

**1.Salmon index generation** <br>
1.0 Download Salmontools
```
scp /Users/yolandatiao/Downloads/SalmonTools-master.zip hdiao@login01.scripps.edu:/gpfs/group/pipkin/hdiao/Pkgs
unzip SalmonTools-master.zip
```
1.1 Generate Decoy transcriptome
```
#!/bin/bash
#PBS -l nodes=1:ppn=8

module load mashmap
module load bedtools

wkdir=/gpfs/group/pipkin/hdiao/ref_resources
cd $wkdir

genome_fa=/gpfs/group/pipkin/hdiao/ref_resources/Mus_musculus.GRCm38.cdna.all.fa

gdt_script=/gpfs/group/pipkin/hdiao/Pkgs/SalmonTools-master/scripts/generateDecoyTranscriptome.sh

$gdt_script -j 8 -a $genome_fa -o .
```



