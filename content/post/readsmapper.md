+++
date = "2019-03-04"
description = "Python cheat sheet for biology"
draft = false
tags = ["bioinformatics"]
title = "Extracting mapped and unmapped reads from fastq file"
topics = ["Bioinformatics"]
+++


Recently, I had a problem where only a certain fraction of reads are mapping to the reference genome. The next step was figuring out how to separate reads that map to the reference genome and reads that are not. I am going to detail below how I have done this as a reference to the future me and also for anyone who wants to do this.

* The first step is to map the reads (fastq format) against a reference genome (sequence) using an aligner (eg. BWA-MEM, Bowtie2, STAR, minimap2).
* Following this, we have a **sam or bam** file and this can be done with either of these files.
* sam file has read ids in the first column and mapped/unmapped status in the 4th column - usually '0' for unmapped reads and a non-zero for mapped reads.
* Information in the 4th column is used to separate mapped and unmapped reads into two separate sam files. Then, read ids in the first column can be used to extract specific reads in the fastq file using software tool called "seqtk".
* **sam file:** 

```console
samtools view -S -F4 sample.sam > sample.mapped.sam
samtools view -S -f4 sample.sam > sample.unmapped.sam
```
Here, **'F4'** and **'f4'** looks for a non-zero and zero in the 4th column respectively followed by printing out those rows to new sam files.

* Next step is to extract the read ids from these sam files into separate lists that **seqtk** uses. For this, we can use **cut** option.

```console
cut -f1 sample.mapped.sam | sort | uniq > mapped_ids.lst
cut -f1 sample.unmapped.sam | sort | uniq > unmapped_ids.lst
```
This will cut the read ids (which are in the first column), sorts them and **uniq** extracts only unique read ids into two separate lists. **uniq** is essential since sam files will have secondary alignments depending on the alignment software used and these lines will have the same read ids. 

* Finally, we use these lists to extract mapped and unmapped reads into separate fastq files from the original fastq file (which was used to map against reference) with **seqtk subseq** option.

```console
seqtk subseq original.fastq mapped_ids.lst > mapped.fastq
seqtk subseq original.fastq unmapped_ids.lst > unmapped.fastq
```

* **mapped.fastq** and **unmapped.fastq** represents reads that mapped and reads which did not map to reference genome respectively. These can be used for any further analysis. For example, sequences in **unmapped.fastq** can be blasted to find more information about these reads.
* Another thing to remember here is how to convert the **fastq** file to **fasta (.fa)** format so that it can be used on the blast website. This can again be done using the **seqtk** software tool by using the code below.

```console
seqtk seq -a unmapped.fastq > unmapped.fa
```
