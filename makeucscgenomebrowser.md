### Load necessary modules
```
module load python3
module load ucscGenomeBrowser
module load samtools
module load BRAKER
```

### Run makehub to generate output for ucsc genomebrowser
Following guidelines in this we combine masked genome, maker annotation, braker annotation to generate compatible files that are housed in shrimp directory [](https://github.com/Gaius-Augustus/MakeHub). The outputs are hosted in Cyverse [](https://user.cyverse.org/).
```
python Tools/MAKEHUB/make_hub.py -l shrimp -L "Brine shrimp" -N "Artemia franciscana" -g Artemia_franhifiNewGenomeNewWscaff/Annotation/asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa.masked -a Artemia_franhifiNewGenomeNewWscaff/Annotation/braker_staralignrnd2/braker_filconagatwgenes_isoORF3_sup100compgen.gtf --maker_gff Artemia_franhifiNewGenomeNewWscaff/MakerAnnotation/Afran_round5rep.maker.output/Afran_round5rep.all.maker.gff --bam Artemia_franhifiNewGenomeNewWscaff/Expression/60541_brakmaskedAligned.sortedByCoord.out.bam Artemia_franhifiNewGenomeNewWscaff/Expression/60543_brakmaskedAligned.sortedByCoord.out.bam Artemia_franhifiNewGenomeNewWscaff/Expression/60545_brakmaskedAligned.sortedByCoord.out.bam Artemia_franhifiNewGenomeNewWscaff/Expression/60547_brakmaskedAligned.sortedByCoord.out.bam -c 10 -e vbett@ist.ac.at --outdir shrimp
```
