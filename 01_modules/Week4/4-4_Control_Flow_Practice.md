# Control Flow Practice

### Todays objectives: 

<details>
  <summary>Click to expand/collapse</summary>

---

- **Vocabulary**
  - High-Performance Computing (HPC)
  - Supercomputer
  - Compute Cluster
  - Nodes
    - Login nodes
    - Compile nodes
    - Compute nodes
  - Custom Commands
  - `$PATH` – your path
  - `.bash_profile` file

- **Things you should know how to do after this class**
  - Know how to log onto ALPINE
  - Understand the benefits of using a supercomputer
  - Have a rudimentary understanding of Nodes on ALPINE
    - Understand that you shouldn’t do large jobs on the login node
  - Have a rudimentary understanding of the File Structure system on ALPINE
  - Learn about the $PATH which is an environmental variable.
    - Be aware of the concept of adding directories to your $PATH
  - Have a cursory knowledge about how .bash_profile files can be used to customize the user experience
  - Learn about the main steps in creating a custom command

- **Commands covered**
  - `acompile`
  - `curc-quota`
  - `module avail`

---

</details>


### Reminder: 

Final exam due on teusday September 23rd! 

### Test your understanding - take this quiz!

[Quiz 7](https://forms.gle/LFgfbRWYnnCYCDM16)

### Exercises for practice

**!!! Exercise 1** - Use a `for` loop structure to produce the following output:

```
10
9
8
7
6
5
4
3
2
1
blast off!
```

<details>
  <summary>Answers</summary>

---

```
#!/usr/bin/env bash
 

numbers=(10 9 8 7 6 5 4 3 2 1 "Blast-Off!")
 
# each element in the array variable houses will be sequentially accessed as the variable $housename
for number in ${numbers[@]}
do
    echo -e "$number"
 
done
```
```
#!/usr/bin/env bash
 
array=(10 9 8 7 6 5 4 3 2 1)
 
for num in ${array[@]}; do
    echo -e "$num"
done
 
echo -e "Blast off!"
```
```
#!/bin/bash
for ((i=10; i>=1; i--)); do
        echo $i
done
echo "blast off!"
```
```
TBD
```

---

</details>


**!!! Exercise 2** - Use a `while` loop structure to produce the same output above.

<details>
  <summary>Answers</summary>

---

```
#!/usr/bin/env bash

x=10

while [ $x -ge 1 ]
do
    echo $x
    (( x-- ))
done

echo "Blast off!"
```
```
#!/usr/bin/env bash

i=10

while [ $i -gt 0 ]
do
    echo "$i"
    i=$((i - 1))
done

echo "blast off!"
```

---

</details>

**!!! BONUS - Exercise 3** - `measureDiskSpace.sh` - Add to the `measureDiskSpace.sh` script so that instead of printing content to the screen, it now redirects all its output to a file called `diskUsage_output.txt`

**!!! BONUS - Exercise 4** - `measureDiskSpace2.sh` - create a conditional inside your loop that gives a different message if the file is empty like so …

```
$ bash measureDiskSpace.sh *.txt
The file listOfHouses.txt takes up 4.0K of disk space
The file text1.txt takes up 4.0K of disk space
The file text2.txt takes up 4.0K of disk space
WARNING! text3.txt is empty!!!
The file text4.txt takes up 4.0K of disk space
```

Answer for Exercise 4:

<details>
  <summary>Answer</summary>

```
#!/usr/bin/env bash
 
#Note: This answer contains a conditional within a for loop...
 
# For loop
   # If
   # Else
 
 
# Capture arguments
myarguments=$@
 
#Loop over each argument
 
for myfile in ${myarguments[@]}
do
	# Calculate the disk usage for a file
	# Remove the file name from the output using cut
	# Remove white space from the output using sed
	myspace=$( du -h $myfile | cut -f 1 | sed 's/ //g' )
 
	# Check if $myspace is 0B
	if [ $myspace == "0B" ]
	then
		# If file is empty, say so
		echo "File is empty!"
	else
		# If file is not empty, print the sentence including the file name and the disk usage:
		echo -e "The file $myfile takes up $myspace of disk space"
	fi
 
done
```

</details>

**!!! SUPER ULTIMATE NINJA SKILLS CHALLENGE EXERCISE - Exercise 5** - Remember the SARS-COV2 GTF file we downloaded before? Go ahead and download that again. Write a script that selects only the coding sequence entry lines (says CDS on column 3), and then outputs the gene name (written after gene_id in column 9), and then calculates the length of the coding sequence, and then outputs the following:
- Input file: [SARS-CoV-2 genome](https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Data/SARSCoV2_ncbiGenes.gtf)
- Example output: 
```
ORF1a 	13214
ORF1ab 	13202
ORF1ab 	8084
S 	3818
ORF3a 	824
E 	224
M 	665
ORF6 	182
ORF7a 	362
ORF7b 	128
ORF8 	362
N 	1256
ORF10 	113
```
- Note: - this is super hard and you'll need to try things that we didn't cover in class as well as navigate through some weird syntax funkiness.

Answer for exercise 5:

<details>
  <summary>Answer</summary>

```
#!/usr/bin/env bash
 
# take in the file as an argument/special variable
mygtf="$1"
 
# Select just the CDS entries
grep 'CDS' $mygtf > temp.gtf
 
# Acquire gene names, start, and stop as array variables
genenames=($(cut -f 9 temp.gtf | cut -d ' ' -f 2 | sed 's/"//g' | sed 's/;//g'))
starts=($(cut -f 4 temp.gtf ))
stops=($(cut -f 5 temp.gtf ))
 
# Initiate a counter
x=0
 
# Conditional While loop
while [ $x -lt ${#genenames[@]} ]
do
 
	# print the gene name
	echo -ne ${genenames[$x]} "\t"
 
	# calculate the length of the 
	diff=$((${starts[$x]} - ${stops[$x]}))
 
	# conditional - if it's a negative, take the positive
	if [ "$diff" -lt 0 ]
		then
        diff=$(($diff * -1))
	fi
 
	# print out the distance 
	echo $diff
 
	# increment the counter
	((x++)) 
 
done
```

</details>

Continue on to [Intro to Alpine](4-5_Intro_to_Alpine.md)
