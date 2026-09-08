# Intro To Scripting 

### Chaining with `;`

So far, we've executed one command per line. However, we learned to pipe commands together, which is a way of combining two commands into one long command.

We can also execute two commands in succession. This is called chaining and it uses the `;` semi-colon.

**chaining usage:**

`command1; command2`

**!!! Exercise:** Try it:

```
$ mkdir testdir; touch testdir/testfile.txt
```

The shell waits for the first command to finish before the second command starts. You can command multiple commands together. Hmm, this seems very useful. If only there was a way we could build on this …

### What is a bash script? 

Next, we're going to level up and start saving our commands in files that can be executed. A simple such file is called a **script**. When scripts are written to be read by a linux shell, they are called **bash scripts**, and the process of coding in this way is called **bash scripting**.

To date, our interactions with the shell have been **interactive** similar to having a conversation with a person. Writing scripts will be analogous to writing a script for a movie or a play. In this way the conversations are written and recorded, to be recalled and acted out in a precisely defined order and in a precisely defined way at any time.

A **bash script** is simply a file that contains a list of linux commands. The **file extension** for bash scripts can take on a few different flavors, but for now we'll use `.sh` to identify them. The script is typically started with a special line called a **shebang** that answers the command line question `$ which bash` and looks like so:

```
#!/bin/bash
```

However, for this class, we'll get into the habit of using a slightly more complex shebang just because many people are running different types of shells. Our bash scripts will start like so:

```
#!/usr/bin/env bash
```

With minor exceptions, anything you can run normally on the command line can be put into a script and it will do exactly the same thing. Similarly, any commands you can put into a script can generally also be run on the command line.


### When do I use bash Scripts? 

If you have some reason to do the same **series** of commands over and over again, it is often best to write these commands into a script so that the process can be **automated** and **reproducible**.

Let's take an example. Say, I want to get into the habit of having the same sub-directory structure in every new project I start. I also want to have a readme file inside every project directory. I find myself doing the same list of commands every time I start a new project …

```
$ mkdir 01_input
$ mkdir 02_scripts
$ mkdir 03_output
$ touch README.txt
```

I can write these same commands into a script called `startProject.sh`. It looks like this …

```
#!/usr/bin/env bash
 
# Make three subdirectories
mkdir 01_input
mkdir 02_scripts
mkdir 03_output
 
# Start a readme file beginning with today's date and time:
touch README.txt
```

Let's take a look at each part of this script …

<p align="center">
<img width="410" alt="scripting1" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/scripting1.png">
</p>

### The nuts and bolts of writing

OK, so how do we actually write these scripts? I find it useful to use a **text editor** to write my scripts. I use BBEdit, so my scripts look like this. I write them in the BBEdit app.

<p align="center">
<img width="410" alt="scripting2" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/scripting2.png">
</p>

**Other options** - you can also write scripts in nano for simple scripts. There are other terminal-embedded text editors that are more complicated than nano like **vim** or **emacs** but these are beyond the scope of this class.

**On ALPINE** - ALPINE has its own text editor for you to use.

**!!! THE CHALLENGE:** the major challenge is syncing up where you are in the terminal with where your script of interest is located.

**!!! PC PITFALL** Are you working on Notepad++ on a PC and seeing weird stuff at the end of each line like `\r` or `\r\n`? If so, you'll need to set your “end of line conversion". To do this, go into Notepad++ **Settings –> Preferences** –> Navigate to **End of line conversion** and select unix/mac. OR, go to **Edit –> EOL Conversion** and select Windows/Linux/Mac.

### The nuts and bolts of executing

To execute a bash script, we simply navigate on the terminal to the place where our script is located. Then, I use `ls` to ensure I can **see** the script located in my working directory. Then, I execute it using the command **bash**, like so…

**bash usage**

`bash <script.sh>`

<p align="center">
<img width="410" alt="scripting3" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/scripting3.png">
</p>

**!!! Group Exercise:** Let's work together to execute this script and see what it does.

Make a new directory called `IntroToScripting`
Navigate into `IntroToScripting` (**Hint:** You should see IntroToScripting's path when you type `$ pwd`
Copy and paste the text below into a file called `startProject.sh` in the `IntroToScripting` directory.

```
#!/usr/bin/env bash
 
# Make three subdirectories
mkdir 01_input
mkdir 02_scripts
mkdir 03_output
 
# Start a readme file
touch README.txt
```

Now, let's execute the script with the following command on the command line:


```
$ bash startProject.sh
```

Navigate what just happened. 

### Expanding our code

OK, let's make this a little bit more fancy …

**!!! Jess' demo:** I will demonstrate opening the code in a text editor and amending the script so that it expands on some of its functionality. In the end I'll have this new code (or something close to it):

☟ **This is what it should look like on BBEdit or Notepad++ when you open the file:**

```
#!/usr/bin/env bash
 
# Prompt user for a project name
echo -n "startProject>>> Enter your new project name (no spaces) and press [RETURN]: "
read projectname
 
# Report progress
echo -e "startProject>>> Starting project named $projectname"
 
# Make a project directory and three subdirectories
mkdir $projectname
mkdir $projectname/01_input
mkdir $projectname/02_scripts
mkdir $projectname/03_output
 
# Start a readme file
touch $projectname/README_${projectname}.txt
 
# Add date info to readme file
echo $(date) >> $projectname/README_${projectname}.txt
 
# Report completion
echo "startProject>>> successfully completed"
```

**!!! Group Exercise:**

- Copy the script above into a file called `startProject.sh`
- Execute the script to test it. Note, this time you don't need to make your own project directory. The script will make it for you.

### What did we learn from the demonstration?

**!!! Comment your code !!!** This makes your code readable to other users. Remember *other users* also refers to future-you.

**!!! Testing:** Test your scripts frequently for proper behavior. Even the best programmers test their code every few lines.

**!!! Expansion:** Scripts are often expanded from basic functionality out to more complex functionality. So we are typically writing from a skeletal script to a more “fleshed out” script. Scripts can also be written from top → down. When writing top → down, plan ahead and write out the comments first.

**!!! Isolation:** Sometimes when you are building on the functionality of a script, it makes sense to comment out several blocks of code during the testing phase (also called **debugging** phase). This allows you to isolate just the new changes you are introducing before seeing how they integrate into the complete script.

Continue on to [More scripting - Scripting 2](3-4_Scripting2.md)
