# :dna: Pedigree Analysis -  Generate SNP Panel

## variantCalling workflow

**Steps**:

1 - Converts *sam files* to *bam files*

2 - Creates indexed *bam files (bai)* with *samtools*

3 - Performs variant calling with *freebayes* using a reference genome. It results in *vcf files*

4 - These files are compressed using *bgzip* and indexed using *tabix*

5 - Filter variants considering MAF, Hardy-Weinberg Equilibrium & missing variants proportion with Plink. This step generates a *bed* file

6 - Converts *bed* file back to *vcf* format also using Plink

7 - Compress and index filtered *vcf* files as in step 4

8 - Get the common variants considering all individuals of same family with *bedtools isec*

9 - Load the files with common SNPs of each family on R and analyse it (Venn graph and comparisons between families)

```snakemake -s variantCalling -c 50```

**Environment**

 - Download [Snakemake Docker Image](https://hub.docker.com/r/snakemake/snakemake)

 - Start container

 ```docker run --name SnakemakeV1 -it <image_id> bash```
 
 - Copy your files to container

  ```docker cp <directory/files> <id_container>:<directory>```
 
 - Create environment from file *(in the container)*:
 
```conda env create -f environment.yaml```
