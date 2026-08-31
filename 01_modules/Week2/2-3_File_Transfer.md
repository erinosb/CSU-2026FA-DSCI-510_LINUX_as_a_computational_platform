<p align="center">
<img width="100%" alt="icons" src="../../05_images/headers_Slide2.png">
</p>

# File Transfer 

So far, we have learned to copy and move files from one location on your local computer to another location on the same computer. However, we can also copy content from remote computers and this is called transferring files.

There are many different programs to help transfer files (or directories) between computers. Different linux installations have different programs as default. Also, remote servers and repositories are often set up to interact with one or another of these programs. You'll need to experiment to determine which of these options works best on your system.

When we learn software installation later in this course, we will add more of these programs.

Common file transfer programs are:

- `sftp`
- `wget`
- `curl`
- `rsync`
- `scp`

### `sftp` - Secure File Transfer Program

```
ftp <sftp://address/to/ftp/site>

-requires that the host/remote is configured as an sftp site
-interact remotely with the remote computer
-use commands cd, ls, get, bye
```

### `wget` - World wide web GET

```
wget <http://address/to/file/file.txt>

-must be installed on MacOS systems using Conda or Homebrew
```

See these links for [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) and [Homebrew](https://brew.sh/) installation! See [here](https://formulae.brew.sh/formula/wget) for installing wget with homebrew!

### `curl` - Command line URL

```
curl [options] <sourcefile.txt> curl [–remote-name-all] <http://address/to/file/file.txt>

-can only download one file at a time
```

### `rsync` - Remote file and directory SYNChronization

```
rsync [options] <source> <target>
rsync [-avzP] http://address/to/dir/> <.>

-a archival, preserves time stamps and permissions
- v verbose, outputs comments to the screen
- z zip, compress to transfer between computers
- P progress, print information on progress to the screen
```

### `scp` - Secure CoPy

```
scp <sourcefile> <target>
scp <http://address/to/file/file.txt> <.>
```

## Exercise 

We are going to do the following:

1. Download the yeast genome (using rsync or wget)
2. Ensure the files were not corrupted in transit (using md5 sums)
3. Unzip the files (using gunzip)

### Using `rsync` or `wget` to download files from UCSC Genome Browser

**!!! Group Exercise:** Obtain the *Saccharomyces cervisiae* genome from the UCSC Genome Browser.

- Go to [UCSC Genome Browser](https://genome.ucsc.edu/)
- Navigate to **Downloads → Genome Data → Other Genomes → S. cerevisiae**
- Let's take some time to navigate around the **SacCer3** links
- Open an terminal and navigate to a place on your local computer where you want to save your downloaded genome.
- Make a new directory that will house the genome. (I'm putting mine in /myhome/DSCI510/02_Exercises/)

```
$ mkdir sacCer3
```

- navigate into that directory:

```
$ cd sacCer3
```

- We want to obtain the Dataset by Chromosome.
- Download the contents of this directory using the command rsync:

**`rsync` Usage:**

`rsync [options] <source> <target>`

```
$ rsync -avzP rsync://hgdownload.cse.ucsc.edu/goldenPath/sacCer3/chromosomes/ .
```

**!!! Common pitfall:** Don't forget the trailing `.`. That indicates your target directory which is your current working directory.

Didn't work? Try this one …

```
$ wget --timestamping 'ftp://hgdownload.cse.ucsc.edu/goldenPath/sacCer3/chromosomes/*'
```

Use the commands you learned last week to explore what you have obtained (ls, more, less, head, tail, wc, etc).


### Ensuring files were not corrupted using `md5sum` checksums

To ensure your files were not corrupted during transit, the UCSC browser people have included **md5sum checksums** for each file that are located in a file called `md5sum.txt`. **checksums** are digital codes associated with a file that are calculated out of information within the file. If the integrity of the file is intact, the md5sum checksum program will match digital code in those text files.

**!!! Group Exercise:** Check sums

Check the sums of all the `.fa.gz` files using this command:

```
$ md5 *.fa.gz
```

**!!! Didn't work?** Try `md5sum *.fa.gz` or `md5sum-lite *.fa.gz` instead. Different distributions will have different utilities.

Read the proper check sums included in this directory from UCSC like so:

```
$ more md5sum.txt
```

Do the digital codes match? Let's check. Here is a little script that I called `CompareSums.sh` to check the contents ...

```
#!/usr/bin/env bash

# Usage check, if wrong will show instructions, need 2 arguments passed to the script
if [ "$#" -ne 2 ]; then
    echo "ERROR: you need to provide the script two files: $0 <checksums1.txt> <checksums2.txt>"
    exit 1
fi


file1="$1"
file2="$2"


# Check that the 2 arguments passed are files that actually exist
if [ ! -f "$file1" ] || [ ! -f "$file2" ]; then
    echo "ERROR: One or both files do not exist."
    exit 1
fi


# what is the script going to do
echo "Comparing checksum files: $file1 vs $file2"
echo


# Sort both files by filename (2nd column)
sorted1=$(mktemp)
sorted2=$(mktemp)
sort -k2 "$file1" > "$sorted1"
sort -k2 "$file2" > "$sorted2"

# Compare line by line: only column 1 (checksum)
paste "$sorted1" "$sorted2" | while read -r sum1 name1 sum2 name2; do
    if [ "$sum1" = "$sum2" ]; then
        echo "$name1: MATCH"
    else
        echo "$name1: MISMATCH"
        echo "    $file1: $sum1"
        echo "    $file2: $sum2"
    fi
done

rm -f "$sorted1" "$sorted2"
```

### Unzipping files

The `.fa.gz` files we have downloaded are compressed using a utility called **gzip** so they are smaller for transfer. You cannot navigate into them using `more` or `less` until they are uncompressed.

**`gzip` usage**

To compress:
```
gzip <filename.txt>
```

To un-compress:
```
gunzip <filename.txt.gz>
```

Let's unzip the files.
```
$ gunzip *.fa.gz
$ ls -alh
```

**!!! Quick tip:** There are many other utilities that can be used for compressing files. Some examples are `bzip2`, `zip`, and `xz`.

**!!! Best Practices:** 

- Every time you download something, make sure it wasn't corrupted during transit.
- Try to downloading data with commands that can be written down, not with clicking.
- Every time you download something … write it down!

Continue on to [File formats](2-4_File_Formats.md)
