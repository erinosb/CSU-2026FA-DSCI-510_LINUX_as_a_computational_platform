# Assignment 2

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

What is your field of study? What type of flat/text files are used in your field of study?

Describe these files and be sure to include 1) the type of information they contain, 2) the file extension, 3) a brief description of how the data is organized

*Hint: If you don't have a field of study, please explore a file type listed on this [Wikipedia Page of Scientific Data types](https://en.wikipedia.org/wiki/List_of_file_formats)*

## Question 2 

Using the skills you have learned, download the [yeast sequence and annotation here](../03_data/SacCer_R64.tgz). Download the file `SacCer_R64.tgz`

  - Expand the tarball
  - Do the md5 checksums match?
  - Write down the md5 checksums of all the yeast* files listed. Write down if these match the md5 checksums included in the tarball.

## Question 3

Let's clean up this folder. 

A. What command line entry would you write to create the directories `notes` and `genome` in a single command line entry?

B. What command line enbry would you write to move the two REAMDE files into the `notes` subdirectory in a single command line entry?

## Question 4

Assuming that the file `yeast_annotation.gff` exists and the file `blerg.jpg` does not, experiment with the following command line entries. 

Describe what is captured in each output file?

```
$ wc yeast_annotation.gff blerg.jpg > output1.txt
$ wc yeast_annotation.gff blerg.jpg 2> output2.txt
$ wc yeast_annotation.gff blerg.jpg &> output3.txt
```

## Question 5

A. Write out a command line entry that would help you create a backup of the yeast genome sequence.

B. Write out a command line entry that would rename the file `yeast_annotation.gff` to `Scerevisiae_annotation.gff`




