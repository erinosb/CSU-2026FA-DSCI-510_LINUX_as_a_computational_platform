# IO and Special Variables

How can we send information into a script? How do we get information out of script? This section will start to explore those concepts. Remember from before that this is called **Input/Output** or simply **IO**.

In this section, we're going to introduce **special variables**. In essence, special variables will allow us to access input that is supplied by the user as an argument. Before we get into the details of that, let's explore our options. How, generally, can we get data into scripts?

### Hard Coding

We can write the input into the script directly. If the input we're talking about is the name of a desired file, we can just write that name into the script itself.

```
#!/usr/bin/env bash
 
wc -w file1.txt
```

### Reading

We can have the user supply the input interactively using the command `read`

**!!! Exercise:** 
- Create a new directory called `moreScripting`
- In that directory, copy and paste some files from other places on your file system.
- Create a new script called `wordCounter.sh`.
- Copy and paste the following code into `wordCounters.sh`:

```
#!/usr/bin/env bash
 
echo "Type the name of the file do you want to count and press enter: "
read filetocount
 
wc -w $filetocount
```

- Make sure you know some of the filenames in your current working directory.
- Execute your script and see what happens:

```
bash wordCounter.sh
```

**Usage of read**

`read <variable name>`

`read` prompts the reader to type something and press enter. The entered keystrokes become the value assigned to the variable named in the command argument.

### Special Variables - passing input into scripts as arguments

We can also pass input into our script as arguments. These arguments can be typed in by the user as they execute the script on the command line like so:

`bash <shellscript.sh> [argument1] [argument2] …` 

Argument1 will be captured as a **special variable** that can be dereferenced using the syntax **$1** within the script itself. Argument2 can be dereferenced as **$2**. Special variables are initiated when you execute your code. They are useful for accessing information about how the script was executed.

Here's how we pass in arguments from the command line.

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

**!!! Example:** Here is a script called `countingLines.sh`

```
#!/usr/bin/env bash
 
wc -l $1
```

And it is executed on the command line like so:

```
$ bash countingLines.sh file1.txt
```

This is where the real power of programming/scripting comes in. Our special variables script has the exact same behavior as the hard coding and reading examples above. However, using special variables we can apply our script to different inputs without re-editing the script directly.

**!!! Best Practices** It is good practice to pass arguments into variables that have nice, descriptive names. This is a good idea because it is hard to remember what $1 means. Also, $1 looks really robotic in a script, especially once you start doing math. Try this …

```
#!/usr/bin/env bash
 
myfirstfile=$1
 
wc -l $myfirstfile
```

**!!! Independent Exercise:** 
- Create the script `countingLines.sh` as written above.
- Pass an existing file to `countingLines.sh` as an argument and ensure it is working properly
- How would you modify your script `countingLines.sh` so it can take in up to 3 arguments?

### Saving output from scripts

How did we save information to files on the command line?

Well, it's really the same within a script.

```
#!/usr/bin/env bash
 
wc $1 > output_counts.txt
```

**!!!** Within scripts, `»` which appends information to the end of an output file is often very handy. Just remember - you may want to use `>` the first time you start your output file. This ensures that if you run your scripts multiple times, it makes a new output file every time and doesn't append to the previous run's output file. 

```
#!/usr/bin/env bash
 
wc $1 > output_counts.txt
wc $2 >> output_counts.txt
```

It is technically possible to have a user supply the desired output file name as an argument. However, that can get risky by confusing input files that exist with output files that are going to be created. It becomes very easy to overwrite files accidentally.

In the next section, I'll show you how you can create output file names from input file names. This can be very handy.

Continue on to [String Operations](3-8_String_Operations.md)
