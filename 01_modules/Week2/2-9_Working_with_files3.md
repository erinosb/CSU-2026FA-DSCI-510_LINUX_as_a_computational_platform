# Working with files 3

Already, we have learned many ways of working within files to read, find, or change their contents.

- `cat`
- `grep`
- `cut`
- `sort`

In this section we'll learn

- `sed`
- `tr`
- `AWK` (I'll just reference you to AWK)

### Substitutions with `sed`, `tr`, `AWK`

In this section, we'll add to our toolkit by learning three ways to **find and replace** select content within a file. The first is using `sed` **- Stream EDitor**. `sed` is a complex program capable of filtering and transforming text within a file. sed is capable of very complex functionality, but for today, we'll just learn its **find and replace** function.

The second way to substitute content will be using `tr` or the translate command. This is a more simple, limited utility.

And the last is `awk` which I'll just describe and refer you to, but we won't delve into.

### `sed` - Stream EDitor

**sed usage:**

`sed [options] 's/search/replace/flags' <filename.txt>`

- search - this is a string you want to find
- replace - this is a string you want your found string to be replaced with
- flags - these are options you can use to modify how sed works

**sed flags**

```
's/search/replace/g' - g - global - apply search-and-replace to ALL instances, not just the first

's/search/replace/i' - i - case insensitive - the "search" will match a string without regard to upper or lower case. # Doesn't work on MAC.
```

**sed options**

```
-e  Expression. Allows multiple search and replace actions
```

**!!! Group Exercise:** Let's make a file called `DNA.txt` and save in it some capital and lower case A,T,C,G sequence like 'ATCAGATATAGATTTTAACCCAAttatcctt' or some such.

Say we want to translate this sequence into an RNA sequence. That is, we want all the T's to become U's. Try the following commands. What does each do? Do they all work (on MAC, they may not)?:

```
$ sed 's/T/U/' DNA.txt 
$ sed 's/T/U/g' DNA.txt 
$ sed 's/t/u/' DNA.txt 
$ sed 's/t/u/i' DNA.txt 
$ sed 's/T//g' DNA.txt
```

To combine search patterns together, use the option `-e`

```
$ sed -e 's/T/U/g' -e 's/t/u/g' DNA.txt
```

**!!! Group Exercise:** How would you save your translated RNA sequence into a file called `RNA.txt`?

**Extended Learning** Please explore more ways to use `sed`: [https://www.grymoire.com/Unix/Sed.html](https://www.grymoire.com/Unix/Sed.html). Those instructions will show you how to use `sed` to …

- Use complex regular expressions for searching
- Retain aspects of the matched string
- Duplicate the matched string
- Resolve duplications
- Specify which occurrences to replace
- Pipe together multiple sed replacements into complex combinations
- Save complex search and replace instructions into files for re-use

### Translate - `tr`

Translate (`tr`)is a much smaller program than `sed` but is better suited to simple tasks, such as in translating DNA:

**tr usage:**

`tr <find> <replace> < <input_file>`

We can give many options within the **find** or **replace** fields using square brackets.

```
$ tr [a-z] [A-Z] < DNA.txt     #will convert everything to upper case
$ tr [A-Z] [a-z] < DNA.txt     #will convert everything to lower case
$ tr [T] [U] < DNA.txt         #will convert T's to U's
$ tr [Tt] [Uu] < DNA.txt       #will convert upper case T's to U's and lower case t's to u's
```

**!!! Common pitfall:** for some reason `tr` needs its input argument specifically indicated as its input using the redirect `<` or using a piped cat command:

```
$ cat DNA.txt | tr [Tt] [Uu]
$ tr [Tt] [Uu] < DNA.txt
$ tr [Tt] [Uu] < DNA.txt > RNA.txt
```

For zsh users ... you need to update the syntax for `tr` to 

```
% tr 'Tt' 'Uu' < DNA.txt

# This also works in the bash shell!
```

### AWK

`AWK` is a speedy little program developed in the 1970's at Bell labs by three programmers Alfred Aho, Peter Weinberger, and Brian Kernighan. The name is the initials of their last names but sounds like the bird, auk.

`AWK` allows users to search and replace but to have a lot of control over the searching, the replacing, and the final output of the printed results.

To learn about using `AWK` on the command line, I suggest this guide: [Geeks for Geeks AWK Command Line Examples](https://www.geeksforgeeks.org/linux-unix/awk-command-unixlinux-examples/)

`AWK` can also be built into complex written scripts.

Here is some example usage for 'awk' ... 

```
awk '{ gsub(/T/, "U"); print }' DNA.txt

awk '{ gsub(/T/, "U"); gsub(/t/, "u"); print }' DNA.txt
```

### A Note on Complexity and Speed

If this is starting to feel AWKward, you're not alone. Once you start to imagine how you want to search, replace, and print out information, your imaginings can quickly outpace what even a sed or awk command can easily do. It's time to level up to python or javascript.

`sed` and `AWK` are extremely fast! If you can write code in them, they will typically run faster than a python code.

Continue on to [Intro to scripting - Scripting 1](3-3_Scripting1.md)
