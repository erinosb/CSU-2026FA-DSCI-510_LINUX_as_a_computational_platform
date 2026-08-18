# Wildcards

So far, we have always typed out the exact argument names. We do this by hand-typing or using `tab` to auto-complete the name of a file or directory. This performs operations on **specific** files or directories. We can also use **wildcards** to ask the shell to perform operations on groups of filenames or directories. Wildcards are special characters that will match a set of characters. This can extend the command by performing the action on more than one file at a time.

`*` this can represent any number of characters (including zero, in other words, zero or more characters)

`?` this can represent any single character

**References**
- Please Refer to Chapter 4 in the textbook, The Linux Command Line, for a detailed discussion on wildcards. Today, we will just cover two types of wildcards, `*` and `?`.
- [GNU/LINUX Wildcard Command Line Tools](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm)

**!!! Examples**:
```
b*b
  will match bob, blob, bathtub, beach_club
  will sometimes match bb
  will NOT match bobbing, robob
  
*.jpg \\
  will match file1.jpg, file2.jpg, examplepicture1.jpg, 12347689.jpg
  will sometimes match .jpg
  will NOT match file1.JPG, jpg, microscope_images.jpg.tgz
  
directory/*
  will match all files in the directory

b?b
  will match bib, bab, bob, bub
  will NOT match bb, BOB, blob, bathtub, beach_club, bobbing, robob
```

**!!! Exercise**: What will the following commands do? 
```
$ head -n 1 *.txt
$ tail d*
$ wc ???_chrom_sizes.txt
```

**!!! Independent Exercise**: How would you use a wildcard to display the word count of all the chrom_sizes files while excluding the word count of the readme file?

Continue on to [Getting Help](1-8_Getting_help.md)
