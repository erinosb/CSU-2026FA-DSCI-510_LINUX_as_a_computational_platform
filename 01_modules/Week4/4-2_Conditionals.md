# Conditionals 

**Conditionals** are if/else statements that allow us to skip over blocks of code entirely based on passing or failing of a test. The simplest conditionals just involve the command `if`.

### `if`

If statements allow us to modify our code to only execute commands only **IF** a particular test is true. If a particular test is true, a set of actions are performed. If it is not true then don't perform those actions.

**if usage**

```
if [ <some test> ]
then
    <commands>
fi
```

**!!! Example:** Follow along. Imagine asking the user for their age. If they are over 21, let them in the club. Start the code `screenPatrons.sh`

```
#!/usr/bin/env bash
 
# prompt user for their age
echo -e "How old are you?"
 
read age
 
#Conditional statement
if [ $age -ge 21 ]
then
    echo -e "Welcome to the club!"
fi
```

Run your code: 

```
$ bash screenPatrons.sh
```

### The test statement

In an `if` statement, like in this one …

```
if [ <some test> ]
then
    <commands>
fi
```

… getting the test statement correct is a little tricky. The syntax needs to be very perfect.

```
if [ $age -ge 21 ]
```

Don't forget the spaces just inside of the square bracket!

`-ge` in this example is a **conditional operator** that means greater than or equal to

### Conditional Operators: Numbers

| Symbol | Comparison |
|--------| -----------|
| `-eq` | Returns true if two "numbers" are **equal** |
| `-ne` | Returns true if two "numbers" are **not equal** |
| `-lt` | Returns true if a "number" is **less than** another |
| `-le` | Returns true if a "number" is **less than or equal to** another number |
| `-gt` | Returns true if a "number" is **greater than** another number |
| `-ge` | Returns true if a "number" is **greater than or equal to** another number |

Here are some examples:

```
# Prints out a message if the value saved in myvar is less than or equal to 2023
if [ $myvar -le 2023 ]
then
  echo "your number is less than 2023"
fi
 
# Prints out a message if the value saved in myvar is equal to 42
if [ $myvar -eq 42 ]
then
  echo "You guess it! My favorite number is 42"
fi
 
# Prints out a message if the value saved in myvar is not equal to 42
if [ $myvar -ne 42 ]
then
  echo "That's not my favorite number. Keep guessing"
fi
```

For a detailed description of how these are used see: [Ryan's Tutorials: bash if statements](https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php)

**!!! Exercise:** Write a brief script called `numberReader.sh` that asks the user to type in a number. If the number is greater than 100, print out “That's a big number”

**!!! Potential Pitfall:** The following does not work ...

```
# Throws an error and doesn't work
if [$myvar -le 2023]
then
  echo "your number is less than 2023"
fi
```

**!!! Potential Pitfall:** In some situations, conditional statements work better with double square brackets

```
[[ if statement here ]] 
```

[More about single vs double square brackets](https://www.baeldung.com/linux/bash-single-vs-double-brackets#:~:text=The%20single%20bracket%20is%20a,brackets%20is%20generally%20more%20convenient.)

### `if/else`

Try running your `screenPatrons.sh` script again but now type in a number that is less than 21. Hmmm, it's not very satisfying. **if/else** statements can help with that. If the test is true, you can execute one block of code. If the test is false, you can execute a different block:

**if else Usage**

```
if [ <some test> ]
then
    <commands>
else
    <commands>
fi
```

Lets try it out ...

```
#!/usr/bin/env bash
 
# prompt user for their age
echo -e "How old are you?"
 
read age
 
#Conditional statement
if [ $age -ge 21 ]
then
    echo -e "Welcome to the club!"
else
    echo -e "Scram, kid!"
fi
```

**!!! Exercise:** Save this script. Run your script again and test it using a variety of ages.

- [more about single versus double square brackets](https://www.baeldung.com/linux/bash-single-vs-double-brackets#:~:text=The%20single%20bracket%20is%20a,brackets%20is%20generally%20more%20convenient.)
- This reference also has more details on **regular expressions**
- This reference has details on **Boolean** searches (`AND` and `OR`).

### `if/elif/else`

This can get more complex, and in the interest of time, we're going to skip over this section. I'll include it here for those who wish to learn on their own.

<p align="center">
<img width="410" alt="ifelifelse" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/if_elif_else.jpg">
</p>

Conditionals can get more complex by adding elif which can add more test criteria.

```
if [ <some test> ]
then
    <commands>
elif [ <some different test> ]
then
    <different commands>
else
    <different commands>
fi
```

**!!! Example:**

```
#!/usr/bin/env bash
 
# prompt user for their age
echo -e "How old are you?"
 
read age
 
#Conditional statement
 
echo -e "How old are you?"
 
read age
 
# If age is greater than 21 and less than 65
if [ $age -ge 21 ] && [ $age -lt 65 ]
then
    echo -e "Welcome to the club!"
 
# If age is greater or equal to 65
elif [ $age -ge 65 ] 
then
    echo -e "Welcome to the club! You get a senior discount!"
 
# If neither of the above tests are true    
else 
    echo -e "Scram, kid!"
fi
```

### Conditional Operators: Strings

We learned how to use conditional comparison statements on numbers. What about on strings (aka - words)?

| Symbol | Comparison |
|--------| -----------|
| `==` | Returns true if two "strings" are **equivalent** |
| `!=` | Returns true if two "strings" are **not equivalent** |
| `!` | General - Returns true if the expression is false |

**Potential Pitfall** - if your variable contains spaces, use double square brackets ...

```
[[ if statement here ]] 
```

**!!! Examples:**

```
myname="Harry Potter"
if [[ $myname == "Harry Potter" ]]
then
   echo -e "Griffindor"
fi
```

**!!! Exercise:** Add onto your `screenPatrons.sh` script to ask the user what state they live in. If they match “Colorado”, print out a message that states that they get a local's discount!

### Conditional Operators: Files & Directories

We learned how to use conditional comparison statements on numbers and strings. What about if we want to use a conditional statement to test whether a file or directory exists and some aspects of its properties (this may not make a ton of sense because we haven't covered permissions yet).

| Symbol | Comparison |
|--------| -----------|
| `-d` | Check the existence of a directory |
| `-e` | Check the existence of a file |
| `$# -gt 0` | Check that the number of arguments the user has provided is greater than 0 |
| `$# -eq 2` | Check that the number of arguments the user has provided is equal to 2 |

**!!! Example:** Test if the file called `file.txt` exists. If it does, count its lines, words, & characters

```
myfile="file.txt"
if [ -e $myfile ]
then
   wc $myfile
fi
```

**!!! Challenge Exercise:** Recall how we can pass an argument into our script as input like so …

```
$ bash countingLines.sh file1.txt
```

And then within the script, we can capture the argument like this …

```
# capture the first argument in a variable called myfirstfile
myfirstfile=$1
 
# use a sub-string substitution line to create a new variable called myoutputfile in which .txt is substituted for _linecount.txt
myoutputfile=${myfirstfile/%.txt/_linecount.txt}
 
# operate on the input file and save the line count to the desired output file
wc -l $myfirstfile > $myoutputfile
```

**!!! Exercise:** Your mission is to expand your script called `countingLines.sh` so that the script checks that a file was given. This script should contain a conditional statement that tests whether the user properly supplied a file as an argument. If the user has supplied a file, report what was supplied. If the user did not supply the file, tell the user they must try again and next time supply an argument.

- You can use the command `exit` to stop your script at any point. This is useful if you find that the argument requirement has not been satisfied.
- Keep in mind - This is a challenging exercise. If you're not getting it, that's ok. If the script isn't behaving how you predict, you're not crazy. I don't know why these steps aren't more intuitive.
- [Checking Arguments Reference](https://www.networkworld.com/article/972112/verifying-bash-script-arguments.html#:~:text=Checking%20the%20number%20of%20arguments%20provided&text=The%20%3D%3D%20(equals)%2C%20lt,the%20person%20running%20the%20script)
- There are many ways to do this, here is one way ...

<details>
  <summary>Answer</summary>

```
#!/usr/bin/env bash
 
# Test that there is at least one argument passed - that the number of arguments is greater than 0
if [ $# -gt 0 ]
then
 echo "Your input file is $1"
else
 echo "Please supply a valid text input file as an argument"
 exit
fi
 
# Test that the argument passed corresponds to a real file in the working directory
if [ -e $1 ]
then
 echo "Your input file is $1"
else
 echo "Please supply a valid text input file"
 exit
fi
 
# capture the first argument in a variable called myfirstfile
myfirstfile=$1
 
# use a sub-string substitution line to create a new variable called myoutputfile in which .txt is substituted for _linecount.txt
myoutputfile=${myfirstfile/%.txt/_linecount.txt}
 
# operate on the input file and save the line count to the desired output file
wc -l $myfirstfile > $myoutputfile
```

</details>

**!!! Resource:** Check out [Ryan's Tutorials](https://ryanstutorials.net/) on bash scripting. There are some nice descriptions of conditionals and loops.
- Ryan's tutorials gives some good demonstrations of **boolean conditionals** - match THIS OR THAT, or match THIS AND THAT.

Continue on to [Loops](4-3_Loops.md)
