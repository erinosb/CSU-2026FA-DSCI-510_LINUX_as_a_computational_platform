# A little more detail about bash terminology

What is **shell scripting**? We are doing shell scripting because this scripts will be read and executed by the shell. When we use the bash shell it's called **bash scripting**. bash is typically the default shell program on most all LINUX operating systems and installations. Didn't know we had more than one shell? It's true. Most LINUX or mac operating systems come with a few different versions of the shell under the hood. In fact, MAC has now switched to the zsh shell which is an extended version of bash with some improvements.

| Name | Name | Year | Developed by | Notes |
|------|------|------|--------------|-------|
| sh | the Thompson Shell | 1971 | Ken Thompson | The origional shell | 
| sh | The Bourne Shell | 1979 | Stephen Bourne | intended as both command line & scripting language |
| bash | the Bourne Again Shell (bash) | 1989 | Brian Fox & the GNU project | default LINUX shell |
| zsh | Z shell | 1990 | Paul Falstad who named it after a Yale TA Zhong Shao | now the default Mac shell |

Note - even though you may not technically be using the **bash** shell, it's still referred to as bash scripting just by habit.

### Reviewing scripting

We will be writing scripts within text editors.

Scripts can be executed on the command line in a variety of ways.

For example, the script `HelloWorld.sh` will look like this:

```
#!/usr/bin/env bash
 
echo "Hello World!"
```

And is executed by calling it on the command line (from within its working directory) as:

```
$ bash HelloWorld.sh
```

Some things to remember:

- Scripts start with a shebang
- Scripts can contain any lines of code that work on the command line
- It is good practice to comment your code. That means, write notes in your code using #
- It is good practice to only write 1 - 2 lines of code at a time and test it in between

[A fun article on why all programming students learn Hello World first](https://slate.com/technology/2019/10/hello-world-history-programming.html#:~:text=Before%20long%2C%20writers%20of%20tutorial,you'd%20enjoy%20the%20syntax.)

### Echo Statements

Echo statements let us print text out to the screen. Like all LINUX commands, they can be used on the command line or within a script:

```
$ echo "hello world"
hello world
```

Echo statement options:

**echo usage:**

`echo [options] “statement”`

`-n` omit trailing carriage return

`-e` allow special character interpretations. “\n” will be interpreted as a return. “\t” will be interpreted as a tab

**!!! Exercise:** Write a script called `balrog.sh`. Write a series of echo statements. Try using -e and -n to test how things work:

**!!! Example:** The script below is `balrog.sh`

```
#!/usr/bin/env bash
 
# Affirmations for Grad Students
echo "The dark fire will not avail you!"
echo "Go back to the Shadow"
echo -n "You shall not"
echo -n "pass"
 
echo -e "\n\n"
 
echo -e "Go back to the Shadow \t\t You shall not \t pass."
```

It spits out the following: 

```
$ bash balrog.sh  
The dark fire will not avail you!
Go back to the Shadow
You shallnotpass


Go back to the Shadow 		 You shall not 	 pass.
```

### Commenting Out 

You can gently ask the computer to ignore lines of code by adding a pound sign in front of it. This is **called commenting out** your code.

```
#!/usr/bin/env bash
 
echo "Hello World!"
echo "My name is Marvin"
#echo "and I am having a rather boring day"
#echo "In fact, all my days are rather boring"
#echo "Maybe I can share stories of my life with you to pass the time?"
```

**!!! Super Useful:** Commenting out lines of code is super useful when you are trying to find a bug in your code. For example, you can comment out all the lines of code and then add lines back in one at a time to determine where the error lies.

Continue on to [Variables](3-5_Variables.md)
