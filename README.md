# Metagenomic Pathogen Identification Pipeline (MetaPathID)
The Metagenomic Pathogen Identification Pipeline (MetaPathID) is designed to improve pathogen identification within a metagenomic context through Illumina short reads or Oxford Nanopore long reads. It includes several sequential steps facilitated by publicly available bioinformatic tools, including metagenome assembly, taxonomic classification, and sequence extraction. While the pipeline described herein has not been integrated into a single software package, each step has been carefully curated and executed using established bioinformatic tools. 

![MetaPathID](https://github.com/jackchen129/Metagenomic-pathogen-identification-pipeline/assets/49889016/6a526218-2a03-49a0-bbf1-3d17a0f1f89e)

This pipeline requires the following publicly available tools: 
1. Metagenome Assembly: [Spades](https://github.com/ablab/spades) for Illumina short reads; [Flye](https://github.com/fenderglass/Flye) for Oxford Nanopore long reads.
2. Taxonomic Classification: [Kraken 2](https://github.com/DerrickWood/kraken2).
3. Sequence Extraction: [KrakenTools](https://github.com/jenniferlu717/KrakenTools).

# Usage
1. Metagenome Assembly: Spades (`metaspades.py`) or Flye (`--meta`) will be used to assemble Illumina short or Oxford Nanopore long reads, respectively.
2. Taxonomic Classification: Following metagenome assembly, taxonomic classification of the assembled contigs will be performed using Kraken 2. This step involves assigning taxonomic labels to individual sequences based on their similarity to reference sequences in a predefined database.
3. Sequence Extraction: Subsequently, sequences corresponding to specific taxonomic groups of interest will be extracted from the assembled contigs. This extraction process is conducted using the sequence extraction module of KrakenTools (`extract_kraken_reads.py`). The extracted sequences is compiled to generate draft metagenome-assembled genomes (MAGs) representing the targeted taxonomic groups. This extraction encompasses reads classified at both parent (`--include-parents`) and child (`--include-children`)taxonomic levels. These draft MAGs serve as valuable genomic resources for downstream genomic analyses, including pathogen identification and phylogenetic inference.

# Citation
To cite this pipeline, please refer to: 

>[Chen, Z., & Meng, J. (2022). Critical Assessment of Short-Read Assemblers for the Metagenomic Identification of Foodborne and Waterborne Pathogens Using Simulated Bacterial Communities. Microorganisms, 10(12), 2416.](https://www.mdpi.com/2076-2607/10/12/2416)
>
>[Kolmogorov, M., Bickhart, D. M., Behsaz, B., Gurevich, A., Rayko, M., Shin, S. B., ... & Pevzner, P. A. (2020). metaFlye: scalable long-read metagenome assembly using repeat graphs. Nature Methods, 17(11), 1103-1110.](https://www.nature.com/articles/s41592-020-00971-x)
>
>[Lu, J., Rincon, N., Wood, D. E., Breitwieser, F. P., Pockrandt, C., Langmead, B., ... & Steinegger, M. (2022). Metagenome analysis using the Kraken software suite. Nature Protocols, 17(12), 2815-2839.](https://www.nature.com/articles/s41596-022-00738-y)
>
>[Nurk, S., Meleshko, D., Korobeynikov, A., & Pevzner, P. A. (2017). metaSPAdes: a new versatile metagenomic assembler. Genome Research, 27(5), 824-834.](https://genome.cshlp.org/content/27/5/824)
>
>[Wood, D. E., Lu, J., & Langmead, B. (2019). Improved metagenomic analysis with Kraken 2. Genome Biology, 20, 1-13.]{https://link.springer.com/article/10.1186/s13059-019-1891-0}
