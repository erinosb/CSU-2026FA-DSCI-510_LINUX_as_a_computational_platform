# Working With Files 1

### Peeking inside files with `more` and `less`

There are four main commands for printing file contents to the screen …

- `more` – scroll down through files
- `less` – scroll up or down through files
- `head` – show the top n lines. The default is n = 10
- `tail` – show the bottom n lines. The default is n = 10

**!!! Exercise**: 

- Navigate to your directory titled `chromsizes2`
- Try the following ways of peeking into files in that directory …

```
$ more ce11_chrom_sizes.txt # OR
$ more hs1_chrom_sizes.txt
```

Use **spacebar** or **down arrow** or **return** to scroll down

Type **q** to quit

```
$ less hs1_chrom_sizes.txt
```

Use **spacebar** or **down arrow** or **return** to scroll down

Use **b** or **up arrow** to scroll up

Type **q** to quit

```
$ head hs1_chrom_sizes.txt #show first 10 lines
$ head -n 5 hs1_chrom_sizes.txt #show first 5 lines
$ tail hs1_chrom_sizes.txt #show last 10 lines
$ tail -n 5 hs1_chrom_sizes.txt #show last 5 lines
```

**!!! Quick tip**: Sometimes it looks like head or tail are showing way more lines than you expect. If your lines are very, very long (typical in bioinformatics), this may be due to forced word wrapping in the terminal. Try re-sizing your browser bigger or smaller to see if this is the case.

**!!! Exercises**: 
- Navigate into the directory `chromsizes2`.
- Practice peeking into each file in the directory using each command.
- Try adding some options. 

### Getting file info 

One of the handiest commands for getting information about a file is word count.

`wc <file.txt> …`

Word count spits out:

1. number of **lines** in the file
2. number of **words** in the file
3. number of **characters/bytes** in the file
4. the file name
5. some totals if multiple files are given.

```
$ wc dm6_chrom_sizes.txt
$ wc *.txt # This will list the word count of ALL the .txt files
```

**!!! Cool trick**: We can also use options with **wc**:

```
$ wc -l    # lists only the number of lines
$ wc -w    # lists only the number of words
$ wc -c    # lists only the number of characters
```

### Multiple Arguments

To date, we have only performed a command on a single argument:

`$ command [argument]`

Most commands allow us to list multiple arguments and will perform the command on them in the order written:

`$ command [argument] <argument> <argument>`

**!!! Exercise**: Try it!

```
$ wc mm39_chrom_sizes.txt  sacCer3_chrom_sizes.txt
```

Continue on to [Wildcards](1-7_Wildcards.md)
