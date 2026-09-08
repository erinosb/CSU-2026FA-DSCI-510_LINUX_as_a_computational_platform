# Array Variables

### Todays objectives: 

<details>
  <summary>Click to expand/collapse</summary>

---

- **Vocabulary**
  - Variables
  - Values
  - Variable assignment, reassignment, & dereferencing
  - Integers v. floating point numbers
  - Array variables
  - Array elements
  - Indexing
  - Special variables
  - Hard Coding
  - String
  - String operation
  - Replacement/substitution
  - Sub-setting strings
  - Sub-strings
  - The environment
  - Environmental variables
  - Startup files
  - Control flow

- **Things you should know how to do after this class**
  - Know how to assign and reassign variables
  - Know how to dereference variables to reveal their associated values
  - Know what constitutes an allowed and good sense name for a variable
  - Capture output of a command as a variable
  - Know some basic math operations
  - Know what an array variable is and how to assign values to one
  - Understand the basics of array indexing
  - Know how to enter input into a script by passing argument that can be accessed with a special variable
  - Know how to save output from a script using `>` and `>>`
  - Know a little bit about manipulating string variables
  - Understand that when strings are saved as the values of a variable, they can be manipulated using string operations.
  - Be able to describe the environment. Know that the shell stores information about the environment in environmental variables. Be able to dereference environmental variables on your terminal or within a script
  - Be able to differentiate sequences, conditionals, and loops

- **Commands covered**
  - `; (chaining)`
  - `bash`
  - `echo`
  - `variable=value`
  - `variable=$(command)`
  - `variable=$((math expression))`
  - `$variable`
  - `${variable}`
  - `arrayvariable=(value1 value2 value3)`
  - `${arrayvariable[*]}`
  - `${arrayvariable[@]}`
  - `${arrayvariable[0]}`
  - `${arrayvariable[1]}`
  - `${arrayvariable[#]}`
  - `${#arrayvariable[@]}`
  - `read`
  - `$0`
  - `$1`
  - `$2`
  - `$#`
  - `$@`
  - `$*`
  - String operations:
    - `newvar=${oldvar/a/A}`
    - `newvar=${oldvar//a/A}`
    - `newvar=${oldvar/#To/So}`
    - `newvar=${oldvar/%txt/fastq}`
    - `newvar=${oldvar:3}`
    - `newvar=${oldvar:3:4}`
  - `printenv`
  - `$USER`

---

</details>

### Test your understanding - take this quiz!

[Quiz 5](https://forms.gle/wFKrVyv5QBf5UCsV6)

### Try Alpine login again:  

- Navigate to https://ondemand-rmacc.rc.colorado.edu in a new tab or window
  - For me, I right-click on the above link and select **Open Link in New Window**
- Log into your "CSU NET ID". You will receive a "DUO PUSH" on your phone. Accept it.
- To access the LINUX command line on ALPINE, go to the **Clusters** menu. Select **>_Alpine Shell**
- In another window, you can also access your files by going to the **Files** menu and selecting any available directories.

For reference, see: [Connecting to remote computers](../../Resources/Connecting_to_remote_computers.md)

Keep learning: 
- DSCI 511 - Python
- DSCI 512 - RNA-seq
- [RC help events and training](https://www.colorado.edu/rc/events)
  - [Working with Linux](https://colorado.libcal.com/calendar/events/linux) a short course - Friday, August 29, 11am - 12pm
- [Coding & Cookies](https://libguides.colostate.edu/coding-cookies/home) through the Morgan Library

### Array Variables

So far, we have assigned only a single value to each variable. We can also assign multiple, ordered values to a variable. These create **array variables**.

Arrays are zero-based. That is, the first element is accessed with the number 0.

**Assign values** to an array variable using parentheses:

```
arrayname=(value1 value2 value3 value4)

# if you wanted to leave an open slot as an empty string placeholder ... you could use " " though it doesnt seem to matter if there is a space between the " " as "" also works. 

arrayname=(value1 " " value3 value4)

# if you print out all the values in this arrayvar the empty slot doesnt show up but you can still access this slot and even reassign its value!
```

**Dereference** the list in a variety of different ways:

```
echo $arrayname
echo ${arrayname[*]}
echo ${arrayname[@]}
```

**!!! Recall:** We just used parentheses to capture the output of a command into a variable, but in those cases, there was an extra dollar sign in the syntax: 

```
$ myscripts=$(ls *.sh) #captures the names of scripts in a directory as the values of an array variable
 
$ echo $myscripts
 
$ myships=(enterprise discovery titan voyager) #assigns values to an array variable
 
$ echo $myships
```

Let's explore this more. Make a bash script called `exploringArrays.sh`. Within it, create the array `ships` with four **values**. Values are also called **elements**. We can access the elements in a variety of ways:

```
#!/usr/bin/env bash
 
# Create an array variable
ships=(enterprise discovery titan voyager)
 
# Explore the elements
echo ${ships[*]} # all elements
echo ${ships[@]} # all elements
echo ${ships[0]} # the first element
echo ${ships[1]} # the second element
echo ${ships[2]} # the third element
echo ${ships[3]} # the fourth element
```

In the example above, the number within the square brackets is called an **index** (plural is indices or indexes). The process of accessing an individual element using an index is called **indexing**. Indexing relies on the fact that elements within an array have a set order.

We can also use indices to add a new element to an array or to **reassign** an element of an array. Try this:

```
#!/usr/bin/env bash
 
# Create an array variable
ships=(enterprise discovery titan voyager)
 
# Explore the elements
echo ${ships[*]} # all elements
echo ${ships[@]} # all elements
echo ${ships[0]} # the first element
echo ${ships[1]} # the second element
echo ${ships[2]} # the third element
echo ${ships[3]} # the fourth element
 
# Add a new starship
ships[4]="excelsior"
 
echo "Added a new element: ${ships[*]}"
 
# Replace a starship
ships[1]="defiant"
 
echo "Changed an element: ${ships[*]}"
```

Finally, we can assess how many elements are in an array variable using the following syntax:

```
# length of an array variable. That is, how many elements are in the array:
echo ${#ships[*]}
```

example of creating an empty slot and reassigning it ...

```
#leave empty slot in the array variable
ships=(" " discovery titan voyager)

#re-assign empty slot
ships[0]="mayflower" 
```

**!!! Independent Exercise:** What cities have you lived in and in what order?

- create an array variable called `mycities`
- Add the names of cities you have lived in as individual elements
- **Hint** use quotes to enclose values that contain spaces like “San Francisco”
- Write a little paragraph using an echo statement about your life in which you dereference the different cities using indexes.
- Your final output should read something like the below paragraph:

`“I was born in Palo Alto. I grew up in Saratoga. I moved to Santa Cruz for college. Then I lived in Eugene. Next, I moved to Berkeley for graduate school. After that, I lived in Chapel Hill. Now, I live in Fort Collins.”`

**!!! Alternative Exercise:** If you haven't lived in very many cities, that's ok. You can list cities you have visited or cities where you wish to live or visit.

Continue on to [Special Variables](3-7_Special_variables_and_IO.md)
