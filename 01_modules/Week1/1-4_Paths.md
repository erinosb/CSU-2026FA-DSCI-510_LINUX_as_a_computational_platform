
# Paths

### Todays objectives: 

<details>
  <summary>Click to expand/collapse</summary>

---

- **Vocabulary**
  - Options
  - Manuals
  - Source (as in the source file in a copy cp command)
  - Target (as in the target file in a copy cp command)
  - Wildcards

- **Things you should know how to do after this class**
  - Know the difference between “command”, “argument” and “options” and be able to identify them
  - Realize you can glob options together (-a -l -s is the same as -als for most command options)
  - Be comfortable navigating manuals and knowing they are available as a help resource
  - Know how to make and remove directories
  - Know how to create files with touch or nano
  - Be comfortable navigating nano and using it to make changes to files
  - Know how to safely remove files and directories using rm
  - Peek into files using more and less and head and tail
  - Be comfortable using cp to copy files or directories in a few different ways (new file in the same directory, in a different directory, or with a new name)
  - Be comfortable using mv to move files and directories in different ways. Know the difference between cp and mv.
  - Know how to use wildcards * and ?
  - Know how to get help using man, help, command -h, or command --help

- **Commands covered**
  - `ls` with commands
  - `man <command>`
  - `mkdir`
  - `rmdir`
  - `touch <filename>`
  - `nano <filename>`
  - `rm`
  - `more`
  - `less`
  - `cp`
  - `mv`
  - `*`
  - `?`
  - `.`
  - `head`

---

</details>

### Reminder: 

- Assignments 1 & 2 → submit on canvas, **DUE September 2nd by midnight**
- This course is short and should be a springboard to more learning such as:
  - [Boulder Computing Training Series](https://www.colorado.edu/crdds/events#research_computing-89)
  - [Coding & Cookies](https://libguides.colostate.edu/coding-cookies/home) in the Morgan Library at CSU
    - [Upcoming workshops](https://libguides.colostate.edu/coding-cookies)

### Test your understanding - take this quiz!

[quiz 1](https://forms.gle/uMGb4qe14pmZKegu7)

### Moving around: absolute paths v. relative paths

The types of paths we've used for navigating up to this point are called **relative paths**. This means that they only make sense from the perspective of the current working directory. In contrast, we can use `cd` to take us to **absolute paths** that would make sense anywhere on the computer system. **Absolute paths** always begin with the root directory, `/`. When we execute `pwd`, the shell spits out our current working directory as an absolute path because it start with a `/` such as `/Users/jessicahill/`.

**!!! Vocabulary**: 
- **Absolute path:** The exact, full address of a file or directory starting from the root `/`. The absolute path always starts with a forward slash. An example of navigating using an absolute path would be `cd /home/martha/dogstuff`
- **Relative path:** The location of a file or directory that only makes sense in the context of a given working directory. Examples of navigating using a relative path would be `cd subdirectory` or `cd ..`

**!!! Example**: Changing directory using an **absolute path:**

```
$ cd /home/users/sally/documents
```
**!!! Example**: Changing directory using an **relative path:**
```
$ ls 
dropbox  documents  pictures  music
$ cd music
```

**!!! Exercise**: Open your Finder/Explorer and navigate to some directory on your computer where you keep a piece of data you've recently gathered. Look at the path bar to get a sense of where this directory is located. Now, using the terminal, try to change into this directory using an absolute path as the argument for a cd command. Use **TAB** to autocomplete to save time and improve accuracy.

**!!! Quick tip**: When moving up or down a directory structure using relative paths, you don't need to jump down each directory one at a time. You can double up your jumps using a `/` between directories. For example, if you are in `/Users/Name/` and you want to be in `/Users/Name/Documents/Labwork/`, try:

```
$ pwd
/Users/Name
$ cd Documents
$ cd Labwork
```

OR

```
$ pwd
/Users/Name
$ cd Documents/Labwork
$ pwd
/Users/Name/Documents/Labwork/
```

**!!! Quick tip**: We have used `ls` to list the contents of our current working directory. If no argument is specified `ls` defaults to listing the contents of the current working directory. We can also specify the name of the directory whose contents we want to list as an argument … even if we are not in that directory! We can use either an absolute or relative path for this …

```
$ ls 
Homework Labwork Servicework
$ ls Servicework
application1.docx report1.docx report2.docx
$ ls /home/users/sandra/sheetmusic
eight_polonaises.pdf hungarian_dance_no5.pdf six_variations.pdf 
```

### Shortcuts

**TAB** - autocomplete

**CTRL+u** - erase the current line

**CTRL+l** - (that's a lower case “L”), clear the terminal screen

**CTRL+a** - go to the beginning of the line

**CTRL+e** - to go the end of the line

**CTRL+c** - cancel out of a program or command that is being executed

**CTRL+d** - log out of the terminal

**UP arrow** - print out the last command executed (even if it failed).

**q** - to come out of the man page session

Continue on to [Options](1-5_Options.md)
