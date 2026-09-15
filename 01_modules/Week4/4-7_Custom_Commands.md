# User-specified Custom Commands

Where should I store my scripts?

- It depends on the project.
- For many **small, specific bash scripts**, you can keep them in the same directory as the project they were designed for.
  - This makes a lot of sense for scripts that are designed for one specific task like cleaning up a specific dataset or filtering through some input data.
- For **larger, analytical scripts**, like data analysis that will be published, consider using [git hub](https://github.com/) as a repository for all your scripts.
  - This is a best practice for reproducible data
  - For training: [coding and cookies](https://libguides.colostate.edu/coding-cookies/home)
  - For training: [Github at Boulder](https://calendar.colorado.edu/event/git-github-in-depth-an-rc-short-course) - Friday October 17th, 2025 from 10 am to 12 pm
- What about **generally useful scripts** that you want to use over and over again?
  - For these, we will want to build them into our own **user-specified custom commands**!

### Steps for building custom commands

1. Add the `bin` directory to your `$PATH`
2. Put script in `bin` directory
3. Make script executable
4. Take the `.sh` off the script name

Currently, we can execute our shell script two ways …
1. Within the **same directory** as the program

```
$ bash script.sh
```

2. From **anywhere** in our computer using an absolute path

```
$ bash /Users/name/dir1/dir2/script.sh
```

However, once we turn our scripts into **custom commands** we can turn our scripts into programs that more closely resemble real **commands**!

```
$ script
```

Recall our original script `startProject.sh`. Let's try transforming this into a custom command on ALPINE.

1. Add the `bin` directory to your `$PATH`
2. Put script in `bin` directory
3. Make script executable
4. Take the `.sh` off the script name

#### 1. Add the `bin` directory to your `$PATH`

Do you already have a `bin` directory in your projects directory on ALPINE?

- Check it
- Go to `/projects/<user>`
- Use the `ls` to see if there is a directory called `bin`
- Make this directory if you don't have it already

Recall that one of our environmental variables was called PATH:

```
$ echo $PATH
```

Your **PATH** is a list of directories where **executable binaries** (aka software) are stored. Each time you execute a command on the terminal or in a script, the shell searches for a script associated with that command name. It searches through each directory listed in the PATH. If the shell cannot find a script associated with that command name in any of those places, it cannot execute the command.

**!!! WARNING:*** You do not want to mess with most of the directories listed in your PATH. They are fundamental to how your installation of LINUX runs.

**!!! COOL TRICK:** However, you can ADD a personal directory to your PATH. The shell will search through this personal directory last. By placing script files in that directory, you can execute them from anywhere in your file structure.

We add to our path by modifying one of our hidden customization files called `.bash_profile`.

- First, navigate to your **home** directory where the `.bash_profile` file is stored.

```
$ cd
$ ls -alh
```

- Next, let's make a backup of your `.bash_profile`

```
$ cp .bash_profile 250918_bash_profile_backup.txt
```

- Now, edit your original `.bash_profile` by opening it in the FILES navigator window.
- Copy and paste the following to the `.bash_profile` file at the end …

```
#Append paths
export PATH="/projects/<jesshill@colostate.edu>/bin:$PATH"
export PATH
```

- Replace jesshill@colostate.edu with youreID@colostate.edu. Remove the greater than and less than sign ... 

```
#Append paths
export PATH="/projects/<eID@colostate.edu>/bin:$PATH"
export PATH
```

You will need to restart the terminal/shell for this to work.

- Close out the terminal.
- Start a new terminal.
- Test it:

```
$ echo $PATH
```

**!!! Warning:** Be very careful modifying your PATH. Make a backup of your startup files before modifying them. If something goes amiss, you can then revert to the previous startup file.

Cool! What else can I do in my `.bash_profile`?

<details>
  <summary>Quick PATH modifications</summary>

---

**example .bash_profile modifications**

```
# Change colors so they look cooler:
export CLICOLOR=1
export LSCOLORS=GxFxBxDxGxegedabagacad
 
# My prompt: 
# Change the color of the prompt: 
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
# Make my prompt shorter - good for teaching:
PS1='\u:\W\$ '
 
# My aliases
alias srm='rm -i'
```

More references here:
- [Guide to editing the prompt](https://phoenixnap.com/kb/change-bash-prompt-linux)
- [How to change colors](https://www.howtogeek.com/307899/how-to-change-the-colors-of-directories-and-files-in-the-ls-command/)
  - Note: the variable is LSCOLORS on Alpine, not LS_COLORS as in their tutorial

---

</details>

<details>
  <summary>Edit your .bash_profile</summary>

---

**!!! Warning:** Be very careful modifying your PATH. Make a backup of your startup files before modifying them. If something goes amiss, you can then revert to the previous startup file.

Update $PATH environmental variable …
- Navigate to home directory using `$ cd`
- See if there is already a file called `.bash_profile`
  - If one already exists, make a backup of it using `$ cp .bash_profile bash_profile_backup.txt`
  - If it doesnt exist, make one using `$ touch .bash_profile`
- Edit the bash profile to inlcude the name of your new scripts path. For example: `Users/jesshill/myscripts`

```
export PATH="/Users/jesshill/myscripts:$PATH"
```

- for yours, if your path (use pwd to check) is <mypath>, put it in here where <mypath> is the absolute path of your scripts directory.

```
export PATH="<mypath>:$PATH"
```

To enact the changes, either close and re-open the terminal OR type:

```
$ source .bash_profile
```

**!!! Warning:** 
- Please be very careful with this. You can really alter your computer's behavior this way. Test this out on ALPINE first before you try this on your own laptop.
- Before changing your `.bash_profile`, make a backup.
- If you have run into some trouble doing this, just delete the `.bash_profile` file and re-start the terminal. Or, revert to a backed up `.bash_profile` and re-start the terminal.

** Other fun things you can do with .bash_profile**

The `.bash_profile` file executes every time you open a new terminal window. So, you can put lots of cool stuff in here like your alias commands. You can also customize the colors of your terminal.

```
# My custom paths
export PATH="<mypath>:$PATH"
 
# My alias commands:
alias srm='rm -i'
 
# Change my colors so they look cooler:
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
```

---

</details>

<details>
  <summary>Using variables in your environment</summary>

---
  
**Changing settings in your environment**

Now that we've had practice with variables, and seen some environmental variables, let's explore how `ls` uses an environmental variable to color its output.

Maybe you already have it, to check, do:

```
printenv | grep COLOR
```

Does anyone have any output from this?

If you already do, then it's being set somewhere, which is fine. This next lesson will show you how to configure it.

**Background**

On linux, doing `ls –color` tells ls to look at the environmental variable `LS_COLORS` for settings on how to color directories, links, executable files, and other more advanced types of files.

On BSD (Macs), `ls -G` does the same, but it looks for the variable `LSCOLORS`.

Usually, these flags are supplied in the alias. Do:

```
alias ls
```

to see if you have the flag set. If not, do:

```
# linux (Windows Ubuntu)
alias ls='ls --color'
 
# BSD (Mac Terminal)
alias ls='ls -G'
```

This insures that `ls` will color its output, and is probably already set for you. If you like how it colors its output already, that's OK, we're just tinkering for now.

**Syntax of `LSCOLORS/LS_COLORS`**

This has to be a value of a variable, so it will be a long string, which means a lot of abbreviation.

Example: `LSCOLORS=Exfxcxdxbxeggaabagacad`

Example: `di=1;34:ln=35:so=32:pi=33:ex=31:bd=34;46:cd=36;40:su=30;41:sg=30;46:tw=30;42:ow=30;43`

This is hard (or time consuming) to deal with, so let's use a utility to generate the code.

**Exercise**

go to [Geoff Greer](https://geoff.greer.fm/lscolors/) to see how the settings change with different highlights.

<p align="center">
<img width="410" alt="lscolors tool" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/lscolor_webtool.png">
</p>

**Syntax**

BSD: 
```
# BSD
LSCOLORS=CODE
# example
LSCOLORS=exfxcxdxbxegedabagacad
 
export LSCOLORS # only has to happen once
 
# Linux:
LS_COLORS='CODE IN QUOTES'
# example
LS_COLORS='di=34:ln=35:so=32:pi=33:ex=31:bd=34;46:cd=34;43:su=30;41:sg=30;46:tw=30;42:ow=30;43'
 
export LS_COLORS # only has to happen once
```

**Try it!**

1. Change the foreground color of directories,
2. paste in the new code using the syntax above.
3. use `ls` in your home directory to test it out
4. Try changing the background color of the “directory"

**Other file types - for the curious**

If you want to test the display of other file types, you have to look in system directories.
- /dev should have symbolic links, and character and block special files
- /bin /usr/sbin, some have the set-uid/set-gid

**Saving changes to your environment**

Everything is saved in configuration files or scripts, and executed when you login, or open a new terminal.

Let's make a new configuration file called `colors.rc` (.rc is a convention for config file extensions).

```
$ nano colors.rc
```

1. Set the value of LSCOLORS or LS_COLORS in the file, as you did in the terminal.
2. You **do** need to export the variable again. `export LSCOLORS`
3. Almost there - colors.rc has to be `sourced` during login.
4. `source colors.rc` must be placed at the very bottom of your login startup file:
  - bash: `.bash_profile`
  - zsh: `.zshrc`
  - Create the file if it doesn't exist.
5. Open a new terminal window (ctrl-alt-t Windows) (command-t Mac) and see if the list colors are defined.

---

</details>


Recall our steps:

1. Add the `bin` directory to your `$PATH`
2. Put script in `bin` directory
3. Make script executable
4. Take the `.sh` off the script name

#### 2. Put script in `bin` directory

The proper place to put short user command scripts on ALPINE is in our projects directory.

- Navigate to your PROJECTS directory.
  - You can do this through the FILES menu
  - OR, you can do this through the shell (cd, etc)

<p align="center">
<img width="410" alt="files menue" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/fileNavigation.png">
</p>

- Next, create a directory called bin if one doesn't already exist.
Do this by clicking the **New Directory** button like so …

<p align="center">
<img width="410" alt="newdir" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/newdir.png">
</p>

- Navigate into `/projects/<yourname>/bin`
- Start a new script called `startProject.sh` using the **New File** button
- Edit the `startProject.sh` file by clicking on its menu of three vertical dots.
- Select **Edit** like so …

<p align="center">
<img width="410" alt="edit file" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/editfile.png">
</p>

Let's go ahead and put this script on ALPINE.

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

Let's test whether our script works.

- Open a cluster by selecting **Clusters** menu
- Select **>ALPINE Shell Access**
- Navigate to `/projects/<user>/bin`
- test code

```
$ bash startProject.sh
```

These were our steps ...

1. Add the `bin` directory to your `$PATH`
2. Put script in a `bin` directory
3. Make script executable
4. Take the `.sh` off the script name

OK, we've written the script. Now let's make it executable.

#### 3. Make script executable

<details>
  <summary>Bonus Content: Permissions</summary>

---

### Permissions

#### User types

Unix/Linux are designed as multi-user systems and it provides mechanisms for managing that. One aspect of that is that file ownership. Every file and directory has an owner. The **owner** of a file/directory can control who has what type of access to it. The other users can belong to another **group** or the rest of the **world**. Three user types:

- **owner**
- **group**
- **world**

#### Permission types

We can specify what different users have permission to do to a file or directory. These privileges are:

- **read** - read privileges mean that users can open a file and read it, but cannot make changes.
- **write** - write privileges allow a user to make changes to it.
- **execute** - execution privileges allow a user to execute a code, script, or program.

#### Checking permissions with `ls -l`

Permission codes are displayed for files and directories using `ls -l`:

```
erinnish@cray2:~/lustrefs> ls -alh
total 56K
drwxr-----   6 erinnish onishlab 4.0K Feb 29  2016 .
drwxr--r-- 625 root     root      36K Jul 26 15:37 ..
drwxr--r--   2 erinnish onishlab 4.0K Feb 22  2016 1_EXECUTABLES
drwxr--r--   3 erinnish onishlab 4.0K Feb 28  2016 2_RAWFILES
drwxr--r--   4 erinnish onishlab 4.0K Apr 25 11:56 3_PROJECTS
drwxr--r--   4 erinnish onishlab 4.0K Mar  4 09:53 4_SEQUENCES
```

The codes `drwxrwxrwx` stand for directory, read, write, execute, read, write, execute, read, write, execute. Disregarding the **d** for directory, the first set of permissions refer to what the **user** can do, the second to what the **group** can do, and the third to what the **others** can do.

If the letter `w`, `r`, or `x` is present, it meant that user has that permission. A `-` represents a permission that is **NOT** granted.

#### Changing permissions with chmod

If I want to change the permissions of a file or directory in my file structure, I can do so with chmod.

**chmod Usage:** 

`chmod [nnn] <file.txt/dir> …`

[nnn] - where nnn is a three number code specifying the desired permission string.

The three number code string is a clever way to specify the permissions for the **owner, group, and world**. If I want all three user groups to have read, write, and execution privileges, the code string is 777:

**!!! EXAMPLES:** To change a file to this permission code …

<p align="center">
<img width="410" alt="permissions777" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/permissions777.png">
</p>

… we would type:

```
$ chmod 777 file.txt
```

Another example:

<p align="center">
<img width="410" alt="permissions764" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/permissions764.png">
</p>

```
$ chmod 764 file.txt
```

And another:

<p align="center">
<img width="410" alt="permissions740" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/permissions740.png">
</p>

```
$ chmod 740 file.txt
```

**!!! Exercise:** To explore aspects of chmod, let's use a program that is executable. Make a file called `hello_user.sh`. Copy and paste the following content into this file.

```
#!/bin/bash
 
#Prompt for name:
echo "What is your name?"
 
# get name from stdin. Call it varname
read varname
 
#say hello
echo "Why hello there, $varname!"
```

Let's see if we can execute this code:

```
$ls -alh # check the current permissions for hello_user.sh
$bash hello_user.sh # Try to execute the code explicitly
$./hello_user.sh # Try to execute the code with executable permissions
```

Did it work? Probably not if you don't have executable permissions. Let's change the permissions.

```
$chmod 744 hello_user.sh #change permissions to owner executable
$./hello_user.sh
```

Did it work?

**!!! Quick tip:** 
- If it didn't work, don't fret. It is possible your system does not store its bash program in /bin/bash. To check this, type which $SHELL. Replace whatever is displayed to the screen within the code in place of `/bin/bash`. Try again.
- There are many more ways of executing chmod. Some of these are very intuitive and may be easier to learn. Please read Chapter9 of the text book to see these alternative techniques.

You can also use **alphabetic change codes**! There are many allowable syntaxes for changecodes.

```
chmod u+x file.sh #allow the user/owner to execute file.sh
$ chmod u-x file.sh #remove permission for user/owner to execute file.sh
$ chmod g+wx file.sh #allow the group to write and execute file.sh
$ chmod g-wx file.sh # remove permission for group to execute file.sh
$ chmod o+rwx file.sh #allow others to read, write and execute file.sh
$ chmod o-rwx file.sh # remove permission for others to read, write, and execute file.sh
```

---

</details>

Please see the reference links above for more information.

For this exercise, we will make our script executable by using the command `chmod` and the options <u+x>. This will make a script executable (x) to the User (that's you, u).

Give it a try …

```
$ ls -alh
$ chmod u+x startProject.sh
$ ls -alh
```

**!!! Exercise:** Test whether the file is executable by running it like so …

```
$ startProject.sh
```

Yay! Now we don't need to use the `bash` command to execute the `startProject.sh` script. We can just execute it by either 1) going to the directory where the script lives and typing `startProject.sh`.

Because this script is in our special `bin` directory that lives in our path, we can use it ANYWHERE in our file structure and execute this script. Try it from your home directory …

```
$ cd
$ startProject.sh
```

Remember, our steps to calling the script anywhere in our computer were:

Add the `bin` directory to our `$PATH`
Put script in a `bin` directory
Make script executable
Take the `.sh` off the script name

#### 4. Take the `.sh` of the script name

The last step is …

```
$ mv startProject.sh startProject
```

And that's it!

You made a brand new command! You can execute it anywhere in ALPINE using:

```
$ startProject
```

HOORAY!!!

**!!! NEXT TIME** you want to make a custom command, you'll only need to do steps 1 - 3. Because you modified your path within .bash_profile, that is permanent. You won't need to do that step again.

**!!! BEST PRACTICE:** Put all your custom commands in the same place so you can easily find their names and modify them as need be.

**!!! BONUS CONTENT:** Learn how to add options and help pages to your custom commands using `getopt` or `getopts`:
- [Make options and help using getopt(s)](https://www.geeksforgeeks.org/linux-unix/getopts-command-in-linux-with-examples/)

**!!! RUNNING JOBS ON ALPINE:** startProjects is a little script. It only takes a minuscule amount of compute power and speed. ALPINE people are ok with us running a command like this on the login, compile, or compute nodes immediately. However, anything bigger will require that you ask formally for resources and get in line (get in a queue). Please learn how to do this by attending their workshops or taking DSCI512: RNA sequencing. Or, you can continue on to the next pages. Enjoy!

Continue on to [Running jobs on Alpine](4-7_Running_jobs_on_Alpine.md)
