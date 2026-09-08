# String Operations

In computer programming, a **string** is a sequence of characters. Variables often point to values that are strings. Sometimes we want to do operations on those strings. We can do this using **string operations**.

By far the most common string operations performed are **replacements** which just means substitution. Another common operation is **sub-setting** or selecting out just a portion of the string, also called a **sub-string**.

**Replace a part of the string**

`<newvarname>=${<oldvarname>/<pattern>/<replacement>}`

Make a new variable `$newvar` that replaces one instance of “pattern” in `$oldvar` with “replacement”.

**!!! Exercise:** You can follow along on the command line:

```
oldvar="Colorado"
newvar=${oldvar/o/O}
echo $newvar #should output COlorado
```

**Globally replace a part of the string**

```
<newvarname>=${<oldvarname>//<pattern>/<replacement>}
```

Make a new variable `$newvar` that replaces ALL instances of “pattern” in `$oldvar` with “replacement”

```
oldvar="Colorado"
newvar=${oldvar//o/O}
echo $newvar # should output COlOradO
```

**Replace a prefix**

`<newvarname>=${<oldvarname>/#<pattern>/<replacement>}`

Make a new variable `$newvar` that replaces “pattern” at the BEGINNING of the string `$oldvar` with “replacement”.

```
oldvar="To be or not to be"
newvar=${oldvar/#To/So}
echo $newvar # should be "So be or not to be"
```

**Replace a suffix**

`<newvarname>=${<oldvarname>/%<pattern>/<replacement>}`

Make a new variable `$newvar` that replaces “pattern” at the END of the string `$oldvar` with “replacement”.

```
oldvar="file1.txt"
newvar=${oldvar/%txt/fastq}
echo $newvar # should be "file1.fastq"
```

**Subset a string** 

`<newvarname>=${<oldvarname>:<n>}`

Make a new variable `$newvar` that corresponds to the `$var` string starting at nth letter.

```
oldvar="California"
newvar=${oldvar:3}
echo $newvar # should be ifornia
```

**Subset a string of specific length** 

`<newvarname>=${<oldvarname>:<n>:<length>}`

Make a new variable `$newvar` that corresponds to the `$oldvar` string starting at nth letter and going for “length” letters.

```
oldvar="California"
newvar=${oldvar:3:4}
echo $newvar # should be "ifor"
```

Cheatsheet For String Replacement - Altering the Values of Variables

| Syntax | Description |
|--------|-------------|
| `${oldvar/find/replace}` | Replace the *first* match of **find** with **replace** from **oldvar** |
| `${oldvar//find/replace}` | Replace the *every* match of **find** with **replace** from **oldvar** |
| `${oldvar/#find/replace}` | If **find** matches the *first* characters of **oldvar**, replace them with **replace** |
| `${oldvar/%find/replace}` | If **find** matches *last characters* of **oldvar**, replace them with **replace** |
| `${oldvar:position:length}` | Extract **length** characters from **oldvar** starting at **position** |
| `${#oldvar}` | Report the number of characters in **oldvar** |

**!!! Practice on your own:** Try to modify your script from before called `countingLines.sh` so that it takes in a single text file as an argument, say `file1.txt`. Then, have your script print out the number of lines in that file to a new output file called `file1_linecount.txt`.


<details>
  <summary>Answer here</summary>

```
#!/usr/bin/env bash
 
# capture the first argument in a variable called myfirstfile
myfirstfile=$1
 
# use a sub-string substitution line to create a new variable called myoutputfile in which .txt is substituted for _linecount.txt
myoutputfile=${myfirstfile/%.txt/_linecount.txt}
 
# operate on the input file and save the line count to the desired output file
wc -l $myfirstfile > $myoutputfile
```

</details>

Continue on to [Environmental Variables](3-9_Environmental_Variables.md)
