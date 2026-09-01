<p align="center">
<img width="100%" alt="icons" src="../../05_images/headers_arrows.png">
</p>

# Redirection

## Standard Streams 

**Standard streams** are default input and output channels. In Linux, there are three standard streams: **stdin**, **stdout**, and **stderr**. You may also see input and output channels referred to as Input/Output or simply **I/O**.

<p align="center">
<img width="50%" alt="stdin-stdout-stderr" src="../../05_images/stdin-stdout-stderr.png">
</p>

**Standard Input**, or **stdin**, is input going into the shell. By default, this input comes from you typing on the keyboard.

When your run a command, say `wc file1.txt`, the shell sends its output to a special file called **standard output** (**stdout**), which by default is not saved in a directory, but is routed to the screen.

If you run an errant command, say `wc werkejtkhgo` when there is no file `werkejtkhgo`, an error message will be produced. The error message goes to a file called **standard error** (**stderr**) that is also routed to the screen by default.

**Redirection** allows us to circumvent the defaults, allowing us to redefine where standard output and standard error go. This is a useful way to capture information.

----

## Redirect output with `>`

Redirection of standard-output is performed using the `>` operator.

**Redirect stdout Usage:**

`command line > outputfilename.txt`

```
$ wc covid_annotation.gff  > wc_annotations.txt
```

----

## Redirect error and status messages with `2>`

Let's see what happens if we tried to redirect an errant command …

```
$ wc blerg > wc_fake_output.txt
```

We can capture the error message with `2>`. This **redirects** standard-error to our desired file:

**Redirect stderr Usage:**

`command line 2> outputfilename.txt`

```
$ wc blerg 2> wc_err_output.txt
```

-----

## Redirect both output and error/status messages with `&>`

Wonderful! But what if we had given `wc` two files, one good and one bad. Experiment a little.

```
$ wc covid_annotation.gff blerg > wc_both_1.txt
$ wc covid_annotation.gff blerg 2> wc_both_2.txt
```

We can capture both using `&>`:

**Redirect stdout and stderr Usage:**

`command line &> outputfilename.txt`

```
$ wc covid_annotation.gff blerg &> wc_both_3.txt
```

>[!WARNING]
> Redirection will overwrite existing files. If, instead, you would prefer to append the new information to the end of an existing file, you can use `»`

```
$ wc covid_annotation.gff >> runningTotal.txt
$ wc covid_sequence.fna >> runningTotal.txt
$ more runningTotal.txt
```

Continue on to [Assignment 3](../../02_assignments/Assignment_1.md)

Continue on to [Working with files 2](2-5_Working_with_files2.md)
