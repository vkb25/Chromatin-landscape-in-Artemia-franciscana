### Spectacle estimates Hidden Markov Model parameters using a spectral learning algorithm

#### Binarize Bed files:

```
java -mx50000M -jar /nfs/scistore18/vicosgrp/vbett/Tools/Spectacle/Spectacle.jar BinarizeBed -b 200 -strictthresh asm_np_female.chromsizes inputbeddir cellmarkfiletablerepp outputbinarydirppspec
```

#### running LearnModel using Spectral Learning from chromatin state 21 to chromatin state 2

```
java -mx50000M -jar /Spectacle/Spectacle.jar BinarizeBed -b 200 -strictthresh asm_np_female.chromsizes inputbeddir cellmarkfiletablerepp outputbinarydirppspec

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec25 25 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb -p 4 outputbinarydirppspec outputlearnmodelppspec24 24 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec23 23 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec22 22 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec21 21 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec20 20 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec19 19 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec18 18 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec17 17 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec16 16 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec15 15 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec14 14 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec13 13 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec12 12 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec11 11 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /nfs/scistore18/vicosgrp/vbett/Tools/Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec10 10 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec9 9 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec8 8 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec7 7 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec6 6 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec5 5 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec4 4 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec3 3 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

java -mx50000M -jar /Spectacle/Spectacle.jar LearnModel -p 4 -b 200 -nobrowser -noenrich -l asm_np_female.chromsizes -i spectral -comb outputbinarydirppspec outputlearnmodelppspec2 2 asm_np_female_mkf02_01_09_2023_renamed_final_fin_wscaff.fa

```

#### we employed the CompareModels function within Spectacle to identify ideal chromatin state number

`java -mx50000M -jar /Spectacle/Spectacle.jar CompareModels modelemissioncomparedir/emissions_21_spectral.txt modelemissioncomparedir modelemissioncomparedir/modelemissioncomparediroutput`

#### The coverage of each emission state (chromatin state 12) across the A. franciscana genome was generated using the MakeSegmentation function

`java -mx50000M -jar /Spectacle/Spectacle.jar MakeSegmentation -b 200 outputlearnmodelppspec12/model_12_spectral.txt outputbinarydirppspec outputmakesegmentationspec12`

#### The outputs were then intersected with the coordinates of genes using bedtools intersect function under default settings

`bedtools intersect -wa -wb -a braker_filconagatwgenes_isoORF3_sup100compgen_genefil.bed -b outputmakesegmentationspec12/mh_12_segments.bed > outputmakesegmentationspec12/mh_12_segments_genes.bed`
