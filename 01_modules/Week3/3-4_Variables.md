# Variables 

**Variables** are placeholders for information. The information can either stay constant throughout the script or change.

All programming languages use variables so if you are learning this concept here for the first time, welcome! You will see this concept again and again as you learn new languages.

Basically, a variable is just a **name** that is given to a **value**. Variables are **assigned** values using the syntax:

```
varname="value"
```

Then, the value can be accessed by typing the variable name after a dollar sign like this - `$varname` or with a fancier syntax like this - `${varname}`. This is called **dereferencing** a variable. For example, we can print out a variable's value using `echo` like so:

```
echo $varname
echo ${varname}
```

**!!! Demonstration:** within the bash script `roomNumbers.sh` we can assign the value “AZ E210” to a variable called `myroom`:

```
#!/usr/bin/env bash
 
myroom="AZ E210"
 
echo $myroom
echo ${myroom}
echo -e "Today's class is being taught in ${myroom}."
```

Then, when we execute `roomNumbers.sh` it should look like this:

```
$ bash roomNumbers.sh
AZ E210
AZ E210
Today's class is being taught in AZ E210.
```

#### How do I come up with good variable names? 

- can only be a string of characters and/or numbers
- cannot have spaces in them
- cannot start with a number
- best practice - do not make them all caps
- think of a name that is meaningful and will help you read the code

**Values** can be individual or multiples (called strings) of letters, numbers, symbols, spaces, special characters, returns, etc. Simple things can be assigned to variables without quotes, but complex things (especially spaces) require quotes. Either double or single quotes can be used but you must be consistent.

**!!! Major pitfall:**
- Use quotes around values that are comprised of characters or strings of characters. Avoid using quotes around numbers
- You cannot put spaces around the equals sign. The variable name and the value must be flush.

```
favoritenumber=42 # this works
favoritenumber = 12 # this doesn't work
favorite number=3 # this doesn't work
 
echo -e "my favorite number is ${favoritenumber}."
```

**!!! Examples:** Here are a few more examples of variable assignments:

```
homeDir="/nas02/home/e/r/erinosb"
favoriteNumber=42
favoriteLetter="E"
```

**!!! Exercise:** Favorite things

Use the code below to assign your favorite things to different variables.

- First! Copy the code below into a file called `favoriteThings.sh` using either nano or a text editor.
- Run the code as is.
- Next, add in the values to all the variables
- Run the code again

**!!! Bonus** - try breaking your code by adding spaces around the equals sign. Then fix it again.

```
#!/usr/bin/env bash
 
#enter your name here
username=
 
#enter your favorite things here. You may need to use quotes for some things.
favoriteOrganism=
 
favoriteShow=
 
favoriteFood=
 
echo "Hi, my name is $username. My favorite organism is $favoriteOrganism. My favorite show is $favoriteShow. I love to eat $favoriteFood."
```

### Variable Reassignment

We can change a variable's associated value within a program. This is called **reassignment**. Say you watch a new show and you now want to update what your favorite show is, like so …

```
#!/usr/bin/env bash
 
#enter your name here
username="Marc Nishimura"
 
#enter your favorite things here. You may need to use quotes for some things.
favoriteOrganism="Arabidopsis"
 
favoriteShow="Breaking Bad"
 
favoriteFood="sushi"
 
echo "Hi, my name is $username. My favorite organism is $favoriteOrganism. My favorite show is $favoriteShow. I love to eat $favoriteFood."
 
#reassigning a new value to a variable 
favoriteShow="Better Call Saul"
 
echo "Hi, my name is $username. My favorite organism is $favoriteOrganism. My favorite show is $favoriteShow. I love to eat $favoriteFood."
```

**!!! Exercise:** Reassign a new value to one of your variables and then copy the same echo statement below that reassignment line of code.

**?** Why are we interested in making variables? Within a bash script, saving information into variables allows you to take in different inputs and execute reproducible commands on that input. Eventually, we will want to do some series of tasks many, many times within a script. This will involve multiple iterations, called looping. Each time we go around a loop, we will change the input values while keeping the commands operating on them the same.

### Capturing output as variables

You can capture the output of a command as a variable like so:

```
$ today=$(date)
 
$ echo $today
```

You can capture the output of a numerical operation as a variable with double parentheses like so:

```
$ mytotal=$((49 + 50))
 
$ echo $mytotal
```

or like so ...

```
$ total1=6
$ total2=5

$ finalTotal=$(($total1 - $total2))
1
```

**!!! Exercise:** modify your `favoriteThings.sh` script to capture the output of a command or numerical operation. Write an echo statement to dereference the variable.

**!!! Advanced skills exercise** modify your `favoriteThings.sh` script to report how many files you have in the current working directory. Print out this information to the user with the following statement:

```
"Hi, my name is Erin. My favorite organism is C. elegans. My favorite show is Better Call Saul. I love to eat ramen.
I have 23 files in my current working directory."
```

<details>
  <summary>Answer here</summary>

---

```
#!/usr/bin/env bash

#enter your name here
username="Jessica Hill"

#enter your favorite things here. You may need to use quotes for some things.
favoriteOrganism="C. elegans"

favoriteShow="Rick and Morty"

favoriteFood="mac n cheese"

echo "Hi, my name is $username. My favorite organism is $favoriteOrganism. My favorite show is $favor$

########

#list all the files in our pwd
# -1 forces output to be one entry per line. This is the default when output is not to a terminal.

filesindir=$(ls -1 | wc -l)

echo "the number of files in my current working directory is:" $filesindir
```

---

</details>

### A few details about math in bash

We can do arithmetic operations in bash scripts using **double parentheses** provided we are working with integers …

| Symbol | Meaning | Example |
|--------|---------|---------|
| + | adding | `myresult=$(( 3 + 5 ))` |
| - | subtracting | `myresult=$(( 5 - 3 ))` |
| * | multiplication | `myresult=$(( 5*3 ))` |
| / | division for integers that divide perfectly | `myresult=$(( 12/3 ))` |
| % | modulo (find the remainder) | `myresult=$(( 11%3 ))` |
| `** or ^` | exponential | `myresult=$(( 10**4 ))` |

**!!! Warning** - these expressions only work with integers. Numbers with decimal points are called **floating point number** in computer science. To do calculations on those, use the built in `bc` application which stands for either **bench calculator** or **basic calculator**.

**bc usage**

`echo “<math expression>” | bc -l`

that's a `-l`, as in little L. This sets scale to **20** and loads an extended math library before running any code.

**!!! Example:**

```
$ echo "11/3" | bc -l
3.66666666666666666666  #this is 20 zeros, see the "scale"

$ echo "9/3" | bc -l
3.00000000000000000000

#vs

$ echo "11/3" | bc
3

$ echo "9/3" | bc
3
```

OR

```
myresult=$(echo "11/3" | bc -l)
echo $myresult
```

You could also use `awk`, `python`, or `R` to work with floating point integers! See below for some examples ...

```
$ echo | awk '{print 10.0 / 3.0}'
3.33333

$ awk 'BEGIN {print 10.0 / 3.0}'

$ python -c 'print(10.0 / 3.0)'
3.3333333333333335
```

see here for how it looks through an interactive session ...

<p align="center">
<img width="700" alt="interactive python session" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/interactivePython.png">
</p>

**!!! Pitfall** The difficulty of doing mathematics using LINUX is a major drawback of LINUX. Other languages that are much more conducive to mathematics are **R** which is built around a statistics framework and Python when used with its many lovely math modules like **NumPy**, **Pandas**, and **MatplotLib**.

If you wanted to try to use `python` or `R` **interactively from the command line** or from a **script**, you could do the following ...

Interactive `python` session example:
```
$ python
>>>

# now you can speak in python!
# type 'exit' to close that interactve session. 
```

Interactive `R` session example:
```
$ R
>

# now you can speak in R!
# type q() to close the interactive session.
```

`python` execution from a script example:
```
#!/bin/bash

# navigate to directory containing python script(s) or execute bash script in same directory as your python script ...
cd /path/to/your/python/scripts

# run python script
python your_script.py

# can also pass arguments to python script
python your_script.py arg1 arg2

# execute a single Python command
python -c 'print("Hello from Python!")'

# excute multi-line python code chunk
python << END_PYTHON_SCRIPT
import sys

def greet():
    print("Hello, World!")
    print("Welcome to Python.")
    print("Have a great day!")

greet()

END_PYTHON_SCRIPT
```

`R` execution from a script example:
```
# test R script ... simple_math.R

result <- 2 + 2
cat("The result is:", result, "\n")
```
```
#!/bin/bash

echo "Running R script..."
Rscript my_script.R
echo "R script finished."


echo "Running R commands directly..."
Rscript -e 'print("This is a direct R command."); x <- 5; y <- 10; print(x * y)'
echo "Direct R commands finished."

# you could also pass arguments to your R script like so in your bash script ...
Rscript my_script_with_args.R "arg1" "123"
```

**!!! Helpful Resource** 

Here's a quick little [bash scripting cheat sheet](https://devhints.io/bash)

Continue on to [Array Variables](3-6_Array_Variables.md)
