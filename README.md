# :dna: Pedigree Analysis

## variantCalling workflow

**Steps**:

1 - Converts *sam files* to *bam files*

2 - Creates indexed *bam files (bai)* with *samtools*

3 - Performs variant calling with *freebayes* using a reference genome. It results in *vcf files*.

4 - These files are compressed using *bgzip* and indexed using *tabix*.

```snakemake -s variantCalling -c 50 --use-conda```

**Dependencies:**
 
 - samtools;
 - freebayes;
 - bcftools.
