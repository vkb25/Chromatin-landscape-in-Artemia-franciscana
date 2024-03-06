### Pre-processing and Alignment of CUT&TAG reads
##### Load necessary modules 
```
module load samtools
module load bowtie2/2.4.5
module load bedtools
module load picard
module load bbmap
module load anaconda3/2022.05
source /mnt/nfs/clustersw/Debian/bullseye/anaconda3/2022.05/activate_anaconda3_2022.05.txt
source activate /nfs/scistore18/vicosgrp/vbett/.conda/envs/cutadapt
```
##### Index reference genomes

`
bowtie2-build asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa Afran_genome
`

##### Remove over-represented sequences reported in fastqc using bbmap
`
bbduk.sh in1=file_R1_001.fastq.gz in2=file_R2_001.fastq.gz out1=file_R1_Paired.fastq.gz out2=file_R2_Paired.fastq.gz ref=adapter1.fasta ktrim=r k=31 mink=11 hdist=1 tpe tbo
`

##### Remove adapters using cutadapt
`
cutadapt -a CTGTCTCTTATACAC -A CTGTCTCTTATACAC -O 5 -q 0 -m 20 -j 30 -o file_outR1.fastq.gz -p file_outR2.fastq.gz file1_R1_Paired.fastq.gz file_R2_Paired.fastq.gz
`

##### Alignment of CUT&TAG reads to the indexed reference genomes
`
bowtie2 -x Afran_genome -p 60 --local --very-sensitive-local --no-unal --no-mixed --no-discordant --phred33 -I 10 -X 700 -1 file_outR1.fastq.gz -2 file_outR2.fastq.gz -S file_trimmed.sam &> file_trimbowtie.txt
`

##### Sort the alignment
`java -jar $PICARD SortSam -I file_trimmed.sam -O file_trimmed_sorted.sam -SORT_ORDER coordinate`

##### Mark duplicates
`
java -jar $PICARD MarkDuplicates I=file_trimmed_sorted.sam O=file_trimmed_sorted_duMarked.sam ASSUME_SORTED=TRUE REMOVE_DUPLICATES=FALSE METRICS_FILE=file_picard.dupMark.txt
`

##### Remove duplicates
`
java -jar $PICARD MarkDuplicates I=file_trimmed_sorted_duMarked.sam O=file_trimmed_rDup.sam REMOVE_DUPLICATES=true METRICS_FILE=file_picard.rmDup.txt
`

##### Sorting the alignment
`samtools sort -@ 16 file_trimmed_rDup.sam -o file_trimmed_rDup_sorted.sam`

##### Filtering the alignment 

-F 0x04 remove PCR duplicates

-f 0x2 proper paired retained 

`samtools view -bS -@ 16 -q 2 -F 0x04 -f 0x2 file_trimmed_rDup_sorted.sam -o file_trimmed_rDup.bam`

##### Sorting and Indexing the alignments for downstream analysis
```
samtools sort -@ 16 file_trimmed_rDup.bam -o file_rDupsorted.bam
samtools index -@ 16 file_rDupsorted.bam
```
