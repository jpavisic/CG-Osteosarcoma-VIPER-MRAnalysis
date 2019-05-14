# CBMF4761 Computational Genomics Spring 2019

This repository contains the project software files (source code/scripts, sample input and output files, additional necessary files for running the associated software) for the final project "Identifying Master Regulator Dependencies in Pediatric Osteosarcoma using VIPER" submitted by Jovana Pavisic, jp3679, as her final project for the Columbia University CBMF4761 Computational Genomics class during the Spring 2019 semester.

The source code is presented in the form of a jupyter notebook and can be run with the R kernel enabled. Comments are included within the code how to run each step, the system requirements, and when use of a cluster or more powerful machine may be necessary. In any such cases, we used the Columbia C2B2 cluster.

The required packages are listed in the notebook. All other files needed are included in the same directory. Of note, only the data files that are publicly available are included, specifically the RNAseq gene expression data for pediatric osteosarcoma patients (as TPM counts) and clinical annotations for those patients available through the Therapeutically Applicable Research to Generate Effective Treatments (TARGET) Project. These can be downloaded at any time from the TARGET data matrix: https://ocg.cancer.gov/programs/target/data-matrix.

However, in this project, I used the original RNAseq FASTQ files from 86 pediatric OS patients available through TARGET and 35 pediatric OS patients available from the DFCI Pediatric Osteosarcoma Genomics Project which are under controlled access requiring submission of an application through dbGaP (projects phs000218.v4.p1 and phs000699.v1.p1, respectively), and 40 samples provided by a collaborating institution (UCSF) through a MTA. I then ensured uniform RNA alignment and gene quantification using Kallisto for all the samples and obtained gene expression counts as logTPMs. The publicly available TARGET RNAseq TPM counts are highly correlated with those obtained using Kallisto and thus that will serve as a template file for running the code. Unfortunately, I cannot provide the sequencing or clinical data used in this project from the other two sites or the original RNA sequencing data.

## Files Included in this Repository

1. `FinalProjectSourceCode.ipynb` This is the source code in the form of a jupyter notebook that can be run with R kernel enabled and contains descriptions for running each section.
2. `TARGET_TPM.txt` Read counts measured in transcripts per million which was downloaded directly from the TARGET Osteosarcoma study. This is the sample input one can use for ARACNe or VIPER analyses in the code. 
3. `regulators.csv` Contains a list of potential regulator genes as Entrez IDs divided by transcription factors, co-transcription factors, and signaling proteins required to run ARACNe-AP
4. `final_network.csv` Output of ARACNe-AP run on the 86 TARGET samples from the TARGET_TPM.txt file. This is a table with 4 columns: regulator, target, mutual information score, p-value. Only the first 50 interactions are included as the full file with >2 million interactions is quite large.
5. `TARGET_OS_Discovery_ClinicalData.csv` This file contains all of the patient clinical data, like relapse status, metastatic disease status, and survival times.
6. `ens2entrez.rda` This has information for mapping gene labels from ensembl ids to entrez ids. This is necessary for downstream MR processing. 
7. `viper_dset.csv` A precomputed table of master regulator normalized enrichment scores for each of 84 TARGET patients (this is the output from running metaVIPER with the pan-cancer interactome). The process used to generate this file is described in detail in the report. 

