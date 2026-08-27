<p align="center">
<img width="100%" alt="icons" src="../../05_images/headers_Slide5.png">
</p>

# Working With Files 1

## Peeking inside files with `more` and `less`

There are four main commands for printing file contents to the screen …

- `more` – scroll down through files
- `less` – scroll up or down through files
- `head` – show the top n lines. The default is n = 10
- `tail` – show the bottom n lines. The default is n = 10

:hammer_and_wrench: **Group Exercise** 

- Navigate to your directory titled `chrom_proj`
- Try the following ways of peeking into files in that directory …

```
$ more At_chromosome.tsv  # OR
$ Hs_chromosome.tsv
```

  - Use **spacebar** or **down arrow** or **return** to scroll down
  - Type **q** to quit

```
$ less Hs_chromosome.tsv
```

  - Use **spacebar** or **down arrow** or **return** to scroll down
  - Use **b** or **up arrow** to scroll up
  - Type **q** to quit

```
$ head less Hs_chromosome.tsv #show first 10 lines
$ head -n 5 less Hs_chromosome.tsv #show first 5 lines
$ tail less Hs_chromosome.tsv #show last 10 lines
$ tail -n 5 less Hs_chromosome.tsv #show last 5 lines
```

>[!TIP]
> Sometimes it looks like head or tail are showing way more lines than you expect. If your lines are very, very long (typical in bioinformatics), this may be due to forced word wrapping in the terminal. Try re-sizing your browser bigger or smaller to see if this is the case.

:hammer_and_wrench: **Group Exercise** 

- Practice readingdifferent files in the `chrom_proj` directory using each command.
- Try using some options.
- Read the two **README** files.

----

## Getting file info 

One of the handiest commands for getting information about a file is word count.

`wc <file.txt> …`

Word count spits out:

1. number of **lines** in the file
2. number of **words** in the file
3. number of **characters/bytes** in the file
4. the file name
5. some totals if multiple files are given.

```
$ wc At_chromosome.tsv
$ wc Hs_chromosome.tsv.txt
$ wc *.txt # This will list the word count of ALL the .txt files
```

:question: What is Ta?

:sunglasses: **Cool trick**: We can also use options with **wc**:

```
$ wc -l    # lists only the number of lines
$ wc -w    # lists only the number of words
$ wc -c    # lists only the number of characters
```

----

## Multiple Arguments

To date, we have only performed a command on a single argument:

`$ command [argument]`

Most commands allow us to list multiple arguments and will perform the command on them in the order written:

`$ command [argument] <argument> <argument>`

:hammer_and_wrench: **Individual Exercise** 

```
$ wc At_chromosome.tsv Bs_chromosome.tsv Ce_chromosome.tsv 
```

Continue on to [Wildcards](1-7_Wildcards.md)
