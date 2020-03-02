# Pseudogene pipeline
Scripts and wrapper file for runing the Shiu Lab's pseduogene pipeline. 

# Overview

## Associated publication

* Zou C, Lehti-Shiu, MD, Thibaud-Nissen F, Prakash Th, Buell CR, and Shiu SH (2009) Evolutionary and Expression Signatures of Pseudogenes in Arabidopsis thaliana and Rice. Plant Physiol. 151:3-15. [pubmed](https://pubmed.ncbi.nlm.nih.gov/19641029-evolutionary-and-expression-signatures-of-pseudogenes-in-arabidopsis-and-rice/)
* Campbell M, Law MY, Holt C, Stein J, Moghe G, Hufnagel Du, Lei J, Achawanantakun R, Jiao D, Lawrence C, Ware D, Shiu SH, Childs K, Sun Y, Jiang N, Yandell M (2014) MAKER-P: a tool-kit for the rapid creation, management, and quality control of plant genome annotations. Plant Physiol164(2):513-24 [pubmed](http://www.plantphysiol.org/content/151/1/3)

## Requirements 

  * python (2.7 or later, not 3; https://www.python.org/downloads/)
  * python scripts in the _pipeline_scripts folder
  * RepeatMaster (http://www.repeatmasker.org/)
  * tfasty (part of the FASTA package, version 36 or later; http://faculty.virginia.edu/wrpearson/fasta/)

## Useage

  The pipline is run using:  
  <pre><code> _wrapper_scripts/CombinedPseudoWrapper.py [parameter_file]</code></pre>

  An example parameter_file can found in in the _example_files folder

  Additionally, a test case using chromosome 4 from A. thaliana can be run from
  the _testcase folder using the following command from within _testcase. You will
  need to supply the path to your local FASTA install and the name of the tfasty
  program you are using in test_parameter_file.txt.
  <pre><code> python ../_wrapper_scripts/CombinedPseudoWrapper.py test_parameter_file.txt</code></pre>

  The test case takes about 15-30 minutes to run. Expected results of this run
  can be found in the _expected_results subfolder

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
