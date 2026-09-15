# Loops

Loops let us cycle over a given block of code over and over again. In other words, executing the code will be iterative. A nice feature of loops is that each pass around the loop can execute the code in a slightly different way.

Types of loops. In LINUX, and in most programming languages, there are several commands that can be used to execute a loop-type flow.
- `for`
- `while`
- `until`
- `select`

For this lesson, we will learn:
- `for` loops - easy
- `while` loops - intermediate
- `while read line` loops - intermediate
- Tips & Tricks
- Looping over arguments

### `for` loops - easy

**!!! Warning** - Stuck in a loop? If you are stuck in an infinite loop, press `CTRL + C` 

The easiest loop in LINUX is a `for` loop that cycles over each element of an array variable. Before we get started, let's review array variables. Remember, array variables contain ordered elements. They are assigned like so …

```
houses=(Gryffindor Slytherin Ravenclaw Hufflepuff)
```

… and they are dereferenced like so …

```
echo -e ${houses[@]}
#or
echo -e ${houses[*]}
```

If we want to one-by-one, go through each element of an array and do something with that element, we can use a for loop. Here is the syntax:

**for usage - Python style**

```
for <var> in ${<array>[@]}
do
    <commands>
done
```

In this type of loop `for` is a command that is typed literally. `in`, `do`, and `done` are also commands that are typed literally. `array` is a variable that has already been defined elsewhere in your code. And `var` is a variable name you will choose. For each iteration of the loop, the variable `var` will store an individual element from the array as its value.

The first time around the loop `var` will represent the first element in the array. The second time around the loop, `var` will represent the second element. And so on.

What commands go inside the loop? Anything you want, really. I do recommend testing how your loop works first using an echo statement within it that dereferences `$var`. This will be helpful to ensure that everything is working properly.

**!!! Exercise:** Let's try this together. Let's make a Hogwarts houses array. Let's start giving some points to different houses using a script `givePoints.sh`. Start `givePoints.sh` and make it executable. Next, copy in the following code:

```
#!/usr/bin/env bash
 
#assign hogwarts houses to the array variable called houses
houses=(Gryffindor Slytherin Ravenclaw Hufflepuff)
 
# each element in the array variable houses will be sequentially accessed as the variable $housename
for housevar in ${houses[@]}
do
    echo -e "Ten points for $housevar"
 
done
```

Test it out! What happened?

**!!! Independent Exercise:** Try it out yourself.
- Write a script called `cycleNames.sh`
- Create an array variable called `labgroup` that includes all the members of your lab (or family or friend-group)
- Use a simple `for` loop to cycle over each person in `labgroup` and repeat a simple echo statement such as `“Hello, $member”` or `“$member, it's your turn for lab meeting”`.

### `while` loops

`while` loops are loops that test a conditional at each iteration of the loop. If the conditional statement is true, the code block is executed. If the condition is false, the loop stops.

**while usage**

```
while [ <some test> ]
do
    <commands>
done
```

Similar to what we learned in the `for` loops, the words `while`, `do`, and `done` must be literally written. The [ <some test > ] section is going to adhere to the rules and conventions we saw in the conditional section. And the commands can be anything we wish.

To achieve the proper behavior, our while loop will need three major components:

1. INITIALIZATION - where we start counter variable (i = 0)
2. CONDITION - where we check if our counter variable satisfies some conditional criteria (less than #, greater than #); and
3. INCREMENTALIZATION - where we reassign our counter by adding or subtracting 1 to/from it.

**!!! Example:** here is a loop that counts from 1 to 5. Let's call it `simpleCounter.sh`

```
#!/usr/bin/env bash
 
# INITIALIZATION of the counter variable x setting it to 1
x=1
 
# CONDITION - check whether x is less than or equal to 5? If TRUE - do a loop. If FALSE - go to the next code block.
while [ $x -le 5 ]
do
 
  echo "In this round of the loop x is equal to $x"
 
  #INCREMENTALIZATION - Add 1 to x
  x=$(( $x + 1 ))
 
done
 
echo "The code is complete"
```

We can also use while loops to access content within an array variable but it can be a little tricky …

```
#!/usr/bin/env bash
 
# INITIALIZATION of the counter variable x setting it to 1
x=1
 
# CONDITION - check whether x is less than or equal to the number of elements in the houses array? If TRUE - do a loop. If FALSE - go to the next code block.
while [ $x -le ${#houses[@]} ]
do
 
  echo "In this round of the loop x is equal to $x"
 
  echo "ten points to ${houses[$x]}"
 
  #INCREMENTALIZATION - Add 1 to x
  x=$(( $x + 1 ))  
 
done
```

OK, that's weird. It looks like it started accessing the second element, Slytherin, first. Why?

You'll recall that array variables start their counting on the number **0**. For this reason, we'll need to modify our code and start the iteration variable on 0. We'll also need to change the conditional -le (less than or equal to) to -lt (less than). If we don't do this, the loop will cycle too many times. Note, I also changed the comments, too.

```
houses=(Gryffindor Slytherin Ravenclaw Hufflepuff)
 
# INITIALIZATION of the counter variable x setting it to 0
y=0
 
# CONDITION - Is x is less than the number of elements the number of elements in the houses array? If TRUE - do a loop. If FALSE - go to the next code block.
while [ $y -lt ${#houses[@]} ]
do
 
  echo "In this round of the loop x is equal to $y"
 
  echo "ten points to ${houses[$y]}"
 
  #INCREMENTALIZATION - Add 1 to y
  y=$(( $y + 1 )) 
 
done
```

**!!! Tip:** Incrementing numeric variables using x++

if we have a numeric variable called x that is assigned the value 0, we can add one to this variable each time we go around the loop with the following x++ syntax …

```
x=0
 
while [ $x -le 5 ]
do
  echo "x is equal to $x"
 
  ((x++))     # Means the same as x=$(( $x + 1 ))
 
done
 
# similarly, "((x--))" will decrease the value by 1.
```

**!!! Independent Exercise:** 
- Comment out the `for` loop you wrote in `cycleNames.sh`, your code that cycles through group members and tells each person when to give lab meeting. Replace that `for` loop with a `while` loop that yields the same output - prints an echo statement that includes each member's name.

### `while read line` loops

Sometimes we want to read a file and do something to each line. For this, we can use a special `while` loop syntax. For each cycle of the loop, we will read a line of the file, starting at the top and making our way to the bottom. In the first cycle of the loop, the content of the first line will be assigned to the variable, say, $line. In the second cycle of the loop, the second line will be reassigned to $line. In this way, we can loop through each line of the file and perform the same function on each line.

**while read line usage**

```
while read -r line;
do
    echo “$line”
done < <inputfile>
```

In this example, the words `while`, `read`, `do`, and `done` are all required and are written literally. The user picks the variable name, and here that name is `line`. The echo statement can be replaced with any other set of commands. Within these commands, the variable `line` can be dereferenced using the syntax “$line”.

At the very bottom, there is the syntax `done < inputfile`. This is a **redirect** statement that pushes a pre-made file into the loop as input.

To re-write the Hogwarts house names loop that gives points to each house, we will first need to create an input file called `listOfHouses.txt` with the following content …

```
$ more listOfHouses.txt
Gryffindor
Slytherin
Ravenclaw
Hufflepuff
```

Now, we can use the `listOfHouses.txt` file as input within our code …

```
#!/usr/bin/env bash
 
# Cycle over each line in the file and echo a statement
while read -r line;
do
  echo "Ten points for $line"
done < listOfHouses.txt
```

**!!! Independent Exercise:** 
- Comment out the `while` loop you wrote in the previous exercise's script called `cycleNames.sh`. Replace that `while` loop with a `while read lines` loop that yields the same output - prints an echo statement that includes each member's name. Note - you'll need to create an input file that lists all your names, each on its own line.

### Tips, Warnings, and Bonus Content

**!!! Warning** - Stuck in a loop? If you are stuck in an infinite loop, press `CTRL + C`

**!!! Tip** - incrementing numeric variables using x++
- If we have a numeric variable called x that is assigned the value 0, we can add one to this variable each time we go around the loop with the following x++ syntax …

```
x=0
 
while [ $x -le 5 ]
do
  echo "x is equal to $x"
 
  ((x++))     # Means the same as x=$(( $x + 1 ))
 
done
 
# similarly, "((x--))" will decrease the value by 1.
```

**!!! Conventions** - We have been using **x** as a counter variable in class. And typically counter variables are single letters. The convention however is typically to choose **i**. In many online examples, you'll see **i**, so just be aware. 

**!!! Bonus content** 
- `break` - If you want to stop going around the loop, you can use the command `break`. Typically, you'll need to place a conditional within a loop to use this correctly.
- `continue` - If you want to skip to the next round of the loop, use the command `continue`. Typically, you'll need to place a conditional within a loop to use this correctly.
- `for` loops C-style - hard

<details>
  <summary>for usage - C style</summary>

---

This will may be familiar to people who have written code in other languages that have been influenced by the C language.

Personally, don't use C-style loops very often, but they are useful to illustrate that `while` loops and `for` loops do the same thing.

In a `while` loop, we actually did three things:

1. INITIALIZATION – When we set counter=0, we initiated the counter.
2. CONDITION – When we checked whether $counter -lt 2, we were testing for a conditional statement
3. AFTERTHOUGHT – when we added 1 to $counter, this is called an afterthough.

Those three steps are used in a C-style `for` loop in a slightly different way, like so:

```
for (( <INITIALIZATION>; <CONDITION>; <AFTERTHOUGHT> ))
do
<commands>
done
```

Here is an example of the same loop in a C-style:

```
#!/usr/bin/env bash
 
files=(file1.txt file2.txt file3.txt)
 
for (( counter=0; counter <= 2; counter++ ))
do
  echo $counter
  echo ${files[$counter]}
done
```

The syntax within the double parentheses is very special because it is basically mimicking “C”. Don't worry if it seems to look weird. If this doesn't make sense, just skip it and move on to Python-style loops. You can totally live without C-style loops.

---

</details>


<details>
  <summary>Example usage of break and continue</summary>

---

`break` statement forces the loop to end/stop under a given circumstance/for a certain situation.

```
#!/usr/bin/env bash

# Make a backup set of files

for value in $1/*
do
    used=$( df $1 | tail -1 | awk '{ print $5 }' | sed 's/%//' )
    if [ $used -gt 90 ]
    then
        echo Low disk space 1>&2
        break
    fi
    cp $value $1/backup/
done
```
```
i=0

while [[ $i -lt 5 ]]
do
  echo "Number: $i"
  ((i++))
  if [[ $i -eq 2 ]]; then
    break
  fi
done

echo 'All Done!'
```


`continue` statement forces the loop to end/stop the current iteration of the loop and begin the next iteration. 

```
#!/usr/bin/env bash

# Make a backup set of files

for value in $1/*
do
    if [ ! -r $value ]
    then
        echo $value not readable 1>&2
        continue
    fi
    cp $value $1/backup/
done
```
```
i=0

while [[ $i -lt 5 ]]; do
  ((i++))
  if [[ "$i" == '2' ]]; then
    continue
  fi
  echo "Number: $i"
done

echo 'All Done!'
```
---

</details>

### Looping over arguments

A typical task is to supply your script with a list of arguments using a wildcard character like so …

```
$ bash measureDiskSpace.sh *.txt
```

Say this script performs `du -h <file.txt>` on each file you pass to it and formats the output like so …

```
Disk usage for file1.txt is:    0B	file1.txt
Disk usage for file2.txt is:  4.0K	file2.txt
Disk usage for file3.txt is: 23.0K      file3.txt
```

**!!! Exercise:** Try to think about how you would write `measureDiskSpace.sh` so it can accept any number of arguments provided, such as when you call it with a wildcard.

**!!! Hint:** Try converting the special array variable for arguments into a new array variable name like so. Then see if you can use a loop structure we already learned to help you do this.

```
myarguments=$@
```

My answer here:

<details>
  <summary>Answer</summary>

```
#!/usr/bin/env bash
 
# Capture arguments
myarguments=$@
 
#Loop over each argument
 
for myfile in ${myarguments[@]}
do
	# Calculate the disk usage for a file
	myspace=$( du -h $myfile )
 
	# Print the sentence including the file name and the disk usage:
	echo -e "Disk usage for $myfile is: $myspace"
done
```

</details>

Continue on to [Control Flow Practice](4-4_Control_Flow_Practice.md)
