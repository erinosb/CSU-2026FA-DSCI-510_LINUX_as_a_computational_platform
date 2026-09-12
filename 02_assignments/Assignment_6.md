# Assignment 6

- Due **Tuesday, September 15, 2026, 10:00 am** 
- **DO NOT write out the questions. Do not write long descriptions. Only write your succinct answers.**
- Enter your answers into a .txt file within a text editor such as BBEdit, Notepad++, or some other application. Do not use Word. Do not use TextEdit (MAC).
- Do not include the questions in your answer file.
- **Turn in your answers as the .txt file on Canvas by uploading your file.**
- Assignments account for 30 % of your final grade. 

---

**Hint:** Do not include the question text in your answer. Just copy-and-paste your script or code into a text file.

---

## Question 1

## Question 1 - Read the exam assignment

For this question, read the exam assignment. Answer Question 1. *Note - you don't have to commit to this file type for the realy Project Exam. You can switch if you want to. The objective of this question is to start you working on your exam project*

**Answer the following:** What file type did you select? Describe the information that is gathered in your file type. If your file has columns, what is tabulated in each column? For full credit, you must explain how this information is organized - what are the column headers? What are the information blocks?

----

## Question 2

For this question, read the exam assignment. Answer Question 2. *Note - you don't have to commit to this file type for the realy Project Exam. You can switch if you want to. The objective of this question is to start you working on your exam project*

- A. What is the operation your script will perform?
- B. Why is this a useful operation to do in your field or in your project?
- C. What is the NAME of your script? (it cannot be script.sh. The name needs to be informative)
- C. Outline a few key commands or steps your script will do. 

Having trouble? Think about how you might filter, sort, select, re-format, compile, quantitate, or display information from your text file in a way that would be meaningful.

*Note - as part of this answer, you need to explain to me a little bit about your project and your field*

----

## Question 3

Alexi is working in the terminal to execute a shell script he has just written. This is what is on his terminal.

```
$ pwd
/user/alexip/dataproject1/
 
$ ls -1
image201.tif
image202.tif
image203.tif
image204.tif
image205.tif
processImages.sh
 
$ bash processImages.sh *.tif
```

What will be the values of the following special variables within Alexi's script when he executes the script (last line above)?

- A. $0
- B. $1
- C. $2
- D. $@
- E. $#

----

## Question 4 - 2 pts

Write a short script called tabToCSV.sh. It takes in as input, a tab-delimited text file and converts it to a comma-separated file, the output file.

Is executed like so…

```
$ bash tabToCSV.sh file1.txt
```