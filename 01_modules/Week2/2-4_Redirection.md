# Redirection 

### Todays objectives: 

<details>
  <summary>Click to expand/collapse</summary>

---

- **Vocabulary**
  - Standard streams
  - Redirection
  - Standard input (stdin)
  - Standard output (stdout)
  - Standard error (stderr)
  - Concatenate
  - Regular expressions/regex
  - Delimiting character
  - Field
  - Pipe

- **Things you should know how to do after this class**
  - Understand what stdout, stderr, and stdin mean
  - Know how to redirect stdout, or stderr to an output file.
  - Know how to concatenate files together
  - Know how to search for simple strings in files
  - Know how to modify your search for simple strings using options
  - Know how to cut out delimited information from files
  - Know how to change the delimiter from a tab to another character (using cut)
  - Know how to use pipes to combine two commands into one

- **Commands covered**
  - `alias`
  - `ssh`
  - `rsync` or `wget` (or sftp, curl, or scp – whichever works best for you)
  - `md5sum` or `md5` or `md5sum-lite`
  - `gzip`
  - `gunzip`
  - `>`
  - `2>`
  - `&>`
  - `>>`
  - `cat`
  - `grep`
  - `cut`
  - `|`
  - `sort`
  - `uniq`
  - `tee`

---

</details>


### Test your understanding - take this quiz!

[Quiz 3](https://forms.gle/rmNNG3vXTzVgFc6X8)

### Standard Streams 

**Standard streams** are default input and output channels. In Linux, there are three standard streams: **stdin**, **stdout**, and **stderr**. You may also see input and output channels referred to as Input/Output or simply **I/O**.

<p align="center">
<img width="410" alt="stdin-stdout-stderr" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/stdin-stdout-stderr.png">
</p>

**Standard Input**, or **stdin**, is input going into the shell. By default, this input comes from you typing on the keyboard.

When your run a command, say `wc file1.txt`, the shell sends its output to a special file called **standard output** (**stdout**), which by default is not saved in a directory, but is routed to the screen.

If you run an errant command, say `wc werkejtkhgo` when there is no file `werkejtkhgo`, an error message will be produced. The error message goes to a file called **standard error** (**stderr**) that is also routed to the screen by default.

**Redirection** allows us to circumvent the defaults, allowing us to redefine where standard output and standard error go. This is a useful way to capture information.

### Redirect output with `>`

Redirection of standard-output is performed using the `>` operator.

**Redirect stdout Usage:**

`command line > outputfilename.txt`

```
$ wc chrI.fa > wc_output.txt
```

### Redirect error and status messages with `2>`

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

### Redirect both output and error/status messages with `&>`

Wonderful! But what if we had given `wc` two files, one good and one bad. Experiment a little.

```
$ wc chrI.fa.gz blerg > wc_both_1.txt
$ wc chrI.fa.gz blerg 2> wc_both_2.txt
```

We can capture both using `&>`:

**Redirect stdout and stderr Usage:**

`command line &> outputfilename.txt`

```
$ wc chrI.fa.gz blerg &> wc_both_3.txt
```

**!!! Common pitfall:** redirection will overwrite existing files. If, instead, you would prefer to append the new information to the end of an existing file, you can use `»`

```
$ wc chrI.fa.gz >> runningTotal.txt
$ wc chrII.fa.gz >> runningTotal.txt
$ wc chrIII.fa.gz >> runningTotal.txt
$ more runningTotal.txt
```

Continue on to [Working with files 2](2-6_Working_with_files2.md)
