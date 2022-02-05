# Confidence_intervals
Bootstrap resampling for some tasks

## MT quality: Bleu - TER - Meteor

```
Usage:	 confidence intervals.sh <-r reference> <-t hypothesis> <-n nreps>  <-l lan> 
 	                          [-b baseline] [-i interval] [-y] [-v] [-h] 
 	 This script will take up a reference file and a hypothesis file and compute TER and BLEU confidence 
 	 intervals by means of bootstrapping. Note: This script needs a *modified* version of TERCOM and 
 	 multi-bleu.perl. These two modified versions are included into this script for simplicity purposes and 
 	 unpacked on the fly. If [-b baseline] is specified, pairwise improvement intervals will also be computed. 
 Input:	 -r reference: file containing the reference translations. 
 	 -b baseline: file containing the baseline translations. If specified, pair 
 	 -t hypothesis: file containing the (machine) translations to be evaluated. 
 	 -n nreps: number of repetitions to do via bootstrapping. 
 	 -i interval: confidence interval to compute (default 95) 
 	 -y: do not delete temporary files.
   -l: language (required for Meteor).  
 	 -v: activate verbose mode (set -x). 
 	 -h: show this help and exit. 
 Output: - confidence interval
```

## How to run - multiple references
 

 ```
 ./confidence_intervals.sh  -r ref_1.txt -r ref_2.txt -r  ref_3.txt  -r /ref_4.txt- r ref_5.txt -b baseline.txt  -t  you_result.txt -n 1000 
 
```

Result

```
Confidence intervals for candidate hypotheses:
BLEU   95.0% confidence interval:           9.9000 -- 10.8000 ( 10.3541 +- 0.4524 ) - BLEU stdev: 0.2287 
BP     95.0% confidence interval:           0.8340 --  0.8470 ( 0.8404 +- 0.0064 ) 
TER    95.0% confidence interval:           72.8000 -- 73.8000 ( 73.3055 +- 0.5232 ) - TER stdev: 0.2652 
METEOR 95.0% confidence interval:           16.0000 -- 16.6000 ( 16.3058 +- 0.2634 ) - METEOR stdev: 0.1326 

Confidence intervals for baseline:
BLEU    95.0% confidence interval:       9.7000 -- 10.6000 ( 10.1687 +- 0.4443 )
BP      95.0% confidence interval:       0.8340 --  0.8470 (  0.8253 +- 0.0061 )
TER     95.0% confidence interval:       72.4000 -- 73.5000 ( 72.9705 +- 0.5226 )
METEOR  95.0% confidence interval:       16.0000 -- 16.5000 ( 16.2475 +- 0.2607 )

BLEU    pairwise improvement 95.0% interval:  0.0000 --  0.4000 (  0.2065 +-  0.1615 )
BP      pairwise improvement 95.0% interval:  0.0130 --  0.0180 (  0.0153 +-  0.0026 )
TER     pairwise improvement 95.0% interval:  0.1000 --  0.5000 (  0.3374 +-  0.2067 )
METEOR  pairwise improvement 95.0% interval:  0.0000 --  0.1000 (  0.0508 +-  0.0812 )
Computing statistical significance with approximate_randomization...
Computing significance level of BLEU
	 Significance level: 0.000999000999000999
Computing significance level of TER
	 Significance level: 0.000999000999000999


```



## IMT effort estimation: WSR - MAR (or other metrics)
```
Usage:	 imt_confindence intervals.sh <-t scores> <-n nreps> 
 	                          [-b baseline] [-i interval] [-y] [-v] [-h] 
 	 This script will take up a WSR and MAR scores file and compute MAR and WSR confidence 
 	 intervals by means of bootstrapping. If [-b baseline] is specified, pairwise improvement 
 	 intervals will also be computed. 
 Input:	 -b baseline: file containing the baseline scores. If specified, pair 
 	 -t scores: file containing the scores to be evaluated. 
 	 -n nreps: number of repetitions to do via bootstrapping. 
 	 -i interval: confidence interval to compute (default 95) 
 	 -y: do not delete temporary files. 
 	 -v: activate verbose mode
 	 -h: show this help and exit. 
 Output: - confidence interval
```


# Approximate Randomization Testing

Requires `art`: https://github.com/smartschat/art .

Two-sided paired approximate randomization tests to assess the statistical significance of the difference in performance between two systems, A and B.
 
art.sh <-r reference> <b output-systemA > <-t output-systemB > <-n nreps>  <-l lan> 

 
