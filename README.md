## Introduction
VMP-Seq is a pipeline designed to characterize the molecular state of AAV (Adeno-Associated Virus) genomes based on long-read mapping. This pipeline is particularly useful for analyzing sequencing data from Pacific Biosciences platforms. Below, you'll find instructions on how to set up the environment, install the required software, and execute the pipeline.

## Usage
### Environment Setup
Before running the analysis, ensure that all necessary files are present in the working directory.

### Software Installation
Install Anaconda: You can install Anaconda from here. This is required for managing SMRT or R packages.

Obtain SMRT Packages: You can freely clone the required SMRT packages from the PacificBiosciences GitHub.

SMRT_Link Documentation: Get support and documentation for SMRT_Link from PacBio's official website.

Recalladapters: For adapter recall, visit this link.

CCS (Circular Consensus Sequence): The CCS tool can be found here.

Minimap2: For Minimap2, check out lh3's GitHub repository.

BLAST: Install BLAST from the Bioconda repository.

Seqkit-tools: Seqkit-tools can be installed from the Bioconda repository.

R: R can be installed using Anaconda from this link.

### Procedure
#### (01)Preparation.sh
Check for Required Files: This script verifies the presence of specific files generated by Pacific Biosciences sequencing platforms, such as subreadset.xml. If these files are missing, the script terminates.

HiFi Output Processing: Adapter recall and CCS generation are performed, resulting in high-fidelity reads. The output sequences are then formatted into FASTA.

Minimap2 Alignments: HiFi reads are aligned to a reference genome using Minimap2, generating various output files. Additional processing is done with the samtools package.

BLAST-Based Alignments: BLAST is used to perform DNA sequence alignments in a looped fashion. The LS and RS Python scripts further process the BLAST results.

#### (02)Rearrange.sh
"Bash Script":

Function process_file(): A series of operations is applied to BLAST results or tabular data.

Main Execution Loop: Files with a specific naming convention are processed based on certain conditions.

Execute R Code: An embedded R script is executed.

"R Script":

Data Visualization: A histogram is created from the Flen.txt file and saved as dlen.png.

Data Processing: A series of functions and operations process files in specific directories, merge their data, and save combined results.

#### (03)Visualization.sh
This script calculates the ratio of the main molecule configuration. Note that if you are processing wild-type AAV sequencing reads, you should update the Subgenome() and plot() functions. Additionally, format.csv should be updated with important sites of the target AAV virus genomes, such as ITR, promoter, etc.

Subgenome(): Calculates main configurations like FULL, SBG, ICG, GDM.
This polished version provides a clearer and more organized overview of the VMP-Seq pipeline and its usage.
