<p align="center">
<img width="100%" alt="icons" src="../../05_images/headers_Slide5.png">
</p>

# Working With Files 2

The following commands will help you to access and organize the information contained in files.

`cat` – concatenate. concatenate files together

`grep` – regular expressions. search for a specific pattern within a file

`cut` – pull out a specific column (or any other delimited information) from a file

## Let's make a file

:hammer_and_wrench: **Group Exercise**

To prepare for the exercise, please do the following …

1. Make a directory called `workingWithFiles`
2. Using `nano`, copy and paste the following content into a file called `chr_sizes.txt`

```
# a list of the yeast chromosomes and their lengths
chrIV	1531933
chrXV	1091291
chrVII	1090940
chrXII	1078177
chrXVI	948066
chrXIII	924431
chrII	813184
chrXIV	784333
chrX	745751
chrXI	666816
chrV	576874
chrVIII	562643
chrIX	439888
chrIII	316620
chrVI	270161
chrI	230218
chrM	85779
```

## Concatenating files with `cat`

The `cat` command reads one or more files and prints the output of all files to the screen. The output can be redirected to a file, as well, and in this way, we can join files together.

**concatenate usage:**

`cat <file.txt> …`

Typically, we join two different files together. For the purpose of example, let's try to duplicate the contents of our file using cat. The  `…` means you can keep adding more and more files.

```
$ cat chr_sizes.txt chr_sizes.txt
$ cat chr_sizes.txt chr_sizes.txt > double_sizes.txt
$ more double_sizes.txt
$ wc chr_sizes.txt
$ wc double_sizes.txt 
```

:question: **Challenge question:** If you had the following files in your directory, how would you concatenate them together using a wildcard?

```
$ ls
data1.csv data2.csv data3.csv data4.csv

$ 
```

-----

## Searching for patterns using `grep`

**Regular expressions** in computing describes a sequence of characters for which you want to search. It is often shortened to *regex*. Regular expressions are very powerful in computing and the expressions themselves can quickly become very complex with lots of wildcards and wiggle room for complex variations on the searched pattern. For this lesson, we'll focus on simple letter and number combinations. In this case, we can think of it here as simple pattern searching and matching.

**grep usage**

`grep [options] <pattern> <file> …`

- there are many options for `grep`
- Typically, the pattern given to search is enclosed in quotes.
- `grep` can search multiple files

Let's say we want to know how long the mitochondrial genome is in yeast:

```
$ grep 'chrM' chr_sizes.txt
```

:hammer_and_wrench: ***Individual Exercises:** Try executing the following to get a sense of what grep does and does not do. To learn more about these options, read the grep man page.

```
$ grep -n 'chrM' chr_sizes.txt
$ grep -v 'chrM' chr_sizes.txt
$ grep -v '#' chr_sizes.txt
$ grep 'chr' chr_sizes.txt
$ grep '^chr' chr_sizes.txt 
$ grep 'chrII' chr_sizes.txt
$ grep -w 'chrII' chr_sizes.txt
$ grep 'V$' chr_sizes_new.txt #doesnt have the chromosome file sizes 
```

>[!WARNING]
> Did you notice how searching for `chr` gave you both the chromosomes listed in columns as well as the word `chromosome` in the header? Also, `chrII` returned both `chrII` and `chrIII`. This is something to look out for with grep. We'll cover more advanced ways to restrict your regular expressions in later lessons.

>[!TIP]
> As long as you use quotes around your search pattern, you can include a space in it.

>[!TIP]
> The syntax `$ grep -v “#” somefile.txt > cleanfile.txt` gets used A LOT. We use it to remove comment lines from files.

>[!TIP]
> The carrot character `^` is called an **anchor** in this context and denotes that the characters to search must be located at the start of the line.

---


## Advanced GREP

`Grep` and REGEX are very flexible and can accept a wide array of wild cards, character types, and variable regions. This is very useful, particularly in the life sciences. However, it is easy to get confused as the syntax looks very busy. Here is a cool resource on advanced grep operations that are beyond the scope of the course at this stage.

[GREP regular expressions](https://www.cyberciti.biz/faq/grep-regular-expressions/)

----

## Extracting columns with `cut`

`cut` is a command that can be used for slicing and dicing information out of delimited files. We'll just use the most basic feature of `cut` which, by default, pulls out specific columns from tab delimited files. There are ways to change this so that it splits on other delimiters, but today, we'll just stick with the default operation.

**column extraction usage**

`cut -f <number> -d <character> <file.txt>`

 - `-f` - the Field # you want to extract
 - `-d` - the "delimiter" you want to use to split the fields. *default = TAB*

:hammer_and_wrench: **Group Exercise:** Let's try to just extract out some columns using cut. cut works by default by splitting a file into tab-delimited columns. The “tab” is called the **delimiting character** the column is called a **field**.

- Let's make a test file that has two fields by removing the first line from `chr_sizes.txt`.
- Next, we can extract the first column or second column using `cut`:

```
$ grep -v "#" chr_sizes.txt > chr_sizes_table.txt
$ cut -f 1 chr_sizes_table.txt
$ cut -f 2 chr_sizes_table.txt
$ cut -f 1,2 chr_sizes_table.txt
```

>[!WARNING]
> The `cut` utility counts like so: 1, 2, 3, 4. However, not all computing languages start on 1. Many start on 0 and count like so: 0, 1, 2, 3. It is a good idea to double check your language by testing it every time.

<p align="center">
<img width="75%" alt="mug" src="../../05_images/worlds_0_programmer_mug.png">
</p>

>[!WARNING]
> `cut` defaults to looking for **tab** delimiting. It outputs with a default **tab** separator. To change these defaults, you can use the option **-d**. On a MAC, this changes both the input and output delimiting character. In other versions of cut, the two can be specified independently.

If you want to use a different character than `TAB` to differentiate the fields, use the `-d` option like so...

```
$ cut -d "," -f 2 file.txt #set the delimiting character to a comma, and then cut out the second field.
$ cut -d " " -f 2 file.txt #set the delimiting character to a space, then cut out the second field.
$ cut -d "\t" -f 2 file.txt #set the delimiting character to a tab, then cut out the second field. (default)
$ cut -d "." -f 2 file.txt #set the delimiting character to a ., then cut out the second field. 
```

Continue on to [Practice grep and cut](2-7_Practice_grep_and_cut.md)
