# Navigating the file system

### Who, What, When, Where commands

In your previous exercise you did the following:

```
$ whoami
$ hostname
$ pwd
$ ls
$ date
$ cal
```

Hopefully, when you typed in these commands, the shell responded more intelligibly than when you typed gibberish. This is because commands are programs that the shell has installed. When you type the command, you are instructing the shell to run a program it recognizes.

```
$ whoami  # WHO am I?
$ hostname  # WHAT computer is this?
$ pwd  # (Path to Working Directory) WHERE on the computer am I?
$ ls  # (List Segments) WHAT are the contents of this directory?
$ date  # WHEN? What is the date and time?
$ cal # WHEN? cute little calendar of this month
```

**!!! Quick tip**: Everything written after a “#” sign is a **comment** or annotation. The shell will not read things written after “#”.

**!!! Quick tip**: A **directory** is just the Linux-y term for “folder”. Just as there are slight terminology differences between MAC and Windows, so too are there differences in Linux.

### Independent Exercise - Dissecting the path

Let's take a closer look at what spits out when you type the command `$pwd`

When I type this out on my MAC computer, I get something that looks like this:

```
$ pwd 
/Users/jessicahill
```

If you are on a LINUX machine or a Windows, you will probably see something more like this …

```
$ pwd 
/home/jessicahill

#or 

C:\Users\jesshill
```

This notation is called a **path** and it describes the location, or the address, of my working directory within the file structure of a computer system.

When I look in this directory, I see …

```
$ ls
Colostate		Library			Pictures
Desktop			Movies			Public
Documents		Music
Downloads		OneDrive - Colostate
```

These are the items I have inside the working directory. This directory corresponds to the same directory I can locate in my "Finder" or "File Explorer".

The home folder on UBUNTU for Windows is in a really weird, hidden place.

### Independent exercises for Mac users

**!!! Exercise**: Open your "Finder" and navigate to the same directory you're in on the terminal. Double check that the contents are the same. Check that the path is similar.

**!!! Mac tip**: If you don't see your path in the Finder window, pull down the **View** menu and select **Show Path Bar**.

The directory you find yourself in when you first open up your terminal is called you **home** directory. This is a special place where the shell starts up by default.

### Independent exercises for Windows users

**!!! Exercise**: Try to find where your home directory is located on your computer. This is pretty challenging, but here we go …

- In your home directory, create a file called `250826_test.txt` like so …

```
$ touch 250826_test.txt
```

- Switch over to your **File Explorer** and **search** for the file `250826_test.txt` on “this PC”.
- Once your File Explorer has located your test file, navigate to that place.
  - Open a NEW File Explorer.
  - Go to “View”
  - Click on “File Name Extensions” to ensure that file name extensions are shown.
  - Click on “Hidden Items” to ensure that hidden items are shown.
  - Then click on “This PC” or “C:” and follow the train of folders down and down until you locate the directory where your test file was stored. This is your home directory.
- Create a shortcut to this home directory on your desktop so you always know where to find it.

### As a group: Moving around - Up to the root

We will learn how to move into different directories and at the same time learn more about paths. To move to a new directory we use the command `cd` for Change Directory.

**!!! Exercise**: Try the `cd` command like so:

```
$ cd
$ pwd
$ ls
```

What happened? Well, if you started in your home directory, nothing. This is because typing cd without anything after it defaults to changing you into your home directory. To give more instruction as to *where* we want to change into, we need to add an argument. **Arguments** are additional user-specific information we supply to a command.

```
$ cd <directoryname>
```

A cool quirk of Linux is that a period, “.”, is shorthand for the **current working directory**. And two periods, “..”, is shorthand for the directory a level up from my current directory. The directory one-level-up is called the **parent directory**.

### Independent Exercise: Moving around 

**!!! Exercise**: Write down the path of your curent working directory somewhere so you can remember it. Execute the following to step-wise navigate up through each directory. Continue this until you get to the top.

```
$ pwd
$ ls
$ cd . #this wont change your location
$ pwd 
$ ls
$ cd .. #this will change your location to the parent directory
$ pwd
$ ls
$ cd ../.. #this will change your location to the grandparent directory
$ pwd
$ ls
```

You should get to a place where you eventually see this:

```
$ pwd
/
```

This location is known as the **root**. This is the uppermost directory of your computer's file structure (that you are allowed to be in).

Now that we are in the uppermost directory, let's navigate back down to where we were before. To do this, we'll browse the contents of our root directory using ls and then select a specific sub-directory to change into using:

If the path to your home directory looked like this: `/subdirectoryname1/subdirectoryname2/subdirectoryname3`, you would do the following …

```
$ pwd
$ ls
$ cd subdirectoryname1
$ pwd 
$ ls
$ cd subdirectoryname2
$ pwd
$ ls
$ cd subdirectoryname3
```

Eventually, take this back down to your home directory.

### Independent Exercise: Navigating Up and Down

Now, try that same exercise one more time on your own.

Navigate from your home directory to the root directory using `$ cd ..`

Once at the root, navigate back through each sub-directory until you arrive back at home.

Do you have any questions?

**!!! Self-Assessment**: Reflect on the following - are you using ls and pwd between each cd step? Try to do this. It'll help you orient your current location.

### Summing it up in pictures

<p align="center">
<img width="410" alt="navigation" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/navigation.png">
</p>

---

**!!! Quick tip**: 

- **tab to autocomplete:** When you're typing out the name of a directory or sub-directory, instead of typing out the whole thing, start typing it a few characters and then autocomplete by typing TAB. If the characters you've typed so far limit you down to one option, the name will autocomplete. If it narrows it down into a few options, press TAB again and those options will be listed.

**!!! Common pitfall**: 

- **not enough ls and pwd:** Many new users have trouble navigating directories when they first start out. It is something that you'll get used to over time. One thing that can help make the process easier is to continually execute pwd and ls commands. Just imagine that anytime you want to look at something in your Finder/Explorer, you are in effect issuing an ls command. So you should be typing ls as often as you look at your files!

- **spaces in names:** Linux does NOT like spaces in directory or filenames, becuase they are commonly used as delimiters to seperate arguments in a command. If one of your directories contains a space, you'll need to treat the space as part of a single argument. This is done by/called **escaping a character**. This can be acheived in one of two ways: 
  - Type a backslash+space as `\ ` instead of just a single space.
  - Use single (' ') or double quotes (" ") to enclose the argument containing spaces.

Example: I have a directory called `OneDrive - Colostate` and I want to `cd` into it, so I need to type:

```
$ cd OneDrive\ -\ Colostate
```

OR

```
$ cd 'OneDrive - Colostate'
$ cd "OneDrive - Colostate"
```


Continue on to [Paths](1-4_Paths.md)

Here is the link to get to [Assignment 1](../../Home_Work/Assignment_1.md)
