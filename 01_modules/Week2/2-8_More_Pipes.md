# More Pipes

Now that we know what piping is, we can discover some new functionalities of Linux. Let's learn how to pipe the following commands:

`sort` - sort lines in a file

`uniq` - find unique (or duplicated) lines in a pre-sorted file

`tee` - redirect stdout or stderr to multiple locations

**!!! Exercise:** Let's download a small file [mini.gff](https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Data/mini.gff).

- To download, right-click and open in a new tab
- click on the down arrow to download
- save to an appropriate place
- sync your working directory (in the terminal) with the directory containing mini.gff

### Sorting files by line using `sort`

We can use sort to sort a file's lines into a new order …

**sort usage:**

`sort [options] <file.txt> …`

**!!! Exercise:** Sort the mini.gff file:

```
$ sort mini.gff
```

**!!! Exercise:** Read the sort man pages to figure out how you would …

- sort in reverse order
- sort the capital and lower case letters together
- sort in numerical order.
- Try some of these options

### Reduce down to unique lines using `sort` or `uniq`

We can remove duplicated lines in a variety of ways.

First, we can use the sort option `-u` like so:

**sort usage:**

`sort -u <file.txt>`

This has the effect of suppressing lines that are identical to previously printed lines.

Another way to do this is using the command `uniq`

**uniq usage:**

`uniq [options] <sortedFile.txt>`

To operate on a presorted file, we have two options. We can do the process in two steps:

```
$ sort file.txt > sortedFile.txt #step1
$ uniq sortedFile.txt #step2
```

OR, we can use the pipe operator to chain the two commands together:

```
$ sort mini.gff | uniq
```

That wasn't very interesting. What if we do this just for the first column and it gives us a chance to really demonstrate the power of pipes …

```
$ cut -f 1 mini.gff
$ cut -f 1 mini.gff | sort
$ cut -f 1 mini.gff | sort -u 
$ cut -f 1 mini.gff | sort | uniq
```

**!!! Quick tip:** To find the duplicated lines, use `-d` as an option for **uniq**.

```
$ cut -f 1 mini.gff | sort | uniq -d
```

**!!! Common pitfall:** Pipes are fun, but pipes can be problematic with large files. Depending on your computer or cluster, there may be a limit to how much information can be piped to a new command. In these cases, creating a temp file (sometimes written as file.tmp) is preferable.

---

Clarifying content on the `sort` and `uniq` commands:

Example of **removal**
```
$ cat file.txt
banana
apple
banana
apple

$ sort file.txt
apple
apple
banana
banana

$ sort -u file.txt
apple
banana
```

Example of **not removed**
```
$ cat file.txt
banana
apple
banana
apple

$ uniq file.txt
banana
apple
banana
apple   # duplicates are not adjacent, so they stay!
```

regarding the in-class example using the mini.gff file, the problem was the lines were not actually identical even though they did look pretty similar. I had to re-space all of the lines (so something was off with the tab spacing)

**origional file** that `sort -u` and `uniq` DONT work on ... (it is the last 2 lines that were duplicated!)
```
# A tester gff file.                                
# For testing pipes.                                
chrV	sacCer3_ensGene	CDS	574807	575379	0.000000	-	0	gene_id "YER190C-A"; transcript_id "YER190C-A";
chrII	sacCer3_ensGene	CDS	805038	805256	0.000000	-	0	gene_id "YBR298C-A"; transcript_id "YBR298C-A";
chrV	sacCer3_ensGene	start_codon	575377	575379	0.000000	-	.	gene_id "YER190C-A"; transcript_id "YER190C-A";
chrII	sacCer3_ensGene	start_codon	805254	805256	0.000000	-	.	gene_id "YBR298C-A"; transcript_id "YBR298C-A";
chrII	sacCer3_ensGene	exon	805035	805256	0.000000	-	.	gene_id "YBR298C-A"; transcript_id "YBR298C-A";
chrIII	sacCer3_ensGene	exon	309070	310155	0.000000	+	.	gene_id "YCR105W"; transcript_id "YCR105W";
CHRII	sacCer3_ensGene	start_codon	805351	805353	0.000000	+	.	gene_id "YBR299W"; transcript_id "YBR299W";
CHRIII	sacCer3_ensGene	start_codon	310958	310960	0.000000	+	.	gene_id "YCR106W"; transcript_id "YCR106W";
chrV	sacCer3_ensGene	exon	574804	575379	0.000000	-	.	gene_id "YER190C-A"; transcript_id "YER190C-A";
chrV	sacCer3_ensGene	stop_codon	575680	575682	0.000000	-	.	gene_id "YER190C-B"; transcript_id "YER190C-B";
chrV    sacCer3_ensGene stop_codon      575680  575682  0.000000        -       .       gene_id "YER190C-B"; transcript_id "YER190C-B";
```

**corrected file** that `sort -u` and `uniq` DO work on ... (it is the last 2 lines that were duplicated!)
```
# A tester gff file.                                
# For testing pipes.                                
chrV sacCer3_ensGene    CDS 574807  575379  0.000000    -   0   gene_id "YER190C-A"; transcript_id "YER190C-A";
chrII sacCer3_ensGene   CDS 805038  805256  0.000000    -   0   gene_id "YBR298C-A"; transcript_id "YBR298C-A";
chrV sacCer3_ensGene    start_codon 575377  575379  0.000000    -   .   gene_id "YER190C-A"; transcript_id "YER190C-A";
chrII acCer3_ensGene    start_codon 805254  805256  0.000000    -   .   gene_id "YBR298C-A"; transcript_id "YBR298C-A";
chrII   sacCer3_ensGene exon    805035  805256  0.000000    -   .   gene_id "YBR298C-A"; transcript_id "YBR298C-A";
chrIII  sacCer3_ensGene exon    309070  310155  0.000000    +   .   gene_id "YCR105W"; transcript_id "YCR105W";
CHRII   sacCer3_ensGene start_codon 805351  805353  0.000000    +   .   gene_id "YBR299W"; transcript_id "YBR299W";
CHRIII  sacCer3_ensGene start_codon 310958  310960  0.000000    +   .   gene_id "YCR106W"; transcript_id "YCR106W";
chrV    sacCer3_ensGene exon    574804  575379  0.000000    -   .   gene_id "YER190C-A"; transcript_id "YER190C-A";
chrV sacCer3_ensGene stop_codon 575680 575682 0.000000 - . gene_id "YER190C-B"; transcript_id "YER190C-B";
chrV sacCer3_ensGene stop_codon 575680 575682 0.000000 - . gene_id "YER190C-B"; transcript_id "YER190C-B";
```

---

### Redirect to multiple locations using `tee`

In an earlier lesson, we learned how to redirect STDOUT and STERR to a file. If we want to direct STDOUT to both a file and the screen, we can use the `tee` command. `tee` is used with the pipe command.

**tee usage:**

`command | tee <filename.txt>`

**!!! Exercise:** Try to send output from a command to both the screen and a file.

```
$ wc mini.gff | tee wc_output.txt
```

**!!! Quick Tip:** `tee` is really used for redirecting stdout. You can redirect both stderr & stdout, but it is a little cumbersome:

```
$ wc mini.gff skdjfldj 2>&1 | tee wc_stdoutstderr.txt
```

### Piping multiple `cut` commands

One thing that we end up doing a lot is piping together multiple cut and grep commands. This is very useful because it allows us to extract **rows** of information using `grep` and **columns** of information using `cut`. We can extract the exact information we want out of a large file.

**!!! Exercise:** Piping together of `cut` commands.

Download the annotation file that lists all the features in the [SARS-CoV-2 genome](https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Data/SARSCoV2_ncbiGenes.gtf). To do so, click over to google drive and then download the file.

- Sync things up so you can interact with this file using the command line. That is, move the file to a directory that you can access using the terminal. OR, within the terminal, navigate to the directory where this file lives.

Use a `cut` command to extract the 9th row of information from this .gtf file like so:

```
$ cut -f 9 SARSCoV2_ncbiGenes.gtf 
```

This column of information contains the annotation information associated with each entry.

How would you extract out just the gene ids?

```
#HINT:
$ cut -f 9 SARSCoV2_ncbiGenes.gtf | cut <put some additional code here>
```

Answer? 

### Where do the arguments go in piped commands?

This is typically where students start to get confused about where the arguments need to go when using pipes.

If you are working with files, the file will be the argument of the **first** command. This is because the argument of the second command is actually equivalent to the **output** of the first command.

`$ command [options] <argument.txt> | command [options] | command [options]`

So it will look like …

```
$ grep 'allgenes' myfile.gtf | wc
```

Here, the argument for the `grep` command is <myfile.gtf>. The argument for the `wc` command is the output of the `grep` command.

### Pairwork - Challenge Exercise

**!!! Exercise:** Can you write a series of pipes that will list the unique genes in the SARS-CoV2 genome?

**Hint** … the final product should look like this …

```
"E"
"M"
"N"
"ORF10"
"ORF1a"
"ORF1ab"
"ORF3a"
"ORF6"
"ORF7a"
"ORF7b"
"ORF8"
"S"
```

What were some of your answers? 

Continue on to [Working with files 3](../Week3/3-2_Working_with_files3.md)
