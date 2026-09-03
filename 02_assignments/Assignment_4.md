# Assignment 4

- Due **Tuesday, September 8, 2026, 10:00 am** 
- **DO NOT write out the questions. Do not write long descriptions. Only write your succinct answers.**
- Enter your answers into a .txt file within a text editor such as BBEdit, Notepad++, or some other application. Do not use Word. Do not use TextEdit (MAC).
- Do not include the questions in your answer file.
- **Turn in your answers as the .txt file on Canvas by uploading your file.**
- Assignments account for 30 % of your final grade. 

---

**!!! Hint**: For answers involving command line entries, write out the full command line entry as you would write it on the command line including all command words + options + arguments.

---

## Question 1 

For this assignment, use the yeast genome information you downloaded from [03_data](../03_data) called `SacCer_R64.tgz`. *Hint: Click on SacCer_R64.tgz and then click on **Raw** to download*

A. What command line entry would you use to print out all the comment lines in the file `yeast_annotation.gff` to the screen?

B. What command line entry would you use to SAVE all the comment lines in the file `yeast_annotation.gff` into a new file called `annotation_comments.txt`?

-----

## Question 2

A. How many gene entries are listed in the `yeast_annotation.gff`?

B. What command line entry (or entries) did you use to attain that number?

-----

## Question 3

Your co-worker has been interested in learning more about the antisense RNAs of yeast. 

She has written four lines of code (below) to extract the names of the anti-sense RNAs from the file `yeast_annotation.gff`. In the process, she creates three "temp" or temporary files and the final output file called `antisense_names.txt`. 

Show her how to combine the four lines of codes into a single command line entry (using pipes). This would effectively eliminate the need to create temp files. In the end, she will simply create one file called `antisense_names.txt`

```
grep -v "#" yeast_annotation.gff > yeast_annotation_WOcomments.gff
grep "\tantisense_RNA\t" yeast_annotation_WOcomments.gff > antisense.gff
cut -f 9 antisense.gff > antisense_info.txt
cut -d ";" -f 2 antisense_info.txt > antisense_names.txt 
```

A. Write the command line entry you suggest for her to use instead.

-----

## Question 4

A `bed` file is a standard file used in genomics that contains the following tabular information.

`Chromosome_Name <tab> Start_bp_# <tab> Stop_bp_# <tab> strand`

The .bed for the yeast antisense_RNAs will contain the following information:

```
NC_001134.8	276805	280645	+
NC_001134.8	376610	378633	+
NC_001139.9	33109	35013	-
NC_001139.9	141898	144120	-
NC_001140.6	378254	379237	+
NC_001145.3	23564	26578	+
NC_001148.4	79562	82648	+
```

What single command line entry would you use to create this bed file? 

*Hints*

  - Use pipes
  - Use ">"
  - name the created file `antisense.bed`

-----

## Question 5 

Let's switch to the file `yeast_sequence.fna`. 

What command line entry would you use to extract all the "header" lines into a new file called `yeast_headers.txt`.

*hint: header lines start with >*

-----

## Bonus Challenge Question (no points, just for fun)

There are 6459 genes in the yeast genome. Can you find a way to extract this number from the file `yeast_annotation.gff`?

What command line entry (or entries) did you use?