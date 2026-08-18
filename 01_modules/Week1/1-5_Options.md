# Options

Up to this point, we have used commands with and without arguments. In addition to this, we can execute commands with **options**. Options are bells and whistles we can append to our commands to customize the way the shell interprets the commands.

Here are a few options for the command ls courtesy of [The Linux Command Line](https://linuxcommand.org/tlcl.php):

<p align="center">
<img width="410" alt="options" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/options.png">
</p>

Options are added after the command itself but before any arguments.

`command [options] [arguments]`

`command [options] <arguments>`

[] – optional. The command will work with or without these.

<> – required. The command requires these arguments.

Short options take one dash `-`. Long options take two dashes `--`.

Further, short options can often be lumped together.

For example, the following commands *should* do the same thing … but! on Mac, the double dashes don't work. This is due to some differences between Linux on these operating systems.

```
$ ls -a
$ ls --all
```

These commands should do the same thing on most distributions …

```
$ ls -a -h -l
$ ls -ahl
```

**!!! Mac Users:** 
- Are you seeing a `.DS_store` file?
- What is this, I didnt create it?
- It is a hidden metadata file that stores custom attributes and settings for its containing folder, such as the position of icons, the size and position of the folder window, and the chosen view mode (icon, list, etc.). The macOS Finder creates and maintains these files, and while they are normally hidden, they can become visible on Windows or Linux systems, making them a potential privacy risk if shared.
- You can leave them or delete them, ignore them, doesnt matter. 

### Exercise: Exploring Options

**!!! Exercise**: Let's obtain a dataset to allow us to explore `ls` and its options:

Download the following file by clicking on it. When prompted, save it to your a directory you can navigate to by both your Finder/Explorer AND by the terminal: [chromsizes2.tgz](https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Data/chromsizes2.tgz)

Note: this may be a good time to make a directory specifically for this class.

Use the Finder/Explorer, navigate to the location where you downloaded the file.

Double click on the `chromsizes2.tgz` file to decompress it.

**!!! Quick tip**: If double-clicking on the “tarball” doesn't open it, try copying-and-pasting the file someplace you can access through your terminal. Then, navigate to the file through the terminal, then execute this command line to decompress it.

```
$ tar -zxvf chromsizes2.tgz
```

If you need to, move the resulting expanded directory and its contents to a location you can easily manipulate in the terminal.

Open your terminal and navigate (use `cd, pwd, ls`) to the directory chromsizes.

Not working? Dr. Nishimura made a video of this in case it is confusing. [Video link to tutorial of tarball download](https://zoom.us/rec/component-page?eagerLoadZvaPages=sidemenu.billing.plan_management&accessLevel=meeting&action=viewdetailpage&sharelevel=meeting&useWhichPasswd=meeting&requestFrom=pwdCheck&clusterId=aw1&componentName=need-password&meetingId=baghS9zqnq9wa-F1KmP-HQdRBUimkEIk8kUzxBj449faPZDHgFKF91eBQsvQgbyo.O63ixl1U5Lv2ax7D&originRequestUrl=https%3A%2F%2Fzoom.us%2Frec%2Fshare%2F9_N4ArPU2l9LYc_jsRrACo0eI6X8eaa80SQcqPtexEcWyMaB7TbVkWJ7gYbepY9I%3FstartTime%3D1598531909000). Passcode: f$fQf2Lc

**Advanced User BONUS Content:** [Tarballs and GZipping](../../Resources/Tarballs.md).

**!!! Exercise**: Once you are within the directory chromsizes, try executing `ls` commands to view its contents using the following iterations:

```
$ ls -a
$ ls -l
$ ls -h
$ ls -a -l -h
$ ls -alh
```

**!!! Partner Exercise**: Find a partner. What combination of `ls` options would you execute to list the contents in the following order and file size format?

- **Hint:** Folders . and .. are not shown
- **Hint:** Consult the image of ls options at the top of this page.
- **Hint:** There might be some differences between what I have listed in this section: -rw-r–r–@ and what you have. Those are permission codes and you don't need to worry about them now. We'll talk about them later.

```
total 232
-rw-r--r--@ 1 erinnishimura  staff    18B Aug 24 05:20 wuhCor1_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff   229B Aug 24 05:21 sacCer3_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff   1.3K Aug 24 05:18 mm39_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff   375B Aug 24 05:16 hs1_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff    44K Aug 24 05:19 dm6_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff    47K Aug 24 05:19 danRer11_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff    99B Aug 24 05:20 ce11_chrom_sizes.txt
-rw-r--r--@ 1 erinnishimura  staff   903B Aug 24 05:29 230824_README_download.txt
```

### Manuals

Your Linux/GNU installation has instructions on how to use many of the commands built in. These are called manuals and they are accessible using:

**Manual Usage** `man <command_name>`

```
$ man ls
```

Use the **SPACE** bar to navigate through the manual pages.

Use **Q** to quit out of the manual pages.

I hate to tell you this, but the man pages are often inaccurate. Little differences between the distros and installations will lead to minor different behaviors. When this happens, try googling your problem and your operating system.

Continue on to [Working with files 1](1-6_Working_with_files1.md)
