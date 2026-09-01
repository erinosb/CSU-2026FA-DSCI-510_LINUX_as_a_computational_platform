
# Independent practice using `grep` and `cut`

*These exercises use the [covid genome sequence and annotation files](../../03_data/covid.tgz)*

  - Ensure you have downloaded the covid genome and sequence files.
  - Sync things up so you can interact with this file using the command line. That is, move the file to a directory that you can access using the terminal. OR, within the terminal, navigate to the directory where this file lives.

---

## `grep` practice

Recall the `grep` usage:

**grep usage**

`grep [options] <pattern> <file> …`

- there are many options for `grep`
- Typically, the pattern given to search is enclosed in quotes.
- `grep` can search multiple files

:hammerandwrench: **Exercise 1:**

  - Coding sequences are marked as `CDS` in the .gff file. 
  - Can you print all the CDS lines out to the screen using grep? 
  - Can you capture the same lines into a file using `>`?
  - *Note*: How would you exclude capturing "mature_protein_region_of_CDS" and only capture "CDS" entries?

:hammerandwrench: **Exercise 2:**

  - How many stem loops are listed in covid_annotation.gff?

----

## `cut` practice

Recall the `cut` command:

**cut usage:**

`cut [options] -f #… <file.txt> …`

- This is the default usage and it splits on tabs
- You can capture a single column such as column one using `-f 1` or a series of columns using `-f 1,2,3`

**cut usage with other delimiters:**

`cut -d <newdelimiter> -f # <file.txt> …`

This will allow you to split on other delimiters like spaces (' ') or commas (,).

:hammerandwrench: **Exercise 3**

  - Notice how columns have the same information in each row. Others have unique information.
- To look it up, reference here: [ALL ABOUT ANNOTATION FILES](../../04_resources/Annotation_Files.md)
- Can you redirect only the 9th column of `covid_annotation.gff` into an output file called `featureDetails.txt`?

Continue on to [Pipes](2-8_Pipes.md)
