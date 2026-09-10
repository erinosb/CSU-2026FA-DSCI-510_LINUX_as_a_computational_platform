<p align="center">
<img width="90%" alt="icons" src="../../05_images/headers_arrows.png">
</p>

# IO and Special Variables

How can we send information into a script? How do we get information out of script? This section will start to explore those concepts. Remember from before that this is called **Input/Output** or simply **IO**.

Why would we want to do this? Well, eventually, we are going to want to point our scripts to certain files. We will want the scripts to either read the files and analyze its contents. Or, we may want to change the file itself. 

In this section, we're going to introduce **special variables**. In essence, special variables will allow us to access input that is supplied by the user as an **argument**. 

Before we get into the details of that, let's explore all our options. How, generally, can we get data into scripts?

----

## Hard Coding

We can write the input into the script directly. If the input we're talking about is the name of a desired file, we can just write that name into the script itself.

```
#!/usr/bin/env bash
 
wc -w file1.txt
```

:hammer_and_wrench: **Group Exercise:** Let's navigate to the directory `Covid` where we had the `covid_annotation.gff` and `covid_sequence.fna` files. This may be in a directory called `genomes`. Or, if you want to download it again, just go to [03_data](../../03_data).

  - Make a script called `analyzeGFF.sh`
  - Navigate into it using your text editor
  - Copy and test the following code into `analyzeGFF.sh`


```
#!/usr/bin/env bash

# get a gff file by hardcoding
mygff="covid_annotation.gff"

# How many lines are there?
cat $mygff | wc -l
```

  - Now test it using:

```
$ bash analyzeGFF.sh
```

----

## Reading

Alternatively, we can ask the user to supply input using the command `read`

:hammer_and_wrench: **Group Exercise:** 

  - Comment out your previous lines and start new:

```
#!/usr/bin/env bash

## get a gff file by hardcoding
# mygff="covid_annotation.gff"

########################
 
# get a gff file by reading
echo "Type the name of the gff file to process: "
read mygff
 
# How many lines are there?
cat $mygff | wc -l
```

  - Try it!

>[!TIP]
> To do this, the file you give it must either be in your current working directory. OR, you must give it a relative or absolute path to your file.

**Usage of read**

`read <variable name>`

`read` prompts the reader to type something and press enter. The entered keystrokes become the value assigned to the variable named in the command argument.

----

## Special Variables - passing input into scripts as arguments

We can also pass input into our script as arguments. These arguments can be typed in by the user as they execute the script on the command line like so:

`bash <shellscript.sh> [argument1] [argument2] ...` 

Argument1 will be captured as a **special variable** that can be dereferenced using the syntax **$1** within the script itself. Argument2 can be dereferenced as **$2**. Special variables are initiated when you execute your code. They are useful for accessing information about how the script was executed.


### List of special variables

| Syntax | Meaning |
|--------|---------|
| $0 | The name of the Bash script |
| $1 | The first argument passed to the script |
| $2 | The second argument passed to the script |
| $3 | The third argument passed to the script, etc … |
| $# | How many arguments were passed to the script |
| $@ | All the arguments supplied to the script |
| $* | All the arguments supplied to the script |

What does this mean? This means that whatever the user writes as `argument` in the terminal becomes the value associated with the special variable `1`. `1` can be dereferenced within your script as $1.

```
# in the terminal
$ bash script.sh <argument> 
```

```
# within the script
echo $1 # will print out <argument>

# OR
myfile=$1 # will capture the <argument> as the value of a new variable called myfile
```

:hammer_and_wrench: **Group Exercise:** 

  - Comment out your previous method of reading in the .gff file and amend your code to take in a special variable:

```
#!/usr/bin/env bash

## get a gff file by hardcoding
# mygff="covid_annotation.gff"
 
## get a gff file by reading
#echo "Type the name of the gff file to process: "
#read mygff

########################

# get a gff through $1
mygff=$1

# How many lines are there?
cat $mygff | wc -l
```

And it is executed on the command line like so:

```
$ bash analyzeGFF.sh covid_annotation.gff
```

This is where the real power of programming/scripting comes in. Our special variables script has the exact same behavior as the hard coding and reading examples above. However, using special variables we can apply our script to different inputs without re-editing the script directly.

>[!TIP]
> **Best practices:** It is good practice to pass arguments into variables that have nice, descriptive names. This is a good idea because it is hard to remember what $1 means. Also, $1 looks really robotic in a script, especially once you start doing math. Try this ...

:hammer_and_wrench: **Independent Exercise:** 

- How would you modify your script `analyzeGFF.sh` so it can take in 3 arguments (3 .gff files)?

----

## Capturing output from a script

How did we save information to files on the command line?

Well, it's really the same within a script.

```
cat $mygff | wc -l > output_counts.txt
```

`>` and `»` append information to the end of an output file. They allow us to create reports. Just remember - use `>` the first time you start your output file. This ensures that if you run your scripts multiple times, it makes a new output file every time and doesn't append to the previous run's output file. Then, add additional information to that output file using `>>`.

```
#!/usr/bin/env bash

## get a gff file by hardcoding
# mygff="covid_annotation.gff"
 
## get a gff file by reading
#echo "Type the name of the gff file to process: "
#read mygff

########################

# get a gff through $1
mygff=$1

# How many lines are there?
cat $mygff | wc -l

# Start an output file
myoutputfile="todays_output.txt"
touch $myoutputfile

cat $mygff | wc -l > $myoutputfile
```

Test it with:

```
$ bash analyzeGFF.sh covid_annotation.gff
```

:exclamation: **Make it fancy** You can really go wild with this and create fancy reports like so...

```
#!/usr/bin/env bash

## get a gff file by hardcoding
# mygff="covid_annotation.gff"
 
## get a gff file by reading
#echo "Type the name of the gff file to process: "
#read mygff

## get a gff through $1
#mygff=$1

## How many lines are there?
#cat $mygff | wc -l

########################

# get a gff through $1
mygff=$1

# Start an output file
myoutputfile="todays_output.txt"
touch $myoutputfile

# Reporting
echo -e "Hi. It looks like you've started analyzeGFF.sh\n" > $myoutputfile

echo -e "I will now process the file $mygff\n" >> $myoutputfile

# Calculating
myLineNum=$(cat $mygff | wc -l | sed 's/ //g')

# More reporting
echo -e "The file $mygff has $myLineNum numbers\n" >> $myoutputfile

echo -e "analyzeGFF.sh complete! Thank you! Come again!\n" >> $myoutputfile
```


----

## What kind of information can be passed as a special variable?

We passed a file to the script, but we can pass any text information to the script as an argument. For example, if we want the user to specify the name of the desired output file, they can. 

```
$ bash analyzeGFF.sh covid_annotation.gff 260910_output.txt
```

:hammer_and_wrench: **Thought Exercise:** 

  - How would you get this code to work?

Continue on to [String Operations](3-6_String_Operations.md)
