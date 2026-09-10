# String Operations

In computer programming, a **string** is a sequence of characters. They often show up as words, ID #'s, or sentences. Variables often point to values that are strings. Sometimes we want to do operations on those strings. We can do this using **string operations**.

By far the most common string operations performed are **replacements** which just means substitution. Another common operation is **sub-setting** or selecting out just a portion of the string, also called a **sub-string**.

In effect, string operations replace the value of a variable using certain rules.

## Replace a part of the string

`<newvarname>=${<oldvarname>/<pattern>/<replacement>}`

Make a new variable `$newvarname` that replaces one instance of “pattern” in `$oldvarname` with “replacement”.

:hammer_and_wrench: ***Group Exercise:** You can follow along on the command line:

```
oldvar="Colorado"
newvar=${oldvar/o/O}
echo $newvar #should output COlorado
```

## Globally replace a part of the string

```
<newvarname>=${<oldvarname>//<pattern>/<replacement>}
```

Make a new variable `$newvar` that replaces ALL instances of “pattern” in `$oldvar` with “replacement”

```
oldvar="Colorado"
newvar=${oldvar//o/O}
echo $newvar # should output COlOradO
```

## Replace the beginning of a string

`<newvarname>=${<oldvarname>/#<pattern>/<replacement>}`

Make a new variable `$newvar` that replaces “pattern” at the BEGINNING of the string `$oldvar` with “replacement”.

```
oldvar="To be or not to be"
newvar=${oldvar/#To/So}
echo $newvar # should be "So be or not to be"
```

## Replace the end of a string

`<newvarname>=${<oldvarname>/%<pattern>/<replacement>}`

Make a new variable `$newvar` that replaces “pattern” at the END of the string `$oldvar` with “replacement”.

```
oldvar="To be or not to be"
newvar=${oldvar/%be/see}
echo $newvar # should be "To be or not to see"
```

This one is VERY important for replacing file extensions like so...

```
oldvar="file1.txt"
newvar=${oldvar/%txt/csv}
echo $newvar # should be "file1.csv"
```

## Subset a string

`<newvarname>=${<oldvarname>:<n>}`

Make a new variable `$newvar` that corresponds to the `$oldvar` string starting at nth letter.

```
oldvar="California"
newvar=${oldvar:3}
echo $newvar # should be ifornia
```

## Subset a string to be a specific length

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

:hammer_and_wrench: **Independent Exercise** 
  - Write a script that takes in a `.gff` file as an arugment (Use $1). 
  - Let's say we give it the file `covid.gff`. 
  - Write a string operation within the script to produce an output a file whose name takes the input file and changes it to `_output`. For example `covid_output.gff`


<details>
  <summary>Answer here</summary>

```
#!/usr/bin/env bash
 
# capture the first argument in a variable called myfirstfile
mygff=$1
 
# use a string operation line to create an outputfile
myoutputfile=${mygff/%.gff/_output.gff}
 
# create the new outputfile
echo "making file $myoutputfile"
touch $myoutputfile
```

</details>

Continue on to [Putting it all together](3-7_Putting_it_all_together.md)
