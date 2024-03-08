# Running Spectacle on CUT&TAG alignment

### First, we convert alignment sam output of picard to bed format using samtools

`samtools view -bS -@ 16 -q 2 -F 0x04 -f 0x2 file_trimmed_rDup_sorted.sam | bedtools bamtobed -i stdin > file_remdup.bed`

