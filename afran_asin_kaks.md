# Let's run our automated pipeline on the gene annotations of A fran and A sin

WD: /nfs/scistore18/vicosgrp/bvicoso/AutoKaKs/Vincent_AfranAsin_24

Final files:
* Nei-Gojobori Ka and Ks: /nfs/scistore18/vicosgrp/bvicoso/AutoKaKs/Vincent_AfranAsin_24/Afran_Asin_kaks_NG.txt
* Yang-Nielsen Ka and Ks: /nfs/scistore18/vicosgrp/bvicoso/AutoKaKs/Vincent_AfranAsin_24/Afran_Asin_kaks_YN.txt

## Get data (shared by Vincent)

```
cp /nfs/scistore18/vicosgrp/vbett/Artemia_franhifiNewGenomeNewWscaff/Expression/braker_filconagatwgenes_isoORF3_sup100compgen.codingseq . 
mv braker_filconagatwgenes_isoORF3_sup100compgen.codingseq Afran.fa

cp /nfs/scistore18/vicosgrp/vbett/Artemia_sinicaAnnWscaff/braker_Asinstaralignrnd2/braker_filconagatwgenes_isoORF3_sup100compgen.codingseq .
mv braker_filconagatwgenes_isoORF3_sup100compgen.codingseq Asin.fa

ln -s ../BLAKL.pl .
```

## Run BLAKL.pl

This pipeline:
* runs blat in both directions
* picks reciprocal best hits
* aligns the CDS with translatorX, and cleans the alignment with gblocks
* estimates Ka and Ks with KaKs_calculator


```
module load blat/20170224
module load gblocks/0.91b
module load muscle

srun perl BLAKL.pl Afran.fa Asin.fa Afran_Asin/
```

Then parse the files:

```
cat Afran_Asin/KaKs/* | cut -f 1,2,3,4,5,6,7 | grep 'NG' > Afran_Asin_kaks_NG.txt
cat Afran_Asin/KaKs/* | cut -f 1,2,3,4,5,6,7 | grep 'YN' > Afran_Asin_kaks_YN.txt
```

Add headers:

```
(echo "Sequence  Method  Ka      Ks      Ka/Ks   P-Value(Fisher) Length"  && cat Afran_Asin_kaks_YN.txt) > filename1 && mv filename1 Afran_Asin_kaks_YN.txt
(echo "Sequence  Method  Ka      Ks      Ka/Ks   P-Value(Fisher) Length"  && cat Afran_Asin_kaks_YN.txt) > filename1 && mv filename1 Afran_Asin_kaks_YN.txt
```