# Cellranger reference genome

## Updated: June 4th, 2020 (update mm & hs)
> Huitian (Yolanda) Diao <br>
> cellranger-3.1.0 <br>
> Location: /gpfs/group/pipkin/hdiao/ref_resources <br>
> [How to choose reference genome](https://genestack.com/blog/2016/07/12/choosing-a-reference-genome/)

## 1. Mus Musclus
## 1.1 Input files
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
- DNA fasta file: release 100, last update 3/5/20 <br>
- GTF file: release 100, last update 3/9/20 <br>

## 1.2 Build reference genome
```
#!/bin/bash
# Filter gtf 
# https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/advanced/references#mkgtf

module load cellranger

wkdir=/gpfs/group/pipkin/hdiao/ref_resources/mm/release100
cd $wkdir

cellranger mkgtf Mus_musculus.GRCm38.100.gtf Mus_musculus.GRCm38.100.filtered.gtf\
                   --attribute=gene_biotype:protein_coding \
                   --attribute=gene_biotype:lincRNA \
                   --attribute=gene_biotype:antisense \
                   --attribute=gene_biotype:IG_LV_gene \
                   --attribute=gene_biotype:IG_V_gene \
                   --attribute=gene_biotype:IG_V_pseudogene \
                   --attribute=gene_biotype:IG_D_gene \
                   --attribute=gene_biotype:IG_J_gene \
                   --attribute=gene_biotype:IG_J_pseudogene \
                   --attribute=gene_biotype:IG_C_gene \
                   --attribute=gene_biotype:IG_C_pseudogene \
                   --attribute=gene_biotype:TR_V_gene \
                   --attribute=gene_biotype:TR_V_pseudogene \
                   --attribute=gene_biotype:TR_D_gene \
                   --attribute=gene_biotype:TR_J_gene \
                   --attribute=gene_biotype:TR_J_pseudogene \
                   --attribute=gene_biotype:TR_C_gene
                   
cellranger mkref --genome=GRCm38 \
                 --fasta=Mus_musculus.GRCm38.dna.primary_assembly.fa \
                 --genes=Mus_musculus.GRCm38.100.filtered.gtf \
                 --ref-version=3.1.0
```

## 2. Homo Sapien
## 2.1 Input files
Download from [Ensembl](http://useast.ensembl.org/info/data/ftp/index.html) <br>
- DNA fasta file (use primary assembly as cellranger suggested): last update 3/4/20 <br>
- GTF file: last update 3/7/20 <br>

## 2.2 Build reference genome
```
#!/bin/bash
# Filter gtf 
# https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/advanced/references#mkgtf

module load cellranger

wkdir=/gpfs/group/pipkin/hdiao/ref_resources/hs/release100
cd $wkdir

cellranger mkgtf Homo_sapiens.GRCh38.100.gtf Homo_sapiens.GRCh38.100.filtered.gtf\
                   --attribute=gene_biotype:protein_coding \
                   --attribute=gene_biotype:lincRNA \
                   --attribute=gene_biotype:antisense \
                   --attribute=gene_biotype:IG_LV_gene \
                   --attribute=gene_biotype:IG_V_gene \
                   --attribute=gene_biotype:IG_V_pseudogene \
                   --attribute=gene_biotype:IG_D_gene \
                   --attribute=gene_biotype:IG_J_gene \
                   --attribute=gene_biotype:IG_J_pseudogene \
                   --attribute=gene_biotype:IG_C_gene \
                   --attribute=gene_biotype:IG_C_pseudogene \
                   --attribute=gene_biotype:TR_V_gene \
                   --attribute=gene_biotype:TR_V_pseudogene \
                   --attribute=gene_biotype:TR_D_gene \
                   --attribute=gene_biotype:TR_J_gene \
                   --attribute=gene_biotype:TR_J_pseudogene \
                   --attribute=gene_biotype:TR_C_gene
                   
cellranger mkref --genome=GRCh38 \
                 --fasta=Homo_sapiens.GRCh38.dna.primary_assembly.fa \
                 --genes=Homo_sapiens.GRCh38.100.filtered.gtf \
                 --ref-version=3.1.0
```

