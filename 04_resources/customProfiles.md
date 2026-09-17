# Custom Profiles


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
