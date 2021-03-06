# micro RNA titration experiment
--------------------------------------
This experiment was performed to identify the minimal
required input yield of microRNA for sequencing.

### Experimental design

We intended to compare concentrated RNA vs non-concentrated
RNA from the same samples at different concentrations (200ul,
400ul). We also tried to define the minimal input concentration
required for sequencing to get reliable, statistically significant
results. Lastly, we looked at the reproducibility in different
samples from the same cell line as well as from two different cell
lines (CD14 and CD4).

| sample name         | input yield |
| ------------------- | ---- |
| AS035_CD4_200_SV    | 40.0 |
| OBB4633_CD14_400_SV | 79.6 |
| OBB4633_CD4_200     | 40.4 |
| OBB4633_CD4_200_SV  | 40.0 |
| OBB3073_CD14_150ng  | 30.0 |
| OBB3073_CD14_200ng  | 40.0 |
| OBB3073_CD14_250ng  | 50.0 |
| OBB3073_CD14_300ng  | 60.0 |
| OBB3073_CD4_150ng   | 30.0 |
| OBB3073_CD4_200ng   | 40.0 |
| OBB3073_CD4_250ng   | 50.0 |
| OBB3073_CD4_300ng   | 60.0 |
| OBB2657_CD4_150ng   | 30.0 |
| OBB2657_CD4_200ng   | 40.0 |
| OBB2657_CD4_250ng   | 50.0 |
| OBB2657_CD4_300ng   | 60.0 |

Unfortunately the following four samples were not sequenced due to
technical issues:

- AS035_CD4_200 (non-SpeedVac paired with AS035_CD4_200_SV),
- OBB4633_CD14_400 (non-SpeedVac paired with OBB4633_CD14_400_SV), 
- AS035_CD14_400 and AS035_CD14_400_SV (the second pair of SV / nonSV
at the concentration of 400).


### Bioinformatic analysis
 
[Matrix](https://github.com/jknightlab/mirna_pipeline/blob/master/mirna_titration_matrix.txt)
generated from the files with numbers of reads mapped to known microRNAs
created by `Htseq`.

On this plot we can see that all concentrations starting from 150ng
(except for one sample, which is most likely just an outliar) generate
sufficient amount of reads mapping to microRNAs -- above 8 mln (median
at 10 mln). This suggest that the initial RNA yield can be as low
as 150 nl.

![alt text](https://github.com/jknightlab/mirna_pipeline/blob/master/all_samples.mapped_reads.png)

On this plot we can see that samples generate using SpeedVac-concentrated
microRNA generate numbers of reads comparable to the amount of reads from
samples non-concentrated RNA (same samples or different samples). Therefore,
when the input yield of a certain sample is not enough, we can benefit from
concentrating RNA (and rather not sequence non-concentrated RNA at very low
input yield).

![alt text](https://github.com/jknightlab/mirna_pipeline/blob/master/SV_vs_nonSV.mapped_reads.png)


**How comparable are different samples**

Apart from looking at raw numbers of reads mapped to known microRNAs, we also
looked at how reproducible the technique is and how comparable the samples
are. After counting reads mapped to each known microRNA, we calculated the
Pearson's correlation coefficient between each pair of the samples. Two
tables down below contain the correlation coefficients.


*Table 1. Comparison of concentrated and non-concentrated microRNA samples*

| Concentration | Same sample | Diff. sample, same cell line | Diff. cell line |
| ------------- | ----------- | ---------------------------- | --------------- |
| 200 ul        | 0.95        | 0.96                         | 0.43            |
| 400 ul*       | NA          | 0.99                         | 0.72            |

* Since only one sample at 400ul was available, it was compared with the samples
at 300 ul.

This table indicates that, when comparing concentrated versus non-concentrated
RNA from the same cell line, regardless of whether the sample is the same or not,
the correlation is high for 200ul and even higher for 400ul. This suggests that
concentrated RNA samples can be compared with non-concentrated samples, however,
preferably at higher concentrations.


*Table 2. Comparison of the titration results*

| Type of comparison | 150 ul | 200 ul | 250 ul | 300 ul |
| ------------------ | ------ | ------ | ------ | ------ |
| Same concentration |        |        |        |        |
| Same cell line     | 0.98   | 0.98   | 0.99   | 0.98   |
| Diff. cell lines   | 0.68   | 0.71   | 0.71   | 0.73   |
| Diff. concentration|        |        |        |        |
| Same sample        | 0.99   | 0.99   | 0.99   | 0.99   |
| Same cell line     | 0.97   | 0.99   | 0.99   | 0.99   |
| Diff. cell lines   | 0.71   | 0.71   | 0.71   | 0.71   |

This table indicates that:
- samples at different concentrations produce very similar results;
- different samples from the same cell line produce very similar results.
- We can reproduce the data very well already at 150 ul.

### Conclusions

1. The input RNA yield of 150 ul produces sufficient amount of reads.
2. Samples of different concentrations from the same cell line generate
reproducible and comparable results.
3. Concentrating RNA generates samples close to non-concentrated RNA.
It is suggested to generated concentrated samples with higher concentrations
(i.g., rather 400ul than 200ul).



#### Designed by Irina Pulyakhina irina@well.ox.ac.uk
