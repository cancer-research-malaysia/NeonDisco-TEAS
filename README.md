# NEONDISCO-TEAS

## Discovery pipeline for transposable element and alternative splicing derived neoantigens

This repo will document my work on transposable element and alternative splicing from derived neoantigens pipeline on a modular system called NEONDISCO.

## 1. Building image for ChimeraTE 

This step is to build a Docker image of ChimeraTE. ChimeraTE is a tool to detect transcripts with paired end RNA-seq developed by Oliveira, D. S., et al.(2023). It has two running Modes:

* Mode 1 chimeric transcripts detection based upon exons and TE copies positions in the genome sequence;

* Mode 2 chimeric transcripts detection regardless the genomic position, allowing the detection of chimeras from TEs that are not present in the referece genome, but with less sensitivity.

ChimeraTE requires the installation of all this dependancy in your path.

### Python dependency:
- Python 3.6+
- Termcolor 1.1.0
- Pybedtools 0.9.0
- Pandas 1.1.5
- Dateutil 2.8.2
- h5py 3.1.0
- numpy 1.19.5

### Softwares:
- Bedtools 2.30.0
- BLAST 2.13+
- Bowtie 2.5.1
- Cufflinks 2.2.1
- express 1.5.1
- RepeatMasker 4.1.2
- Trinity 2.9.1
- Seqtk 1.3
- Samtools 1.7
- STAR 2.7.10

## 2. Push to DockerHub
