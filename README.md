# Pseudogene pipeline
Scripts and wrapper file for runing the Shiu Lab's pseduogene pipeline. 

# Overview

## Associated publications

* Zou C, Lehti-Shiu, MD, Thibaud-Nissen F, Prakash Th, Buell CR, and Shiu SH (2009) Evolutionary and Expression Signatures of Pseudogenes in Arabidopsis thaliana and Rice. Plant Physiol. 151:3-15. [pubmed](https://pubmed.ncbi.nlm.nih.gov/19641029-evolutionary-and-expression-signatures-of-pseudogenes-in-arabidopsis-and-rice/)
* Campbell M, Law MY, Holt C, Stein J, Moghe G, Hufnagel Du, Lei J, Achawanantakun R, Jiao D, Lawrence C, Ware D, Shiu SH, Childs K, Sun Y, Jiang N, Yandell M (2014) MAKER-P: a tool-kit for the rapid creation, management, and quality control of plant genome annotations. Plant Physiol164(2):513-24 [pubmed](http://www.plantphysiol.org/content/151/1/3)
* Lloyd JP, Tsai ZTY, Sowers RPu, Panchy NL, Shiu SH (2018) A model-based approach for identifying functional intergenic transcribed regions and non-coding RNAs. Mol. Biol. Evol. 35(6):1422-1436 [pubmed](https://pubmed.ncbi.nlm.nih.gov/29554332/) 

## Requirements 

* python 3 (https://www.python.org/downloads/)
* python scripts in the `_scripts` folder
* RepeatMaster (http://www.repeatmasker.org/)
  * A local installation of RepeatMasker is needed. Note that RepeatMasker has other dependencies.
* tfasty (part of the fasta36 package, version 36.0.0 or later; https://github.com/wrpearson/fasta36): 
  * The GitHub version need to be compiled and installed. Please follow the instruction in the README for fasta36.

## Useage

### Cut-to-the-chase

The pipline is run using:  
<pre><code>python _scripts/PseudogenePipeline.py [parameter_file]</code></pre>

To invoke the help function, run:
<pre><code>python _scripts/PseudogenePipeline.py</code></pre>

### About the parameter file

This text file specifies how the pipeline should run and an example can found in in the `_example_files` folder.

### Test run

Two test datasets are provided for you to gauge whether there is any issues.

1. `_test25.tgz`: This compressed file contains a test dataset of 25 proteins that takes ~1 minute to run. To use:

```Python
tar xvzf _test25.tgz
cd _test25
```
Then make sure the `test_parameter_file` in the folder is modified to specifiy:
- The location and name of `tfasty` program.
- The location of `RepeatMasker`. 
- The location of `PseudogenePipeline`'s `_scripts` folder. 
 
Below we assume that you are in the `_test25` folder is in the cloned `PseudogenePipeline` folder. Run the pipeline:

```Python
python ../_scripts/PseudogenePipeline.py test_parameter_file 
```

The `_expected_results` folder contains what you should be seeing.

2. `_test27206.tgz`: This is a test case that is more realistic with a larger _Arabidopsis thaliana_ dataset that takes ~20-30 min to run. 

## Ouput

The output of the pipeline is seperated into the following subfolder:
  
* _intermediate: Intermediate files used to generate final results. 
* These may be removed following a successful run, however if you want a list of pseudogenes generated prior to high confidence  filtering and/or RepatMasker filtering they will be here
* _logs: log files generated by the run
* _results: Output files for the final list of pseudogenes following high confidence and and RepeatMasker filtering
  1. hiConf.RMfilt/hiConf.RMfilt.cdnm - position information for pseudogenes
  2. fa.hiConf.RMfilt/fa.hiConf.RMfilt.cdnm - sequence information for pseudogenes
  3. hiConf.RMfilt.cdnm.gff - gff file with pseudogene annotations 
* NOTE: cdnm versions of the output use simplified pseudogene names.

## Versio info

### v.2.0.0

- Converted to Python 3.
- Some changes so the codes are PEP8-compliant.
- Added license.

### v1.0.0

- Implemented in Python 2.
- Included functionalities for checking parameter and input files.
- The version for the [Campbell et al. (2014) Plant Physiol](http://www.plantphysiol.org/content/151/1/3).
- Python 2-based.
