# Final Exam

- **Due by Thursday September 24 th at 11:59 pm.**
- If you need more time to complete this exam, please contact me in advance!
- This exam accounts for 40 % of your final grade. 

--- 

## About the exam

This exam will be a **project**. You will be asked to pick a **standardized file type** in your field. You will be asked to **write a bash program** that performs some operation on this standardized file type. Your program should be able to take one or more of these standardized file types and perform some operation on them. It will also report a **message** if the user did not execute the program properly.

Students who have gotten the most out of this exercise have found ways of linking this exercise to their immediate research goals and projects. If you are not in a lab with a project, you can still work to link this project to your life in some way. Text/flat files are all around us. I am totally ok with this exercise having nothing to do with your project or even science. Be creative!

Are you having trouble figuring out a file type or project? Click here for some [examples of previous projects](Examples_of_previous_projects.md). 

-----

## Grading 

The grade for the final will be structured like so …

```
2  pts - Question 1
2  pts - Question 2
2  pts - Question 3
10 pts - Question 4
   1 pts - is commented
   1 pts - Takes in the file as a special variable argument ($1)
   2 pts - Outputs the result to the screen (that can be captured in a redirect) or to an output file
   2 pts - Contains **at least 3 loops or conditionals** in any combination (3 loops, 2 loops + 1 conditional, etc).
   2 pts - Reports to the user (display) what it is doing at different steps in the process.
   2 pts - If the user fails to provide an input file, your script should print to the screen that something is wrong and suggest the proper usage of the script using a **usage statement**.
2  pts - Question 5
2  pts - Question 6

20 pts - TOTAL (this will be scaled to be 35.5 % of your grade)

```

----

## Question 1

Select a standardized file type in your field. You can use any flat/text file formats listed in this [Wikipedia page of scientific standardized file types](https://en.wikipedia.org/wiki/List_of_file_formats). OR, you can pick any other file type that is flat. If you are a master's student or a graduate student not currently in a lab, you can pick any of the file formats we covered in class (.fa, .gtf) or go on the internet and try to learn more about how information is stored in the field or profession you eventually wish to join.

**Answer the following:** What **file type** did you select? Write a brief paragraph that describes the information that is gathered in your file type, what it is used for, and how it relates to a larger field of study.

Please break down how the information is organized within your file. For example, if your file has columns, what is tabulated in each column? For full credit, this answer must contain a list of each column number and its header, and/or a description of the file's sections of information.

----

## Question 2

**Answer the following:**
- A. What is the operation your script will perform?
- B. Why is this a useful operation to do in your field or in your project?
- C. What is the NAME of your script? (it cannot be script.sh. The name needs to be informative)
- C. Outline a few key commands or steps your script will do. 

Having trouble? Think about how you might filter, sort, select, re-format, compile, quantitate, or display information from your text file in a way that would be meaningful.


----

## Question 3

**Answer the following and submit input an output files**

- A. What is the **input** for your script? Describe the input and **attach** an example input file.
- B. What is the **output**? Describe the output and **attach** an example output file.
- C. What **command line entry**** will be used to execute your script? Write out the command line in full. (example $ bash myscript.sh )

To grade this question I will test your script using the command line you write in C, the script you supply, and the supplied input in A. You will receive full credit if my output matches your example output in B. For this reason, please tell me about any options or typed content that I will need to generate the output. You must include the input file, the script file, the output file, and a written description of how to execute the script for full credit.

If your input files are giant, please include a “tester” file. It will be a smaller version of the giant file that can still be used on the code. Please include the output of that tester file. Contact me if you have questions.

If I can't run your code and compare it to your output, you won't get points associated with this question.

----

## Question 4

Write your script and attach it. Your script MUST do the following for full credit:

  - Be commented
  - Take in the file as a special variable argument ($1)
  - Output the result to the screen (that can be captured in a redirect) or to an output file
  - Contain **at least 3 loops or conditionals** in any combination (3 loops, 2 loops + 1 conditional, etc).
  - Report to the user (display) what it is doing at different steps in the process.
  - If the user fails to provide an input file, your script should print to the screen that something is wrong and suggest the proper usage of the script using a **usage statement**.

Example:

```
$ bash gtf2bed.sh 
$ GTF2BED>>> ERROR >>>
  Please provide a proper input file in the form: 
     bash gtf2bed.sh input.gtf
```


Bonus goals - Can you have your script generate a final report to the user?

Bonus goals - can you think of how to write in an “option” using an if statement?

**What to turn in?** Attach your script

----

## Question 5 - Evaluation

Evaluate your own script. Does it work? If not, what do you think is the trouble? If so, how would you expand the script in the future? Or, what would you need to learn next to make this script more useful?

----

## Question 6 - Automation

*Note: This question is unrelated to the above project.*

**Answer the following:**

Carol has written a short bash script that takes in a file as a single argument and copies a backup into a backup directory with a new name (see below). Currently, this script only operates on one file at a time and is executed using the code `bash saveBackup.sh file1.txt`. How could she use a loop to automate this backup script so that it can work on many text files and be called using `bash saveBackup.sh *.txt`? *Use the hints in the code to help guide you.*

```
#!/usr/bin/env bash
 
# Make a backup directory if it doesn't already exist
mkdir -p backups
 
# Acquire the input filename. ## Hint - change this line to acquire multiple files
inputfile=$1
 
## Hint - Start loop here
 
# Substring replacement to create an output file name
outputfile=${inputfile/.txt/_bkp.txt}
 
# Save the backup 
echo -e "\nBacking up $inputfile. Saviing it as $outputfile in backup directory\n"
 
cp $inputfile backups/$outputfile
 
## Hint - Stop loop here
 
echo -e "saveBackups.sh program complete\n"
```

