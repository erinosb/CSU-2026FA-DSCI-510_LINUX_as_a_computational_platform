
# Independent practice using `grep` and `cut`

- Download the annotation file that lists all the features in the . To do so, click over to google drive and then download the file.
- Sync things up so you can interact with this file using the command line. That is, move the file to a directory that you can access using the terminal. OR, within the terminal, navigate to the directory where this file lives.

### `grep` practice

Recall the `grep` usage:

**grep usage**

`grep [options] <pattern> <file> …`

- there are many options for `grep`
- Typically, the pattern given to search is enclosed in quotes.
- `grep` can search multiple files

:hammerandwrench: **Exercise 1:**

- Coding sequences are marked as `CDS` in the .gtf file. Can you print their lines out to the screen using grep? Can you capture all those lines in a file using grep and `>`?
Start codons are called `start_codon` in the .gtf file. Can you print their lines out to the screen using grep? Can you capture all those lines in a file using grep and `>`?
Compare how many lines are in the original annotation file, the coding sequence file, and the strat codon file. 

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

:hammerandwrench: **Exercise 2:**

- What is in each column of your annotation file? Use cut to print out individual columns of information to the screen.
  - Notice how columns have the same information in each row. Others have unique information.
- To look it up, reference here: [ALL ABOUT ANNOTATION FILES](../../04_resources/Annotation_Files.md)
- Can you redirect only the 9th column from this file into an output file called `featureDetails.txt`?

Continue on to [Pipes](2-8_Pipes.md)
