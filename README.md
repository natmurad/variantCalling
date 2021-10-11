# :dna: Pedigree Analysis

## variantCalling workflow

It gets sam files, converts to bam files and creates the index with samtools and performs variant calling with freebayes using a reference genome.

```snakemake -s variantCalling -c 50 --use-conda```
