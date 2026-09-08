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

She has written the following code but it doesn't seem to work. Can you fix her code for her so it has the desired behavior?

```
#!/bin/usr/env/bash 

# This script will take a file (likely a .gtf file) and convert any chromosome names in the format chrI, chrII, chrIII to chromosome1 chromosome2, chromosome3, etc.
# This script is designed specifically for the C. elegans chromosome that has 5 autosomes and an X chromosome

# This script will prompt the reader for a file to convert
echo -n "convertChrom>>> Enter your filename and press [RETURN]: "
read filename

# replace the chromosome names
sed -e 's/chrI/chromosome1/g' $filename | sed -e 's/chrII/chromosome2/g' | sed 's/chrIII/chromosome3/g' | sed 's/chrIV/chromosome4/g' | sed 's/chrV/chromosomeV/g' | sed 's/chrX/chromosomeX/g'
```

**Hint** make a test file with all possible `chrI`, `chrII` combinations. 

---

## Question 2 

---

## Question 3 

---

## Question 4

--- 

## Question 5

