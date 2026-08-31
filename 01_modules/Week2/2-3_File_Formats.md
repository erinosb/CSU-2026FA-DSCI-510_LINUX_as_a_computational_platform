# File Formats

Let's learn about **file formats**. Different file formats are typically identified by specific **file extensions**, suffixes to their names that inform programs of their type. Two general types of file formats are:

- **text files** (also called **flat** files) are files that have only text information.
- **binary files** files that have more complex information that can be interpreted as formatting, images, application-specific objects, as well as text. Examples: .docx, .xlsx, .jpg, .pdf, and .m4p

How do you we know something is a text file?

- It has the file extension like .txt, .csv, .fa, .gb
- You can use `more` or `less` to read through it
- You can use a **text editor** to view and edit it

How do we know something is a **binary file**?

- It has a specific file extension associated with a specific program
- It was produced in a specific program (Microsoft Word, for example)
- If you use `more` or `less`, it looks like a bunch of alien writing

**!!! Quick Tip:**

- If you cannot see file extensions on your computer, take a moment to make these visible.
- Where do file extensions come from? For flat, text files, you put them there!
- It is good practice to **always save files with the proper file extensions!** All files should have extensions!
- Some standardized file formats will have lines at the beginning that start with `#`. These are comments. They typically contain information about how the information was generated.

### Text Editor 

Everyone will need to install a [text editor](https://en.wikipedia.org/wiki/Text_editor) for writing and modifying plain text files.

- Mac:
  - Recommend [BBEdit](https://www.barebones.com/products/) or [Xcode](https://xcodereleases.com/). Click Download under the BBEdit software. You dont need to buy it. The free version does everthing you need.

**!!! Warning:** Do not use MAC's application called **TextEdit**. It is a rich text format editor and not a flat text editor.

- Windows 11:
  - Recommend [Notepad++](https://notepad-plus-plus.org/), BBEdit, or [Visual Studio Code](https://code.visualstudio.com/download) do not recommend TextEdit, Wordpad, Notebook, EMACS, or Microsoft Word.
  - If you already have a text editor you like that is not listed, you are free to use it provided it saves files in true flat .txt and not rich text format.

### Standard file types in the life sciences

Several standardized types of text files have been developed to handle biological data and genome data. You may already be familiar with some [Common Examples of Biological File Types](https://en.wikipedia.org/wiki/List_of_file_formats#Biology). In dealing with genomic information, almost all the files are **text files**.

Genome information is typically stored in **FASTA** files and **GTF/GFF** (aka **Annotation files**). The combination of these two file types gives you the entire genome sequence (fasta) and the location of all genes and other features in the genome (annotation file).

- More information about [FASTA FILES HERE](../../Resources/FASTA_Files.md)
- More information about [ANNOTATION FILES HERE](../../Resources/Annotation_Files.md) 

**Where can we obtain these files?** There are many places where we can download genomic data, but the main resources for Genomic Datasets are the following repositories:

- [UCSC Genome Browser](https://genome.ucsc.edu/index.html)
- [Ensembl](https://www.ensembl.org/index.html)
- [NCBI](https://www.ncbi.nlm.nih.gov/guide/howto/dwn-genome/)
- Organism specific community resources like [Wormbase](https://www.wormbase.org/#012-34-5) or [TAIR](https://www.arabidopsis.org/)

**!!! Question:** For your own research, what type of information do you need? What types of files is it stored in? If you are in a different field, what are the main data types you encounter? Are they stored in text/flat files? What are the repositories in which they are stored?

### Independent Exercise 

Try it for yourself!

For this next exercise, try to download two *Saccharomyces cerevisiae* annotation files (.gtf files) and the chrom.sizes file. The .gtf files can be found here:

[https://hgdownload.soe.ucsc.edu/goldenPath/sacCer3/bigZips/](https://hgdownload.soe.ucsc.edu/goldenPath/sacCer3/bigZips/)

They are located under the directory called genes

Your challenge:
1. Use rsync or wget to download the two .gtf.gz files.
2. Uncompress the .gtz.gz files
3. Compare the two versions of the annotation files.

Your challenge
1. download the file called sacCer3.chrom.sizes
2. Use rsync or wget to download sacCer3.chrom.sizes

Continue on to [Redirection](2-5_Redirection.md)
