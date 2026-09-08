# Assignment 5

- Due **Tuesday, September 15, 2026, 10:00 am** 
- **DO NOT write out the questions. Do not write long descriptions. Only write your succinct answers.**
- Enter your answers into a .txt file within a text editor such as BBEdit, Notepad++, or some other application. Do not use Word. Do not use TextEdit (MAC).
- Do not include the questions in your answer file.
- **Turn in your answers as the .txt file on Canvas by uploading your file.**
- Assignments account for 30 % of your final grade. 

---

## Question 1 - 10 pts

You friend would like to write a script that asks the user for a C. elegans gtf file and then converts any chromosome names with roman numbers into chromosome names with numerals. 

chrI -> chromosome 1, for example

She has written the following code but it doesn't seem to work. Can you fix her code for her so it has the desired behavior? Copy and paste your new script into the answer key. Include the shebang. Include comments. 

```
#!/bin/usr/env/bash 

# This script will take a file (likely a .gtf file) and convert any chromosome names in the format chrI, chrII, chrIII to chromosome1 chromosome2, chromosome3, etc.
# This script is designed specifically for the C. elegans genome that has 5 autosomes and an X chromosome

# This script will prompt the reader for a file to convert
echo -n "convertChrom>>> Enter your filename and press [RETURN]: "
read filename

# replace the chromosome names
sed -e 's/chrI/chromosome1/g' $filename | sed -e 's/chrII/chromosome2/g' | sed 's/chrIII/chromosome3/g' | sed 's/chrIV/chromosome4/g' | sed 's/chrV/chromosomeV/g' | sed 's/chrX/chromosomeX/g'
```

**Hint** make a test file that contains all entries to convert: `chrI`, `chrII`, `chrIII`, `chrIV`, `chrV`, `chrX`.

---

## Question 2 - 10 pts 

Write a quick shell script that prompts the user for a file that contains some DNA sequence (A's, T', G', and C's) and then outputs to the screen the corresponding RNA sequence in which any T's have been transformed into U's.

**Hint:** Use the read command in Question 1 to prompt the reader for their file

**Hint:** Make a test file 

**Hint:** Your code should include a shebang and comments

---

## Question 3 - 5 pts

Let's pretend the script you wrote in Question2 is called `DNA2RNA.sh`.

What would be the proper command line entry you would use to convert the test file `DNA1.txt` to a new files called `RNA1.txt` using your code `DNA2RNA.sh`?

**Hint** How would you re-direct the output of `DNA2RNA.sh` to the file `RNA1.txt`?