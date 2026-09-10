
# Putting it all together - DNA2RNA example

Here is a little script that will take in a file that contains a DNA sequence and converts it to RNA. The program is called DNA2RNA.sh and it is used like so...

```
$ bash DNA2RNA.sh <file.txt>
```

Here is the script for `DNA2RNA.sh`:


```
#!/usr/bin/env bash

# The point of this program is to take a text file with DNA sequence and convert it to RNA sequence.

# This program works as follows...
# $ bash DNA2RNA.sh <file.txt>
# It will output a file called file_RNA.txt

# take in a file
mydna=$1

# create an outputfile
myrna=${mydna/%.txt/_RNA.txt}

# tell the user what will happen:
echo "DNA2RNA>>> The file $mydna will be converted to $myrna"

# Do the conversion
sed -e 's/T/U/g' -e 's/t/u/g' $mydna > $myrna

# tell the user it is done:
echo "DNA2RNA>>> The file $myrna has been created"
echo "DNA2RNA>>> program complete"
```

This script is helpful to understand because it contrasts how we can use `sed` to search and replace text within a **file** versus how we use string operations to search and replace text within a **variable's value**.

Continue on to [Environmental Variables](3-8_Environmental_Variables.md)
