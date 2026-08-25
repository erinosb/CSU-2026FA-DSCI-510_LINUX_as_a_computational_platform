# Options

Up to this point, we have used commands with and without arguments. In addition to this, we can execute commands with **options**. Options are bells and whistles we can append to our commands to customize the way the shell interprets the commands.

Here are a few options for the command ls courtesy of [The Linux Command Line](https://linuxcommand.org/tlcl.php):

<p align="center">
<img width="60%" alt="options" src="/05_images/options.png">
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

## Exercise: Exploring Options

:hammer_and_wrench: **Group Exercise**: Let's obtain a dataset to allow us to explore `ls` and its options:

 - Right click [03_data](/03_data/chrom_project.tgz) and open in a new tab. This will navigate to the dataset.
 - Click on **Raw** in the top right corner.
 - You will be prompted to select a directory where you want the dataset to download.

>[!TIP]
> This may be a good time to make a directory specifically for this class.

  - Use the Finder/Explorer, navigate to the location where you downloaded the file.
  - One of three things will happen:
    1. The **tarball** will expand on its own into a directory
    2. If you click on the **tarball**, it will expand into a directory
    3. You will need to expand the **tarball** using a command.

>[!TIP]
> If double-clicking on the “tarball” doesn't open it, try copying-and-pasting the file someplace you can access through your terminal. Then, navigate to the file through the terminal, then execute this command line to decompress it.

```
$ tar -zxvf chrom_project.tgz
```

  - If you need to, move the resulting expanded directory and its contents to a location you can easily manipulate in the terminal.

Open your terminal and navigate (use `cd, pwd, ls`) to the directory chromsizes.

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


