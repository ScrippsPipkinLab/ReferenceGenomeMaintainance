# Salmon index

### Updated: Jan 20, 2020
> Huitian (Yolanda) Diao <br>
> salmon/0.14.1

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
1.0 Download Salmontools
```
scp /Users/yolandatiao/Downloads/SalmonTools-master.zip hdiao@login01.scripps.edu:/gpfs/group/pipkin/hdiao/Pkgs
unzip SalmonTools-master.zip
```
1.1 Generate Decoy transcriptome
```
```



