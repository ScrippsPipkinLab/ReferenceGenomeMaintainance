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
- Release 100, updated March 2020

### **1.Salmon index generation** <br>
**Generated decoy-augmented transcriptomes according to updated guideline. Please use with selective-alignment (via the –validateMappings, –mimicBT2 or –mimicStrictBT2 flags)** <br>
1.0 Install Salmontools (JC did) <br>
1.1 Generate Decoy transcriptome <br>
1.2 Generate salmon index
```
#!/bin/bash
#PBS -l nodes=1:ppn=8

module load salmon
module load mashmap
module load bedtools

wkdir=/gpfs/group/pipkin/hdiao/ref_resources/mm/release100
cd $wkdir

cDNA_fa=Mus_musculus.GRCm38.cdna.all.fa
genome_gtf=Mus_musculus.GRCm38.100.gtf
genome_fasta=Mus_musculus.GRCm38.dna.toplevel.fa

gdt_script=generateDecoyTranscriptome.sh

$gdt_script -a $genome_gtf  -t $cDNA_fa -g $genome_fasta -o . -j 8

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
1.2 Generate salmon index <br>
```
#!/bin/bash
#PBS -l nodes=1:ppn=8

module load salmon
module load mashmap
module load bedtools

wkdir=/gpfs/group/pipkin/hdiao/ref_resources/hs/release100
cd $wkdir

cDNA_fa=Homo_sapiens.GRCh38.cdna.all.fa
genome_gtf=Homo_sapiens.GRCh38.100.gtf
genome_fasta=Homo_sapiens.GRCh38.dna.toplevel.fa

gdt_script=generateDecoyTranscriptome.sh

$gdt_script -a $genome_gtf  -t $cDNA_fa -g $genome_fasta -o . -j 8

salmon index -t $cDNA_fa -i GRCh38.salmon.index --decoys decoys.txt -k 31
```







