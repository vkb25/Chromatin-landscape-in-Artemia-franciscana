# Mapping of RNA reads to annotated CDS of Artemia franciscana

Load necessary modules

`module load kallisto`

Indexing the CDS

`kallisto index -i transcripts.idx braker_filconagatwgenes_isoORF3_sup100compgen.codingseq`

Quantification of Transcript abundances

`kallisto quant -t 16 -i transcripts.idx -o file -b 100 file_1.fastq file_2.fastq`

Let's prepare sample information referred to as hiseq_info.txt

```
run_accession   condition
60541   mh
60542   mh
60545   fh
60546   fh
```
# Let's run sleuth

Load the necessary package 

`library("sleuth")`

Let's read the samples and associate them sample information

```
base_dir <- "path/ExpressionKal"

sample_id <- dir(file.path(base_dir, "KalSomatic"))

kal_dirs <- sapply(sample_id, function(id) file.path(base_dir, "KalSomatic", id))

s2c <- read.table(file.path(base_dir, "hiseq_info.txt"), header = TRUE, stringsAsFactors=FALSE)

s2c <- dplyr::select(s2c, sample = run_accession, condition)

s2c <- dplyr::mutate(s2c, path = kal_dirs)
```

Steps below involve as described in [](https://pachterlab.github.io/sleuth_walkthroughs/trapnell/analysis.html)

(1) load the kallisto processed data into the object

(2) estimate parameters for the sleuth response error measurement (full) model

(3) estimate parameters for the sleuth reduced model, and

(4) perform differential analysis (testing) using the likelihood ratio test

```
so <- sleuth_prep(s2c, extra_bootstrap_summary = TRUE)

so <- sleuth_fit(so, ~condition, 'full')

so <- sleuth_fit(so, ~1, 'reduced')

so <- sleuth_lrt(so, 'reduced', 'full')

results_table <- sleuth_results(so, 'reduced:full', test_type = 'lrt')

```

we can get the results of this analysis

```
SummaryKallisto_table<- sleuth_to_matrix(so, "obs_norm", "tpm")

write.table(results_table, file = "DEtranscripts_mhfh.txt")

write.table(SummaryKallisto_table, file = "KallistoSummary_mhfhtranscripts.txt")

genes<-read.table("braker_filconagatwgenes_isoORF3_sup100compgen_transcript.bed", sep="\t", head=T)

t2g <- dplyr::rename(genes, target_id = Transcript.stable.ID,  ens_gene = Gene.stable.ID)

so_genes <- sleuth_prep(s2c, ~condition, target_mapping = t2g, aggregation_column = 'ens_gene', gene_mode = TRUE, extra_bootstrap_summary = TRUE)

so_genes <- sleuth_fit(so_genes, ~condition, 'full')

so_genes <- sleuth_fit(so_genes, ~1, 'reduced')

so_genes <- sleuth_lrt(so_genes, 'reduced', 'full')

sleuth_table <- sleuth_results(so_genes, 'reduced:full', 'lrt', show_all = FALSE)

write.table(sleuth_table, file = "DEgenes_mhfh.txt")

kallisto_table<-sleuth_to_matrix(so_genes, "obs_norm", "tpm")

SummaryTPM <- cbind(rownames(kallisto_table), data.frame(kallisto_table, row.names=NULL))

colnames(SummaryTPM)[1] <- "gene"

write.table(SummaryTPM, file = "ExpressionSummary_mhfh.txt")

final<-merge(sleuth_table, SummaryTPM, by.x="target_id", by.y="gene")

write.table(final, file = "DEgenes_expression_mhfh.txt")

pdf("jg20557.pdf", width=14, height=7)

plot_bootstrap(so_genes, "jg20557", units = "scaled_reads_per_base", color_by = "condition")

dev.off()
```

### We then Normalize the expression

```

expf <- read.table("DEgenes_expression_mhfh.txt", head=T, sep=" ")

expf_1 <- expf[, c(13:16)]

rownames(expf_1)<-expf[,1]

bolFMat<-as.matrix(expf_1, nrow = nrow(expf_1), ncol = ncol(expf_1))

library(dplyr)

library(NormalyzerDE)

expf2<-performQuantileNormalization(bolFMat, noLogTransform = T)

rownames(expf2)<-rownames(expf_1)

pdf('Expression_visualizationNormfhmh.pdf',width=7,height=7)

boxplot(log2(expf2+1))

dev.off()

expf_2<-expf[,c(2:3)]

expf3 <- data.frame(expf2, expf_2)

write.table(expf3, file = "Expression_afranciscana_headsnormalizedTPM.txt", quote=F)
```



