# The Terminal

Today, most of the applications or programs we run on our computers are Graphical User Interface (GUI, pronounced “gooey”) applications. These are typically a window that pops up with a work space, menus, and icons. We can visually see things, “move” them, and click on things. Even the “Finder” (MAC) or “Explorer” (Windows) are GUI applications.

This wasn't always the case. When computers were first developed, all user interactions occurred by typing on the keyboard into a text interface.

Linux maintains this older, text-based interface through the **terminal emulator**, or **terminal**. By typing into the terminal, we can interact with the **shell**. The shell is a program that will take our text input and pass it to the **kernel**. The kernel is the core operating system that will assess how best to carry out each job given the computer's hardware and the task at hand.

<p align="center">
<img width="410" alt="scheme" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/scheme.png">
</p>

**!!! Cool trivia**: The operating system we will interface with in this class is larger than just the core kernel. It involves many other tasks and programs. Most of these auxiliary programs and tasks originate from the GNU Project that predates the Linux kernel. For this reason, what we refer to as “Linux” should probably be referenced as “GNU/Linux”. However, that is quite a mouthful and doesn't quite zing like just plain “Linux”. For more information on this interesting fact, please see **“Why I don't call it “GNU/LINUX”** in the textbook.

### Launching the terminal

**!!! Exercise**: launch your terminal

For more details, see [Computer_Requirements](../../Computer_Requirements.md).

### Getting started on the terminal

When you first open your terminal, you should get some introductory information about the computer you are on, sometimes some information about when you last logged in, and the prompt. looks like this

```
$
```

If you see this, great! The prompt is telling us that the shell is ready for input. We can type things in and see how the shell responds.

**!!! Exercise**: Type in some gibberish into the prompt.

**!!! Exercise**: Type in these commands into the prompt and see what happens:

```
$ whoami
$ hostname
$ pwd
$ ls
$ date
$ cal
```

Continue on to [Navigating_the_file_system](1-3_Navigating_the_file_system.md)
