# Metagenomic Pathogen Identification Pipeline (MetaPathID)
The Metagenomic Pathogen Identification Pipeline (MetaPathID) is designed to improve pathogen identification within a metagenomic context through Illumina short reads or Oxford Nanopore long reads. It includes several sequential steps facilitated by publicly available bioinformatic tools, including metagenome assembly, taxonomic classification, and sequence extraction. While the pipeline described herein has not been integrated into a single software package, each step has been carefully curated and executed using established bioinformatic tools. 

![MetaPathID](https://github.com/jackchen129/Metagenomic-pathogen-identification-pipeline/assets/49889016/6a526218-2a03-49a0-bbf1-3d17a0f1f89e)

This pipeline requires the following publicly available tools: 
1.	Metagenome Assembly: [Spades](https://github.com/ablab/spades) for Illumina short reads; [Flye](https://github.com/tseemann/shovill) for Oxford Nanopore long reads.
2.	Taxonomic Classification: [Kraken 2](https://github.com/DerrickWood/kraken2).
3.	Sequence Extraction: [KrakenTools](https://github.com/jenniferlu717/KrakenTools).
