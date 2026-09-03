<p align="center">
<img width="100%" alt="icons" src="../../05_images/headers_pipes.jpg">
</p>

# More Pipes

Now that we know what piping is, we can discover some new functionalities of Linux. Let's learn how to pipe the following commands:

`sort` - sort lines in a file

`uniq` - find unique (or duplicated) lines in a pre-sorted file

`tee` - redirect stdout or stderr to multiple locations

----

:hammer_and_wrench: **Group Exercise:** Let's make a file called mini.gff.

  * Copy and paste the following content into a file called `mini.giff` using nano or your text editor.


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

## Sorting files by line using `sort`

We can use sort to sort a file's lines into a new order …

**sort usage:**

`sort [options] <file.txt> …`

:hammer_and_wrench: **Group Exercise:** Sort the mini.gff file:

```
$ sort mini.gff
```

:hammer_and_wrench: **Independent Exercise:** Read the `sort` man pages to figure out how you would …

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

[!TIP]
> ]To find the duplicated lines, use `-d` as an option for **uniq**.

```
$ cut -f 1 mini.gff | sort | uniq -d
```

>[!WARNING]
> Pipes are fun, but pipes can be problematic with large files. Depending on your computer or cluster, there may be a limit to how much information can be piped to a new command. In these cases, creating a temp file (sometimes written as file.tmp) is preferable.

---

### When is something considered unique?

For the `uniq` command to remove duplicate entries, those entries must be adjacent. That is why `sort` and `uniq` are used in combination.

Example of **removal**

```
# Example of duplicates that are NOT removed

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

# Examples of proper removal...

$ sort file.txt | uniq
apple
banana

$ sort -u file.txt
apple
banana
```


---

## Redirect to multiple locations using `tee`

In an earlier lesson, we learned how to redirect STDOUT and STERR to a file. If we want to direct STDOUT to both a file and the screen, we can use the `tee` command. `tee` is used with the pipe command.

**tee usage:**

`command | tee <filename.txt>`

:hammer_and_wrench: **Group Exercise:** Try to send output from a command to both the screen and a file.

```
$ wc mini.gff | tee wc_output.txt
```

>[!TIP]
> `tee` is used for redirecting stdout. You can redirect both stderr & stdout, but it is a little cumbersome:

```
$ wc mini.gff skdjfldj 2>&1 | tee wc_stdoutstderr.txt
```

---

## Piping multiple `cut` commands

One thing that we end up doing a lot is piping together multiple cut and grep commands. This is very useful because it allows us to extract **rows** of information using `grep` and **columns** of information using `cut`. We can extract the exact information we want out of a large file.

:hammer_and_wrench: **Group Exercise:** Piping together of `cut` commands.

Switch over to the Covid genome information you downloaded in a previous exercise...

```
$ pwd
~/genomes/Covid
$ ls -1
covid_annotation.gff
covid_sequence.fna
ErinsNotes.txt
md5sum.txt
README.md
```

We are going to use the file `covid_annotation.gff`

- Sync things up so you can interact with this file using the command line. That is, move the file to a directory that you can access using the terminal. OR, within the terminal, navigate to the directory where this file lives.

Use a `cut` command to extract the 9th row of information from this .gtf file like so:

```
$ cut -f 9 covid_annotation.gff
```

This column of information contains the annotation information associated with each entry.

How would you extract out just the gene ids?

:wink: **Hint** The output will look like this...

```
##gff-version 3
#!gff-spec-version 1.21
#!processor NCBI annotwriter
#!genome-build ASM985889v3
#!genome-build-accession NCBI_Assembly:GCF_009858895.2
##sequence-region NC_045512.2 1 29903
##species https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=2697049
ID=NC_045512.2:1..29903
ID=id-NC_045512.2:1..265
ID=gene-GU280_gp01
ID=cds-YP_009724389.1
ID=cds-YP_009724389.1
ID=id-YP_009724389.1:1..180
ID=id-YP_009724389.1:181..818
ID=id-YP_009724389.1:819..2763
ID=id-YP_009724389.1:2764..3263
ID=id-YP_009724389.1:3264..3569
ID=id-YP_009724389.1:3570..3859
ID=id-YP_009724389.1:3860..3942
ID=id-YP_009724389.1:3943..4140
ID=id-YP_009724389.1:4141..4253
ID=id-YP_009724389.1:4254..4392
ID=id-YP_009724389.1:4393..5324
ID=id-YP_009724389.1:4393..5324
ID=id-YP_009724389.1:5325..5925
ID=id-YP_009724389.1:5926..6452
ID=id-YP_009724389.1:6453..6798
ID=id-YP_009724389.1:6799..7096
ID=cds-YP_009725295.1
ID=id-YP_009725295.1:1..180
ID=id-YP_009725295.1:181..818
ID=id-YP_009725295.1:819..2763
ID=id-YP_009725295.1:2764..3263
ID=id-YP_009725295.1:3264..3569
ID=id-YP_009725295.1:3570..3859
ID=id-YP_009725295.1:3860..3942
ID=id-YP_009725295.1:3943..4140
ID=id-YP_009725295.1:4141..4253
ID=id-YP_009725295.1:4254..4392
ID=id-YP_009725295.1:4393..4405
ID=id-GU280_gp01
ID=id-GU280_gp01-2
ID=gene-GU280_gp02
ID=cds-YP_009724390.1
ID=gene-GU280_gp03
ID=cds-YP_009724391.1
ID=gene-GU280_gp04
ID=cds-YP_009724392.1
ID=gene-GU280_gp05
ID=cds-YP_009724393.1
ID=gene-GU280_gp06
ID=cds-YP_009724394.1
ID=gene-GU280_gp07
ID=cds-YP_009724395.1
ID=gene-GU280_gp08
ID=cds-YP_009725318.1
ID=gene-GU280_gp09
ID=cds-YP_009724396.1
ID=gene-GU280_gp10
ID=cds-YP_009724397.2
ID=gene-GU280_gp11
ID=cds-YP_009725255.1
ID=id-GU280_gp11
ID=id-GU280_gp11-2
ID=id-NC_045512.2:29675..29903
ID=id-NC_045512.2:29728..29768
###
```

:wink: **Hint**

```
$ cut -f 9 SARSCoV2_ncbiGenes.gtf | cut <put some additional code here>
```

---

### Where do the arguments go in piped commands?

This is typically where students start to get confused about where the arguments need to go when using pipes.

If you are working with files, the file will be the argument of the **first** command. This is because the argument of the second command is actually equivalent to the **output** of the first command.

`$ command [options] <argument.txt> | command [options] | command [options]`

So it will look like …

```
$ grep 'allgenes' myfile.gtf | wc
```

Here, the argument for the `grep` command is <myfile.gff>. The argument for the `wc` command is the output of the `grep` command.

---
## Pairwork - Challenge Exercise

:hammer_and_wrench:  **Partner Exercise:** Can you write a series of pipes that will list the unique genes in the SARS-CoV2 genome?

:wink: **Hint** The final product should look like this ...

```
ORF1ab
S
ORF3a
E
M
ORF6
ORF7a
ORF7b
ORF8
N
ORF10
```

What were some of your answers? 

Continue on to [Working with files 3](../Week3/3-2_Working_with_files3.md)
