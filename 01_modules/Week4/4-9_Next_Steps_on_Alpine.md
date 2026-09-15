# Next steps on ALPINE!

This is all the time we have for this class. You are encouraged to learn more about how to use ALPINE on your own and through future workshops and classes.

Here are recommended next steps to consider:
- Learn to customize your user experience by editing your `.bash_profile` on ALPINE.
- Learn to load already-installed software using **modules**
  - [About modules on ALPINE](https://curc.readthedocs.io/en/latest/compute/modules.html)
- Learn to install software on ALPINE using CONDA
  - [Getting started with CONDA](https://curc.readthedocs.io/en/latest/software/python.html#basic-conda-commands-to-get-you-started)
  - [Upcoming workshop on conda and software install on ALPINE](https://www.colorado.edu/rc/events)
- Learn how to save, synchronize, and version-control your scripts using [GitHub](https://github.com/)
- Learn how to organize large computational projects - DSCI512 - RNA sequencing data analysis


Here is some old content from the SUMMIT days. It may be useful for some users:

<details>
  <summary>Summit - Customizing</summary>

---

In this section, we'll learn how to customize our SUMMIT user experience.

All the files associated with customizing the User experience will go in your home directory. Let's navigate there and inspect its contents …

```
$ cd
$ pwd
$ ls -alh
```

**Question:** Do you see a file called `.bash_profile`?

If YES, go ahead and make a backup copy into a backup directory like so …

```
# If you have a .bash_profile file, do the following...
$ mkdir bash_profile_bkup
$ cp .bash_profile bash_profile_bkup/220915_bash_profile
```

If NO, create the file …

```
# If you do not have a .bash_profile file, do the following...
$ touch .bash_profile
```

The `.bash_profile` file where we will add customized code that will run at the START of EVERY SUMMIT session.

For example, if we want to use our custom sacct and squeue commands every session, we can make aliases of these here.

To open your .bash_profile in an editor, go to **FILE –> Open from Path … –>** Type in `/home/<your-eID@colostate.edu/.bash_profile`

Then, at the bottom of the file, add the following code …

```
#Aliases
alias scheck="squeue -u $USER"
alias sa='sacct -X --format JobID,JobName,AllocCPUS,State,ExitCode,Elapsed,TimeLimit,Submit,Start,End'
```

Save and close.

On the terminal, you can refresh these new conditions using …

```
$ source .bash_profile
```

Now, you can go ANYWHERE on SUMMIT and use `scheck` instead of `squeue -u $USER` and you can use `sa` instead of the long `sacct` command. This will also be **persistent**, as in, it will work every time you log into SUMMIT.

---

</details>

<details>
  <summary>Summit - Installing Software</summary>

---

### Loading pre-installed software with modules

The SUMMIT support staff has already installed some software on SUMMIT that you can load. To browse what is pre-installed,

```
$ module avail
```

You may have already noticed that when you login you are prompted to try this. We won't be going through the modules here, but you can learn more about them on the [Module User Guide](https://curc.readthedocs.io/en/latest/compute/modules.html)

To load a listed module,

```
$ module load <nameofmodule>
```

### Loading pre-installed software with modules

Scientific software is created by the open-source community of researchers like you and me.

<p align="center">
<img width="410" alt="open source" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/opensource_img.png">
</p>

When the software is being actively supported, there may be binaries (ready-to-run programs) available to download. If not, the **source code** of the software will need to be downloaded, compiled, and installed. For several decades, these tasks took up a large amount of a person's time and energy while wearing down their very sanity.

However, **software installers** have really changed the game. There are now several software installers available for different systems:

- Homebrew - Mac OS
- apt-get - Ubuntu, other linux
- conda - all systems

Homebrew and apt-get require administrative access on your own computer, whereas you can use conda to install on systems where you are not an administrator, such as on SUMMIT.

Today, we will walk you through how to install software on SUMMIT using **conda**. What is conda?

<p align="center">
<img width="410" alt="conda" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/conda_logo.png">
</p>

#### conda

- conda is an open-source **package** management system
- conda maintains a repository of open-source software code called Anaconda
  - We will use the computational biology specific version called [bioconda](https://anaconda.org/bioconda/repo)
- conda assists in downloading, compiling, and installing software
- when a piece of software is downloaded, all dependent packages will also be obtained
- conda helps users create different **environments** where software collections can be collected and curated.

**packages** - small units of software

**environment** - a virtual space where a user can contain a collection of installed software. Users can have environments associated with different research projects.

#### what is up with the name?

- python, anaconda, sense a theme? hint - there is also a boa

#### A little bit about the scope of this project

<p align="center">
<img width="410" alt="updates" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/update.png">
</p>

### Configuring conda with `.condarc`

Today's lesson is adapted from: [https://curc.readthedocs.io/en/latest/software/python.html](https://curc.readthedocs.io/en/latest/software/python.html) to specifically apply to command-line bioinformatics software. See the original doc for more information and ways to use it.

Our first step before we can use conda is to configure our startup files to customize how conda will perform.

Like `.bash_profile`, `.bashrc` and `.zshrc`, other programs use “.rc” files to start up files that spell out configuration settings. These settings are not BASH scripts, though, just lists of values.

For conda, the startup file is called `.condarc` and it is located in your `$HOME` directory.

**!!! Exercise** - let's work together to customize our conda settings.

Navigate to your `$HOME` directory and open `.condarc`

```
$ cd
$ open .condarc
```

Type in the following at the end of the file, making sure to replace `your-eID@colostate.edu` with your actual eID-e-mail address.

```
pkgs_dirs:
  - /projects/<your-eID@colostate.edu>/.conda_pkgs
envs_dirs:
  - /projects/<your-eID@colostate.edu>/software/anaconda/envs
```

Save and exit the file. You won’t need to perform this step again – it’s permanent unless you modify `.condarc` later.

The `.condarc` file provides a variety of settings that can be detailed to speed up your workflows. For more information on `.condarc`, check out the [Anaconda documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/use-condarc.html). 

### Create a new conda environment

Now, let's create a new conda environment where we can house some software associated with this class. To do this, we will need to 1) Initialize Anaconda, 2) Create our new conda environment, and 3) install software on it.

This will take a little while to do. But once we do this the first time, then every subsequent time we log into SUMMIT, we can load our environment and our software will be ready to use at a moment's notice.

#### 1. Initialize Anaconda

First move to the compile node:

```
$ ssh scompile
```

Next, let's load the anaconda module

```
$ module load anaconda
```

Check if anaconda is working …

```
(base) $ conda -V
conda 4.13.0 # It should say this. ONLY if it says command not found, do the next step...
 
 
#$ source /curc/sw/anaconda3/latest #you probably don't need to do this
```

Great. Now we've essentially started anaconda. You should see a `(base)` prior to your prompt.

Next, let's list what environments are already available for us to load software into …

```
$ conda env list #may take a minute to load
# conda environments:
#
base                  *  /curc/sw/anaconda3/2020.11
```

We need to create a new environment that we can install to.

1. **conda init**: adds conda to your `.bashrc`

```
(base) jesshill@colostate.edu@shas0137 ~]$ conda init
no change     /curc/sw/anaconda3/2020.11/condabin/conda
no change     /curc/sw/anaconda3/2020.11/bin/conda
no change     /curc/sw/anaconda3/2020.11/bin/conda-env
no change     /curc/sw/anaconda3/2020.11/bin/activate
no change     /curc/sw/anaconda3/2020.11/bin/deactivate
no change     /curc/sw/anaconda3/2020.11/etc/profile.d/conda.sh
no change     /curc/sw/anaconda3/2020.11/etc/fish/conf.d/conda.fish
no change     /curc/sw/anaconda3/2020.11/shell/condabin/Conda.psm1
no change     /curc/sw/anaconda3/2020.11/shell/condabin/conda-hook.ps1
no change     /curc/sw/anaconda3/2020.11/lib/python3.8/site-packages/xontrib/conda.xsh
no change     /curc/sw/anaconda3/2020.11/etc/profile.d/conda.csh
modified      /home/jesshill@colostate.edu/.bashrc

==> For changes to take effect, close and re-open your current shell. <==
```

You may open a new jupyter lab terminal, or exit (go back to login), and do `ssh scompile` again. If you don't see `(base)` do `$ module load anaconda` again.

Next, we'll point conda to the place from which we want to download software which is `conda-forge` and `bioconda`

```
(base) jesshill@colostate.edu@shas0137 ~]$ conda config --add channels conda-forge
(base) jesshill@colostate.edu@shas0137 ~]$ conda config --add channels bioconda
```

#### 2. Create a custom environment

Now, it's time for us to start our custom environment. We'll call it DSCI510 as this environment will be specific to our class.

```
(base) [jesshill@colostate.edu@shas0137 ~]$ conda create -n DSCI510 python==3.8 r-base=4
Collecting package metadata (current_repodata.json): done
Solving environment: failed with repodata from current_repodata.json, will retry with next repodata source.
Collecting package metadata (repodata.json): done
Solving environment: done


...


  xorg-libxdmcp      conda-forge/linux-64::xorg-libxdmcp-1.1.3-h7f98852_0
  xorg-libxext       conda-forge/linux-64::xorg-libxext-1.3.4-h7f98852_1
  xorg-libxrender    conda-forge/linux-64::xorg-libxrender-0.9.10-h7f98852_1003
  xorg-libxt         conda-forge/linux-64::xorg-libxt-1.2.1-h7f98852_2
  xorg-renderproto   conda-forge/linux-64::xorg-renderproto-0.11.1-h7f98852_1002
  xorg-xextproto     conda-forge/linux-64::xorg-xextproto-7.3.0-h7f98852_1002
  xorg-xproto        conda-forge/linux-64::xorg-xproto-7.0.31-h7f98852_1007
  xz                 conda-forge/linux-64::xz-5.2.5-h516909a_1
  zlib               conda-forge/linux-64::zlib-1.2.11-h516909a_1010
  zstd               conda-forge/linux-64::zstd-1.5.0-ha95c52a_0


Proceed ([y]/n)?
```

Hit ENTER.

This takes a few minutes. Here's what the end will look like:

```
...
libstdcxx-devel_linu | 9.9 MB    | ################################################################## | 100% 
binutils_linux-64-2. | 23 KB     | ################################################################## | 100% 
libcurl-7.76.1       | 328 KB    | ################################################################## | 100% 
libgfortran-ng-11.2. | 19 KB     | ################################################################## | 100% 
sysroot_linux-64-2.1 | 31.6 MB   | ################################################################## | 100% 
gxx_impl_linux-64-9. | 10.6 MB   | ################################################################## | 100% 
libsanitizer-9.4.0   | 6.9 MB    | ################################################################## | 100% 
gsl-2.6              | 3.2 MB    | ################################################################## | 100%

Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate DSCI510
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

Yay! Now we have started our new environment. Let's list our environments and check that it has been added:

```
(base) [jesshill@colostate.edu@shas0137 ~]$ conda env list
# conda environments:
#
base                  *  /curc/sw/anaconda3/2020.11
DSCI510                  /projects/.colostate.edu/jesshill/software/anaconda/envs/DSCI510
```

Our new environment is available for us, but we are still using the (base) environment as denoted by the *. To switch into the `DSCI510` environment, do the following …

```
(base) [jesshill@colostate.edu@shas0137 ~]$ conda activate DSCI510
 
(DSCI510) [jesshill@colostate.edu@shas0137 ~]$ conda env list
# conda environments:
#
base                     /curc/sw/anaconda3/2020.11
DSCI510               *  /projects/.colostate.edu/jesshill/software/anaconda/envs/DSCI510
```

Notice how the information prior to the prompt now says `(DSCI510)`. And you can see how the asterisk has moved in the environment list, too.

#### 3. Install new programs to your environment

We are going to install some software developed by the UCSC Genome Browser Team. It's

```
$ conda install ucsc-randomlines ucsc-fafrag ucsc-faonerecord
Collecting package metadata (current_repodata.json): done
Solving environment: done


==> WARNING: A newer version of conda exists. <==
  current version: 4.9.2
  latest version: 4.10.3

Please update conda by running

    $ conda update -n base -c defaults conda

## Package Plan ##

  environment location: /projects/.colostate.edu/jesshill/software/anaconda/envs/DSCI510

  added / updated specs:
    - ucsc-fafrag
    - ucsc-faonerecord
    - ucsc-randomlines


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    ucsc-fafrag-377            |       h0b8a92a_2         132 KB  bioconda
    ucsc-faonerecord-377       |       h0b8a92a_2          28 KB  bioconda
    ucsc-randomlines-377       |       h0b8a92a_2         128 KB  bioconda
    ------------------------------------------------------------
                                           Total:         288 KB

The following NEW packages will be INSTALLED:

  mysql-connector-c  conda-forge/linux-64::mysql-connector-c-6.1.11-h6eb9d5d_1007
  ucsc-fafrag        bioconda/linux-64::ucsc-fafrag-377-h0b8a92a_2
  ucsc-faonerecord   bioconda/linux-64::ucsc-faonerecord-377-h0b8a92a_2
  ucsc-randomlines   bioconda/linux-64::ucsc-randomlines-377-h0b8a92a_2


Proceed ([y]/n)? 


Downloading and Extracting Packages
ucsc-fafrag-377      | 132 KB    | ################################################################## | 100% 
ucsc-faonerecord-377 | 28 KB     | ################################################################## | 100% 
ucsc-randomlines-377 | 128 KB    | ################################################################## | 100% 
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
     
(DSCI510) [jesshill@colostate.edu@shas0136 ~]$ faFrag
faFrag - Extract a piece of DNA from a .fa file.
usage:
   faFrag in.fa start end out.fa
options:
   -mixed - preserve mixed-case in FASTA file

(DSCI510) [jesshill@colostate.edu@shas0136 ~]$ randomLines
randomLines - Pick out random lines from file
usage:
   randomLines inFile count outFile
options:
   -seed=N - Set seed used for randomizing, useful for debugging.
   -decomment - remove blank lines and those starting with 
```

Let's test if our software works!

```
(DSCI510) [jesshill@colostate.edu@shas0136 ~]$ faOneRecord 
faOneRecord - Extract a single record from a .FA file
usage:
   faOneRecord in.fa recordName
```

### Next time you log in - cheat sheet

Next time you log into SUMMIT and you want to use this same environment, here is what you can do …

```
(base) $     #first, make sure you see (base). If you don't load anaconda with $ module load anaconda
(base) $ conda activate DSCI510
```

That's all! Once you do that, you can use the three software applications already installed. It should take no time at all.

Ok, that's great, but what do I do next time if I want to start my own, new environment?

Just do the following …

```
(base) $     #first, make sure you see (base). If you don't load anaconda with $ module load anaconda
(base) $ ssh scompile
conda create -n <newEnvName> python==3.8 r-base=4
(base) $ conda activate <newEnvName>
```

Easy peasy!

### Bioinformatics packages on MacOS, Windows/Ubuntu

You'll need this link to find the installer:

[Miniconda](https://www.anaconda.com/docs/getting-started/miniconda/main)

Follow instillation instructions [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html), as well as verify your installer using sha256 or a related utility (this is a security issue). 

You will not need to add the special directories to `.condarc`.

---

</details>

<details>
  <summary>Summit - Demo</summary>

---

### SUMMIT - Quick demonstration

The software we obtained called **faFrag** lets us pull out a subset of a fasta file.

**!!! Exercise:** Let's try it!

Download *C. elegans* chromosome X.

```
$ rsync -aP \
rsync://hgdownload.cse.ucsc.edu/goldenPath/ce11/chromosomes/chrX.fa.gz .
```

The output from that command is:

```
receiving incremental file list
chrX.fa.gz
     5666803 100%    4.65MB/s    0:00:01 (xfer#1, to-check=0/1)

sent 51 bytes  received 5667599 bytes  1030481.82 bytes/sec
total size is 5666803  speedup is 1.00
```

We just downloaded the C. elegans chromosome X.

```
$ gunzip chrX.fa.gz 
$ wc chrX.fa 
  354380   354380 18073327 chrX.fa
```

The chromosome has 17,718,942 basepairs. Let's extract 40 of those with a simple command.

```
[shas0533 /projects/jesshill@colostate.edu/DSCI510]$
$ ./faFrag chrX.fa 10 50 small.fa
Wrote 40 bases to small.fa
```

Now see what it did:

```
$ cat small.fa
>chrX:10-50
gcctaagcctaagcctaagcctaagcctaagcctaagcct
```

It's OK to do small jobs like this on scompile.

### SUMMIT - Getting data on and off

Command-line tools that you can use to transfer files onto and off of SUMMIT include `rsync`. See an example of usage below. You can also use secure copy (scp) and secure ftp (sftp).

In your local terminal, you can download files **from SUMMIT** to your local computer like so, substituting <your-eID> with your own eID …

```
rsync -auvz -e 'ssh -p 22' <your-eID>\@colostate.edu@login.rc.colorado.edu:/scratch/summit/erinnish@colostate.edu/<file.txt> .
```

and you can move files **to SUMMIT** like so, substituting <your-eID> with your own eID …

```
rsync -auvz -e 'ssh -p 22' ./file.txt <your-eID>\@colostate.edu@login.rc.colorado.edu:/scratch/summit/erinnish@colostate.edu/ .
```

Additionally, you can also transfer data onto and off of SUMMIT using other methods like a web-based application called [Globus](https://www.globus.org/data-transfer), or [filezilla](https://filezilla-project.org/)! 

---

</details>
