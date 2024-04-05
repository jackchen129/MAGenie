# MAGenie
A bioinformatic pipeline to reconstruct draft metagenome-assembled genomes (MAGs).

<p align="center">
<img src="https://github.com/jackchen129/MAGenie/assets/49889016/042feb5d-7056-465c-bb44-acf4ccd80737">
</p>

# Introduction
MAGenie is a bioinformatic pipeline designed to reconstruct draft MAGs for downstream pathogen identification within a metagenomic context through Illumina short reads or Oxford Nanopore long reads. It includes several sequential steps facilitated by publicly available bioinformatic tools, including metagenome assembly, taxonomic sequence classification, and classified sequence extraction. While the pipeline described herein has not been integrated into a single software package, each step has been carefully curated and executed using established bioinformatic tools. 

This pipeline requires the following tools: 
1. Metagenome assembly: [MEGAHIT](https://github.com/voutcn/megahit) (Tested with version 1.2.9), [SPAdes](https://github.com/ablab/spades) (Tested with version 3.15.4), or [Ray](https://github.com/sebhtml/ray) (Tested with version 2.3.1) for Illumina short reads; [Flye](https://github.com/fenderglass/Flye) (Tested with version 2.9.2) for Oxford Nanopore long reads.
2. Taxonomic sequence classification: [Kraken 2](https://github.com/DerrickWood/kraken2) (Tested with version 2.1.3 and the standard database created in 09/2019).
3. Classified sequence extraction: [KrakenTools](https://github.com/jenniferlu717/KrakenTools) (Tested with version 1.2).

# Usage

<p align="center">
<img width="800" height="424.7427"src="https://github.com/jackchen129/MAGenie/assets/49889016/410d5ad4-2ea6-4f6b-b622-c0fafb526abe">
</p>

1. Metagenome assembly: MEGAHIT, SPAdes (`metaspades.py`), or Ray and Flye (`--meta`) will be used to assemble Illumina short reads and Oxford Nanopore long reads, respectively, into contiguous sequences (contigs). The assemblers were previously benchmarked and selected based on their performance in generating high-quality assemblies for downstream genomic analyses.
2. Taxonomic sequence classification: Following metagenome assembly, taxonomic classification of the assembled contigs will be performed using Kraken 2. This step involves assigning taxonomic labels to individual sequences based on their similarity to reference sequences in a predefined database.
3. Classified sequence extraction: Subsequently, sequences corresponding to specific taxonomic groups of interest will be extracted from the assembled contigs. This extraction process is conducted using the sequence extraction module of KrakenTools (`extract_kraken_reads.py`). The extracted sequences are compiled to generate draft MAGs representing the targeted taxonomic groups. This extraction encompasses reads classified at both parent (`--include-parents`) and child (`--include-children`) taxonomic levels.

The draft MAGs serve as valuable resources for downstream genomic analyses, such as identifications of mobile genetic elements (plasmids, prophages, etc.) and genes (antimicrobial resistance genes, virulence genes, etc.), serotyping, multilocus sequence typing, and phylogenetic inference.

# Citations
If you find MAGenie useful, please cite: 

>[Chen, Z., & Meng, J. (2022). Critical assessment of short-read assemblers for the metagenomic identification of foodborne and waterborne pathogens using simulated bacterial communities. Microorganisms, 10(12), 2416.](https://www.mdpi.com/2076-2607/10/12/2416)
>Chen, Z., Grim, C.J., Ramachandran, P., & Meng, J. (2024). Advancing metagenome-assembled genome-based pathogen identification: Unraveling the power of long-read assembly algorithms in Oxford Nanopore sequencing. Microbiology Spectrum. In press.

You may also consider citing the following (tools used by MAGenie): 

>MEGAHIT: 
>[Li, D., Liu, C. M., Luo, R., Sadakane, K., & Lam, T. W. (2015). MEGAHIT: an ultra-fast single-node solution for large and complex metagenomics assembly via succinct de Bruijn graph. Bioinformatics, 31(10), 1674-1676.](https://academic.oup.com/bioinformatics/article/31/10/1674/177884)
>
>SPAdes: 
>[Nurk, S., Meleshko, D., Korobeynikov, A., & Pevzner, P. A. (2017). metaSPAdes: a new versatile metagenomic assembler. Genome Research, 27(5), 824-834.](https://genome.cshlp.org/content/27/5/824)
>
>Ray: 
>[Boisvert, S., Raymond, F., Godzaridis, É., Laviolette, F., & Corbeil, J. (2012). Ray Meta: scalable *de* *novo* metagenome assembly and profiling. Genome Biology, 13, 1-13.](https://link.springer.com/article/10.1186/gb-2012-13-12-r122)
>
>Flye: 
>[Kolmogorov, M., Bickhart, D. M., Behsaz, B., Gurevich, A., Rayko, M., Shin, S. B., ... & Pevzner, P. A. (2020). metaFlye: scalable long-read metagenome assembly using repeat graphs. Nature Methods, 17(11), 1103-1110.](https://www.nature.com/articles/s41592-020-00971-x)
>
>Kraken 2: 
>[Wood, D. E., Lu, J., & Langmead, B. (2019). Improved metagenomic analysis with Kraken 2. Genome Biology, 20, 1-13.](https://link.springer.com/article/10.1186/s13059-019-1891-0)
>
>KrakenTools: 
>[Lu, J., Rincon, N., Wood, D. E., Breitwieser, F. P., Pockrandt, C., Langmead, B., ... & Steinegger, M. (2022). Metagenome analysis using the Kraken software suite. Nature Protocols, 17(12), 2815-2839.](https://www.nature.com/articles/s41596-022-00738-y)

