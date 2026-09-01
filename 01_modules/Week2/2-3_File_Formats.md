<p align="center">
<img width="100%" alt="icons" src="../../05_images/headers_Slide5.png">
</p>

# File Formats

Let's learn about **file formats**. Different file formats are typically identified by specific **file extensions**, suffixes to their names that inform programs of their type. Two general types of file formats are:

- **text files** (also called **flat** files) are files that have only text information.
- **binary files** files that have more complex information that can be interpreted as formatting, images, application-specific objects, as well as text. Examples: .docx, .xlsx, .jpg, .pdf, and .m4p

### How do we know if a file is a text file?

- It has the file extension like .txt, .csv, .fa, .gb
- You can use `more` or `less` to read through it
- You can use a **text editor** to view and edit it

### How do we know if a file is a binary file?

- It has a specific file extension associated with a specific program
- It was produced in a specific program (Microsoft Word, for example)
- If you use `more` or `less`, it looks like a bunch of alien writing

>[!TIP]
> If you cannot see file extensions on your computer, take a moment to make these visible.

  - [Mac: Making file extensions visible](https://www.idownloadblog.com/2023/05/23/how-to-show-hide-filename-extensions-mac/)
  - [PC: Making file extensions visible](https://www.howtogeek.com/205086/beginner-how-to-make-windows-show-file-extensions/)

### Where do file extensions come from?

  - For flat, text files, you put them there!

>[!TIP]
> It is good practice to **always save files with the proper file extensions!** All files should have extensions!

>[!NOTE]
> Some standardized file formats will have lines at the beginning that start with `#`. These are comments. They typically contain information about how the information was generated.

---

## Text Editor 

Everyone will need to install a [text editor](https://en.wikipedia.org/wiki/Text_editor) for writing and modifying plain text files.

- **Mac:**
  - I recommend [BBEdit](https://www.barebones.com/products/) OR [cotEditor](https://coteditor.com/)
    - You dont need to buy these. The free versions are enough.
    - **Warning:** Do not use MAC's application called **TextEdit**. It is a rich text format editor and not a flat text editor.

- **Windows 11:**
  - Recommend [Notepad++](https://notepad-plus-plus.org/)

- **Mac or PC: IDEs**
  - [Visual Studio Code](https://code.visualstudio.com/download) - this is a more feature-intensive Integraded Development Environment (IDE). It includes a text editor, a terminal, and a window for navigating files

>[!NOTE]
> If you already have a text editor you like that is not listed, you are free to use it provided it saves files in true flat .txt and not rich text format.

---

## Standard file types in the life sciences

Several standardized types of text files have been developed to handle biological data and genome data. You may already be familiar with some [Common Examples of Biological File Types](https://en.wikipedia.org/wiki/List_of_file_formats#Biology). In dealing with genomic information, almost all the files are **text files**.

Genome information is typically stored in **FASTA** files and **Annotation files** (**GTF/GFF3** files). The combination of these two file types gives you the entire genome sequence (fasta) and the location of all genes and other features in the genome (annotation file).

  - More information about [FASTA FILES HERE](../../04_resources/FASTA_Files.md). 
    - This contains the entire genome sequence.
  - More information about [ANNOTATION FILES HERE](../../04_resources/Annotation_Files.md)
    - This file contains information and the location of all gene and other features of the genome.

**Where do we obtain these files?** There are many places where we can download genomic data, but the main resources for Genomic Datasets are the following repositories:

- [UCSC Genome Browser](https://genome.ucsc.edu/index.html)
- [Ensembl](https://www.ensembl.org/index.html)
- [NCBI](https://www.ncbi.nlm.nih.gov/guide/howto/dwn-genome/)
- Organism specific community resources like [Wormbase](https://www.wormbase.org) or [TAIR](https://www.arabidopsis.org/)

----

## What are the predominant file types in your field?

  - If you are in a different field, what are the main types of data or information you encounter? 
  - What types of files are they stored in?
  - Are they text/flat files? 
  - What are the repositories in which they are stored?

----

## Obtain the yeast genome and annotation

:hammer_and_wrench: **Group Exercise**

Download the tarball `covid.tgz`

  - Let's download the covid genome information together
  - Navigate to [03_data](../../03_data)
  - Click on `covid.tgz`
  - Click on the word **Raw** on the far right side of the window
  - Select a directory in which to save the files

Extract the file

  - **Mac** -> double click the file `covid.tgz` in the Finder
  - **PC** -> In the terminal, navigate to the file `covid.tgz` and unzip with tar:

```
$ tar -zxvf covid.tgz
```

**Mac** and **PC**

  - In the terminal, navigate into the expanded directory and examine the files obtained using `ls`, `more`, and `wc`

----

## Ensuring files were not corrupted using `md5sum`

To ensure your files were not corrupted during transit, I have included **md5sum checksums** for each file that are located in a file called `md5sum.txt`. **Checksums** are digital codes associated with a file that are calculated out of information within the file. If the integrity of the file is intact, the md5sum checksum program will match digital code in those text files.

**!!! Group Exercise:** Check sums

  - Within the directory `Covid`, read the file `md5sums.txt`

```
$ more md5sums.txt
```
  
  - Now, calculate your own md5 sums of the included files:

```
$ md5 covid*
```

**Didn't work?** Try `md5sum covid*` or `md5sum-lite covid*` instead. Different distributions will have different utilities.

  - Do the digital codes match? Let's check. Here is a little script that I called `CompareSums.sh` to check the contents ...

Continue on to [Redirection](2-5_Redirection.md)
