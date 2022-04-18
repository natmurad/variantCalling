# :dna: Pedigree Analysis -  Generate SNP Panel

## Docker Environment

 - Download the Dockerfile and inside same directory run:

 ```docker build -t <IMAGE_TAG> .```

 - Check the IMAGE ID (look for the name of your image tag):

 ```docker images -a```
 
 - Start container

 ```docker run --name <CONTAINER_NAME> -it <IMAGE_ID> bash```
 
 - Copy your files to container

  ```docker cp <DIRECTORY/FILES> <CONTAINER_ID>:<DIRECTORY>```
  
  
## variantCalling Workflow

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

## Prepare code before running:

### Change in the file *"variantCalling"* the path to the *config.yaml* file.

### In *config.yaml* file change the paths for all folder.


## Run pipeline:

```snakemake -s variantCalling -c 50```
