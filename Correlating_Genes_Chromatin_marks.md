#### Assessment of the enrichment of chromatin marks across genes, we adopted a similar approach in (Anderson, Henikoff, and Ahmad 2023)

aggregating reads with deepTools/multiBamSummary using a bed annotation file, and then normalizing counts based on the number of mapped reads and the gene length in kilobases in Million. The resulting metric provides counts per kilobase per million (CPKM)

```
multiBamSummary BED-file --BED annotation.bed --bamfiles alignment.bam --centerReads --maxFragmentLength 700  -o results.npz --outRawCounts readCounts.tab
```

#### To generate average plots depicting chromatin signals surrounding TSS of genes of each replicate

we applied deepTools/bamcoverage to summarize normalized coverage within a window of 10 bp intervals

```
bamCoverage -b alignment.bam --binSize 10 -p 20 --normalizeUsing RPKM --maxFragmentLength 700 -o file.bw
```

#### To average distribution of chromatin marks of surrounding TSS of genes in both replicates

we used bamCompare function of deepTools 

```
bamCompare --bamfile1 file1.bam --bamfile2 file2.bam -p 20 -bs 5 --normalizeUsing RPKM --skipNAs --minFragmentLength 10 --maxFragmentLength 700 --operation mean --scaleFactorsMethod None -o output.bw
```

#### In order to visualize we used deepTools/computeMatrix and and then use plotProfile feature. 


```
computeMatrix reference-point --referencePoint TSS -S file.bw -R annotation.bed --missingDataAsZero -b 1000 -a 2000 --binSize 5 -o file.mat.gz
```

#### In order to visualize the distribution of H4K16ac in each tissue across all 21 chromosomes of A. franciscana

```
bamCoverage -b file.bam -bs 30000 -p 20 --outFileFormat bedgraph --normalizeUsing RPKM --maxFragmentLength 700 -o file.bedgraph
```
