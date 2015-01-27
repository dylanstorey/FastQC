FastQC
=======
Quality control for data generated by Illumina Sequencing. 

Why?
=======
We needed a scalable local solution for generating quality control reports in the 100k Genomes Project.
We started with these measurements and visualizations and will likely add more later.

Installation/Dependencies:
==========================
The program will need to have a c++11 compatible compiler. To visualize the graphs you'll need R and ggplot2. 

Usage:
=======

`./HTseqQA <options> -i <fastq or gzip'd fastq> `

You can set the phred offset manually :

`./HTseqQA -o 64|33 -i test.fastq.gz`

The output is a text file with an extension of '.R' and run through R to get your graph out.

If you need to be running many files I suggest using parallel:

`parallel HTseqQA -i {} ::: /path/to/all/*.fastqs`

On a standard computer we're able to process 4000+ files over night. 

Cumulative Quality Scores
--------------------------
![Cumulative Quality Scores Graph](https://github.com/dylanstorey/HTseqQA/blob/master/documentation/C1ln3SF_NIcont_1.cqs.png)

Nucleotide Proportions
---------------------------
![Nucleotide Proportions](https://github.com/dylanstorey/HTseqQA/blob/master/documentation/C1ln3SF_NIcont_1.ntd.png)

Quality Distributions by Position
----------------------------------
![Quality Distributions by Position](https://github.com/dylanstorey/HTseqQA/blob/master/documentation/C1ln3SF_NIcont_1.qbp.png)

Passing Reads Filter
--------------------
![Passing Reads Filter](https://github.com/dylanstorey/HTseqQA/blob/master/documentation/C1ln3SF_NIcont_1.prf.png)


TODO:
======
- Add flag and code for producing YAML dumps of the files.
- Sequence representation proportions and graphs.
